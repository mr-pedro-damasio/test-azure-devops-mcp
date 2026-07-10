# Shared Conventions — Backlog Quality Prompts (v2)

Revised shared conventions for the Azure DevOps backlog-quality prompt suite.
All prompts inherit this section. When promoting a prompt to a skill, copy this
in (or reference it). Changes from v1 are marked **[NEW in v2]**.

Work-item scope only — no repos, pipelines, or code.

---

## Input contract

- **Required:** `project` — the Azure DevOps project name.
- No other parameters in v1/v2. Scope is always: all area paths, all iteration
  paths, all teams in the project.
- Thresholds shown as `{name:=default}` are inline defaults, overridable later
  if promoted to parameterized skills.
- **[NEW in v2] Date source.** All date logic (filenames, "N days ago", "past
  iteration", ChangedDate aging) uses a single run timestamp: the system date at
  invocation, resolved **once** at the start of the run and reused everywhere so
  a single run is internally consistent. If promoted to a skill, this may be
  overridden by an injected `as_of` parameter for reproducible re-runs.

---

## Guardrails

- Use only Azure DevOps MCP tools.
- **Read-only. Never create, update, delete, or link work items.** Do not call
  any mutating tool (`wit_create_work_item`, `wit_update_work_item`,
  `wit_update_work_items_batch`, `wit_work_items_link`, `wit_work_item_unlink`,
  `wit_add_child_work_items`, `wit_add_work_item_comment`, etc.) under any
  circumstance, even if a finding seems trivially fixable.
- If a required tool or permission is unavailable, report that and stop — do not
  approximate results from partial data without saying so.

---

## Preflight capability check (run ONCE before any check) **[NEW in v2]**

The suite's "process-agnostic" promise depends on metadata that must be
confirmed present before running. Run these in order; if any fails, report the
specific limitation and either stop or degrade the affected check explicitly
(never silently).

1. **Backlog levels.** Resolve the project's backlog hierarchy and the work item
   types mapped to each level (Epic / Feature / Requirement) via
   `wit_list_backlogs` (per team — see field resolution below). Never hard-code
   type names like "User Story" or "PBI".
2. **State categories.** For each work item type in scope, call
   `wit_get_work_item_type` and confirm the returned state definitions expose a
   **category** (a.k.a. metaState: Proposed / InProgress / Resolved / Completed /
   Removed). Build and cache a per-type map of `category → [state names]`.
   - If a type's states do **not** expose categories, the "select by category"
     mechanism cannot run for that type. Report this in the summary and exclude
     the type — do not guess categories from state names.
3. **Estimate field.** Resolve by existence, in order:
   `Microsoft.VSTS.Scheduling.Effort` → `Microsoft.VSTS.Scheduling.StoryPoints`
   → `Microsoft.VSTS.Scheduling.Size`. Record which field was chosen; report it
   in the summary. If none exists, estimate-based checks (3, 9, 10, 15) report
   zero findings with an explicit "no estimate field in this project" note.
4. **Acceptance criteria field.** Per requirement-level type, determine whether
   `Microsoft.VSTS.Common.AcceptanceCriteria` (or equivalent) exists. Types
   without it are excluded from the AC check and noted.

---

## Process-agnostic field resolution

1. Identify types by **backlog level**, never by hard-coded names.
2. Resolve states by **state category**, never by state name — using the
   `category → [state names]` map built in preflight.
3. Resolve the estimate field by existence (order above).
4. "Active work" throughout this document = state category **Proposed or
   InProgress**, unless a prompt says otherwise.

### Category → state-name translation is mandatory **[NEW in v2]**

WIQL (`wit_query_by_wiql`) can filter only by state **name**
(`[System.State] IN (...)`); it has **no** operator for state category. Every
query that selects "items whose state category is X" must be built by expanding
X into the concrete state names from the preflight map, then emitting an
`IN (...)` clause. Do not attempt to filter by category directly in WIQL.

### Teams, backlogs, and iterations are team-scoped **[NEW in v2]**

- `wit_list_backlogs` / `wit_list_backlog_work_items` require a **team**.
  Enumerate teams with `core_list_project_teams` (page via `top`/`skip`) and
  iterate.
- Two distinct iteration sources — do not conflate:
  - **Project iteration tree** (all iteration nodes + start/finish dates):
    `work_list_iterations` (use `depth` to reach leaves). Use this for Prompt 11
    (lost iterations) and as the source of iteration **dates**.
  - **Team current iteration:** `work_list_team_iterations` supports only
    `timeframe: 'current'`. It does **not** return future iterations.
- **Near-term scope caveat.** Because no tool returns a team's *future* subscribed
  iterations, "current + next {n} iterations per team" (Prompts 3, 10) is
  approximated from the project iteration tree by date order relative to the run
  timestamp. State this approximation in the summary of those checks; the "per
  team" precision is best-effort, not exact.

---

## Scale, pagination, and truncation **[NEW in v2]**

An audit that silently truncates and reports "0 issues" is worse than no audit.
Never let a hard cap masquerade as a clean result.

- **WIQL:** `wit_query_by_wiql` defaults to `top: 50`. Always set an explicit
  high `top`. WIQL returns IDs only; if the ID set approaches any service limit,
  page by narrowing the query (e.g., by area path or date window) and union the
  results.
- **Batch reads:** `wit_get_work_items_batch_by_ids` is capped at **200 IDs per
  call**. Chunk ID lists into ≤200 and merge. Request only the fields the check
  needs via the `fields` parameter.
- **Deduplicate by work item ID** across all team-scoped enumerations. Backlogs
  and iterations are commonly shared across teams, so the same item surfaces
  under multiple teams; collapse to one row per ID before counting or reporting.
- If any hard cap is hit and results may be incomplete, say so explicitly in the
  summary line. Do not present a partial scan as complete.

---

## Text normalization for length checks **[NEW in v2]**

Prompts 1, 2, and 9 count characters in HTML fields. Use this single procedure
everywhere so standalone checks and the DoR matrix (Prompt 9) always agree:

1. Remove all HTML tags.
2. Decode HTML entities (`&nbsp;` → space, `&amp;` → `&`, etc.).
3. Collapse runs of whitespace (including non-breaking space) to a single space
   and trim leading/trailing whitespace.
4. Count the remaining characters. An empty result (no text content) counts as
   length 0 regardless of markup, images, or empty tables.

---

## Output contract

Every prompt writes its report to a **Markdown file** — chat output is only a
one-line confirmation with the file path and the finding count.

- **Path:** `{output_dir:=./backlog-reports-<project>-<YYYY-MM-DD>/}` — one
  directory per project per run date, using the run timestamp date. Create the
  directory if it does not exist.
- **Filename:** `backlog-check-<check-slug>-<project>-<YYYY-MM-DD>.md`, using the
  run timestamp date. Slugs are fixed per prompt (see index). Re-running a check
  on the same day overwrites its own file — reports are idempotent per day.
- If the runtime has no filesystem access, say so explicitly and fall back to
  printing the report inline. Never silently drop the file.

The file content is this block, so files can be concatenated into a single
backlog health report. Three explanatory sections precede the findings table so
the report is self-explaining — a reader who has never seen the prompt can tell
what was checked, by what rules, and how to read the list. **[NEW in v2]**

```markdown
## <Check name>
**Project:** <name> | **Run:** <date> | **Scope:** all areas/iterations/teams
**Result:** <N> issues found across <M> items scanned

### What this check looks for
<1–2 plain sentences: the work items examined and the single condition being
detected — the prompt's objective, restated for someone who has not read it.>

### How it was checked
- **Population:** <backlog levels / work item types and state categories
  included (named process-agnostically), plus any iteration or area narrowing.>
- **Flagging rule:** <the exact condition that flags an item, with every
  threshold and its resolved value — e.g. "Description < 140 chars after HTML
  strip + entity decode + whitespace collapse".>
- **Fields used:** <the resolved reference names actually read — e.g. estimate
  field `Microsoft.VSTS.Scheduling.Effort`, acceptance-criteria field,
  ChangedDate — or "System fields only".>
- **Severity key:** <what each severity value used in this report means for THIS
  check — the fixed per-prompt definition, not a judgment call.>

### Findings
<One sentence on how to read the table: what a single row represents and how to
interpret the Finding and Severity columns for this check.>

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|

**Summary:** <one sentence, factual, no recommendations>
```

- The three explanatory sections (**What this check looks for**, **How it was
  checked**, **Findings**) are derived from the prompt's own objective, rules,
  thresholds, and severity definitions. They restate the method applied; they
  never add recommendations or interpret findings. **[NEW in v2]**
- `Finding` is a short factual phrase ("No acceptance criteria", "Iteration
  ended 47 days ago").
- `Severity` has a fixed meaning defined per prompt — not a judgment call — and
  that meaning is spelled out in the **Severity key** of each report.
- Zero findings still produces the full block — all three explanatory sections
  plus the empty table — with "0 issues found".
- **Report scan completeness and any degradation in the summary** — items
  scanned, types/teams excluded during preflight, caps hit, and approximations
  used (e.g., near-term scope). **[NEW in v2]**
- No prose recommendations. The explanatory sections describe the rules that
  were applied, not actions the reader should take.

### Documented exceptions to the standard format

Both exceptions keep the header, the three explanatory sections, and the summary
frame — only the findings list itself changes.

- **Prompt 9 (Definition of Ready)** replaces the findings table with a
  pass/fail compliance matrix but keeps the same header and summary frame. Its
  **How it was checked** section lists the five DoR criteria (DESC / AC / EST /
  PARENT / SIZE) as the flagging rules, and its **Findings** section explains
  that each cell is ✅/❌ and that Ready? is ✅ only when all five pass.
- **[NEW in v2] Prompt 8 (Duplicate Candidates)** is the deliberate exception to
  the determinism rule. Its findings and severities are similarity **judgments**,
  not factual measurements. It must (a) label every output as a candidate for
  human review, (b) never assert two items ARE duplicates, and (c) note in the
  summary that this check is non-deterministic. Its **How it was checked**
  section must state the comparison strategy used (candidate-neighbour vs. full
  pairwise) and that the check is non-deterministic. To stay tractable at scale,
  use `search_workitem` to fetch candidate neighbors (optionally scoped by
  `areaPath`) rather than an O(n²) all-pairs comparison.

---

## Known capability limits (report, don't fake) **[NEW in v2]**

- **Team membership rosters (Prompt 12):** there is no MCP tool that returns a
  team's full member list. `work_get_team_capacity` requires an `iterationId`
  and returns only members with capacity records; `core_get_identity_ids` is a
  search-by-filter lookup, not an enumeration. Treat Prompt 12 as **best-effort**:
  it cannot reliably distinguish a departed user from a member who simply has no
  capacity record, and it likely cannot verify org-level disabled/removed status.
  Report all such findings as Medium and state the limitation prominently.
