# Backlog Quality Prompts — Azure DevOps MCP (consolidated)

A set of single-purpose prompts for auditing backlog quality in Azure DevOps
using the Azure DevOps MCP server. Work-item scope only — no repos, pipelines,
or code. Each prompt has exactly one objective and is a candidate for promotion
to a skill or command.

This file is the consolidated suite — earlier drafts have been merged into it.
Prompts appear here in their final form: the v2 revisions for checks 3, 8, 10,
and 12, and the new checks 13–16. Prompts 1, 2, 4, 5, 6, 7, 9, and 11 are
unchanged in wording and inherit the v2 conventions by reference (preflight,
category→name translation, pagination, dedup, text normalization, output
contract).

---

## Contents

All 16 prompts, grouped by category. `#` is the stable check ID (not
presentation order). For file slugs, severity anchors, and v2 status, see the
canonical [Prompt Index](#prompt-index) at the end of this file.

**Category 1 — Completeness**

- [Prompt 1: Description Completeness Check](#prompt-1-description-completeness-check)
- [Prompt 2: Acceptance Criteria Presence Check](#prompt-2-acceptance-criteria-presence-check)
- [Prompt 3 (revised): Missing Estimates](#prompt-3-revised-missing-estimates)
- [Prompt 15: Estimate Rollup Mismatch](#prompt-15-estimate-rollup-mismatch)

**Category 2 — Structure**

- [Prompt 4: Orphan Detector](#prompt-4-orphan-detector)
- [Prompt 5: Empty Parent Detector](#prompt-5-empty-parent-detector)
- [Prompt 6: Misplaced State Detector](#prompt-6-misplaced-state-detector)
- [Prompt 11: Lost Iteration Detector](#prompt-11-lost-iteration-detector)
- [Prompt 13: Missing / Default Area Path](#prompt-13-missing--default-area-path)
- [Prompt 14: Work Item Type at Wrong Backlog Level](#prompt-14-work-item-type-at-wrong-backlog-level)

**Category 3 — Hygiene**

- [Prompt 7: Stale Item Report](#prompt-7-stale-item-report)
- [Prompt 8 (revised): Duplicate Candidates](#prompt-8-revised-duplicate-candidates)
- [Prompt 12 (revised): Invalid Assignments](#prompt-12-revised-invalid-assignments)
- [Prompt 16: Blocked Items Without Recent Movement](#prompt-16-blocked-items-without-recent-movement)

**Category 4 — Readiness**

- [Prompt 9: Definition of Ready Audit](#prompt-9-definition-of-ready-audit)
- [Prompt 10 (revised): Oversized Items](#prompt-10-revised-oversized-items)

---

## Shared Conventions

All prompts below inherit these rules and `SHARED_CONVENTIONS.md` v2. When
promoting a prompt to a skill, copy this section in (or reference it).

### Input contract

- **Required:** `project` — the Azure DevOps project name.
- No other parameters in v1. Scope is always: all area paths, all iteration
  paths, all teams in the project.
- Thresholds shown as `{name:=default}` are inline defaults, overridable later
  if promoted to parameterized skills.

### Guardrails

- Use only Azure DevOps MCP tools.
- **Read-only. Never create, update, delete, or link work items.**
- If a required tool or permission is unavailable, report that and stop — do
  not approximate results from partial data without saying so.

### Process-agnostic field resolution (run before any check)

1. Discover work item types present in the project; identify types by
   **backlog level** (Epic / Feature / Requirement), never by hard-coded names
   like "User Story" or "PBI".
2. Resolve states by **state category** (Proposed, InProgress, Resolved,
   Completed, Removed), never by state name.
3. Resolve the estimate field by existence, in order:
   `Microsoft.VSTS.Scheduling.Effort` → `Microsoft.VSTS.Scheduling.StoryPoints`
   → `Microsoft.VSTS.Scheduling.Size`.
4. "Active work" throughout this document = state category Proposed or
   InProgress, unless a prompt says otherwise.

### Output contract

Every prompt writes its report to a **Markdown file** — chat output is only a
one-line confirmation with the file path and the finding count.

- **Path:** `{output_dir:=./backlog-reports/}` — create the directory if it
  does not exist.
- **Filename:** `backlog-check-<check-slug>-<project>-<YYYY-MM-DD>.md`
  (e.g., `backlog-check-lost-iterations-Contoso-2026-07-08.md`). Slugs are
  fixed per prompt and listed in the index. Re-running a check on the same day
  overwrites its own file — reports are idempotent per day.
- If the runtime has no filesystem access, say so explicitly and fall back to
  printing the report inline. Never silently drop the file.

The file content is this block, so files can be concatenated into a single
backlog health report. Three explanatory sections precede the findings table so
the report is self-explaining — a reader who has never seen the prompt can tell
what was checked, by what rules, and how to read the list.

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
  never add recommendations.
- `Finding` is a short factual phrase ("No acceptance criteria",
  "Iteration ended 47 days ago").
- `Severity` has a fixed meaning defined per prompt — not a judgment call — and
  that meaning is spelled out in the **Severity key** of each report.
- Zero findings still produces the full block (all three explanatory sections
  plus the empty table) with "0 issues found".
- No prose recommendations. Exceptions: Prompt 9 replaces the findings table
  with a pass/fail compliance matrix but keeps the header, explanatory sections,
  and summary frame; and Prompt 8 is the deliberate non-deterministic exception
  (similarity judgments, labelled candidates for human review) — see
  SHARED_CONVENTIONS.md v2.

---

# Category 1 — Completeness

## Prompt 1: Description Completeness Check

```
# Backlog Check: Description Completeness

You are auditing backlog quality in Azure DevOps project "{project}".
Use only Azure DevOps MCP tools. Do not modify any work items.

Objective (single): identify requirement-level work items in
pre-committed states whose Description field is empty or trivially
short.

Steps:
1. Discover the project's work item types and identify all types at
   the Requirements backlog level (do not assume names like "User
   Story" or "PBI").
2. Discover state categories; select items whose state category is
   "Proposed" or "InProgress".
3. Query all matching items across all area and iteration paths.
   Retrieve: ID, type, title, state, area path, iteration path,
   Description.
4. Flag an item when Description is empty, OR contains fewer than
   {min_chars:=140} characters after stripping HTML tags.
5. Severity: High = empty; Medium = under threshold; Low = not used
   in this check.

Do NOT evaluate the quality, clarity, or correctness of descriptions
that meet the threshold. Presence and length only.

Write the report to a Markdown file per the shared output contract,
using the standard backlog-check report format.
```

## Prompt 2: Acceptance Criteria Presence Check

```
# Backlog Check: Acceptance Criteria Presence

You are auditing backlog quality in Azure DevOps project "{project}".
Use only Azure DevOps MCP tools. Do not modify any work items.

Objective (single): identify requirement-level work items in
pre-committed states with no acceptance criteria.

Steps:
1. Identify all Requirements-level work item types.
2. Determine, per type, whether an acceptance criteria field exists
   (typically Microsoft.VSTS.Common.AcceptanceCriteria). If a type has
   no such field, exclude that type and note it in the summary.
3. Select items whose state category is "Proposed" or "InProgress".
4. Flag an item when the acceptance criteria field is empty, OR
   contains fewer than {min_chars:=50} characters after stripping
   HTML tags.
5. Severity: High = empty; Medium = under threshold.

Do NOT evaluate whether existing acceptance criteria are testable,
well-written, or correct. Presence and length only. Do NOT check the
Description field — that is a separate check.

Write the report to a Markdown file per the shared output contract,
using the standard backlog-check report format.
```

## Prompt 3 (revised): Missing Estimates

```
# Backlog Check: Missing Estimates

You are auditing backlog quality in Azure DevOps project "{project}".
Follow SHARED_CONVENTIONS.md v2. Use only Azure DevOps MCP tools. Do not
modify any work items. Run the preflight before anything else.

Objective (single): identify requirement-level work items approaching
commitment that have no estimate.

Steps:
1. Use the estimate field resolved in preflight. If none exists, emit the
   report block with 0 findings and note "no estimate field in project".
2. Determine "near-term scope": for each team, the current iteration plus the
   next {n_sprints:=2} future iterations. Per the v2 iteration caveat, derive
   future iterations from the PROJECT iteration tree (work_list_iterations, with
   dates) ordered relative to the run timestamp — this is a date-based
   approximation of per-team scope. State the approximation in the summary.
3. Select items in near-term scope whose state category is Proposed or
   InProgress (expand categories to state names per v2).
4. Deduplicate by work item ID across teams before flagging.
5. Flag an item when the estimate field is empty or zero.
6. Severity: High = item is in a current iteration; Medium = future near-term.

Do NOT judge whether existing estimates are reasonable in size (that is
Prompt 10). Do NOT flag items outside near-term scope.

Write the report per the v2 output contract, standard table format.
```

## Prompt 15: Estimate Rollup Mismatch

```
# Backlog Check: Estimate Rollup Mismatch

You are auditing backlog quality in Azure DevOps project "{project}".
Follow SHARED_CONVENTIONS.md v2. Use only Azure DevOps MCP tools. Do not
modify any work items. Run the preflight before anything else.

Objective (single): identify Feature-level parents whose own estimate differs
materially from the sum of their children's estimates.

Steps:
1. Use the estimate field resolved in preflight. If none exists, emit 0 findings
   with a note.
2. Select Feature-level items whose state category is Proposed or InProgress and
   whose estimate field is populated and > 0.
3. For each, sum the estimate of children whose state category is Proposed or
   InProgress (ignore children with empty/zero estimates, but count how many
   were ignored).
4. Flag a parent when abs(parent_estimate - children_sum) exceeds
   {tolerance:=20}% of the parent estimate AND at least one child is estimated.
5. In the Finding column report parent estimate, children sum, and count of
   unestimated children.
6. Severity: Medium (informational — rollup conventions vary by team).

Do NOT flag parents with no estimated children (indistinguishable from
missing-estimate cases). Do NOT judge which value is "correct".

Write the report per the v2 output contract, standard table format.
```

---

# Category 2 — Structure

## Prompt 4: Orphan Detector

```
# Backlog Check: Orphaned Items

You are auditing backlog quality in Azure DevOps project "{project}".
Use only Azure DevOps MCP tools. Do not modify any work items.

Objective (single): identify backlog items missing a parent link at
the level above them in the backlog hierarchy.

Steps:
1. Discover the project's backlog hierarchy (e.g., Epic → Feature →
   Requirement) using backlog levels, not type names.
2. Select items whose state category is "Proposed" or "InProgress":
   a. Requirements-level items with no parent link to a
      Feature-level item.
   b. Feature-level items with no parent link to an Epic-level item.
3. Flag each such item. In the Finding column state which parent
   level is missing.
4. Severity: Medium = Requirements-level orphan; Low = Feature-level
   orphan.

Do NOT flag Epic-level items (top of hierarchy). Do NOT flag parents
with no children — that is a separate check. Do NOT create any links.

Write the report to a Markdown file per the shared output contract,
using the standard backlog-check report format, grouped by
work item type.
```

## Prompt 5: Empty Parent Detector

```
# Backlog Check: Empty Parents

You are auditing backlog quality in Azure DevOps project "{project}".
Use only Azure DevOps MCP tools. Do not modify any work items.

Objective (single): identify Feature-level and Epic-level items in
active states that have zero child items in active states.

Steps:
1. Discover the backlog hierarchy by backlog levels.
2. Select Feature-level and Epic-level items whose state category is
   "Proposed" or "InProgress".
3. For each, count child links to items whose state category is
   "Proposed" or "InProgress".
4. Flag items with zero such children. In the Finding column,
   distinguish "no children at all" from "children exist but all are
   completed/removed".
5. Severity: High = InProgress parent with no active children;
   Medium = Proposed parent with no active children.

Do NOT flag parents whose children are merely unestimated or
incomplete in content. Child count and child state category only.

Write the report to a Markdown file per the shared output contract,
using the standard backlog-check report format, grouped by
work item type.
```

## Prompt 6: Misplaced State Detector

```
# Backlog Check: Parent/Child State Inconsistencies

You are auditing backlog quality in Azure DevOps project "{project}".
Use only Azure DevOps MCP tools. Do not modify any work items.

Objective (single): identify parent-child pairs whose state
categories are logically inconsistent.

Steps:
1. Discover the backlog hierarchy and state categories.
2. Traverse all parent-child links between backlog levels.
3. Flag these patterns (report the PARENT as the finding row, listing
   offending child IDs in the Finding column):
   a. Parent state category Completed, but one or more children in
      Proposed or InProgress. Severity: High.
   b. Parent state category Proposed, but one or more children in
      InProgress or beyond. Severity: Medium.
   c. Parent state category Removed, but one or more children in any
      non-Removed active state. Severity: High.
4. One row per parent, even if multiple children offend.

Do NOT flag missing links (orphan check) or empty parents (empty
parent check). Only state-category logic between existing links.

Write the report to a Markdown file per the shared output contract,
using the standard backlog-check report format.
```

## Prompt 11: Lost Iteration Detector

```
# Backlog Check: Lost Iterations

You are auditing backlog quality in Azure DevOps project "{project}".
Use only Azure DevOps MCP tools. Do not modify any work items.

Objective (single): identify iterations whose end date is in the past
but which still contain work items in non-closed states.

Steps:
1. Enumerate all iteration nodes in the project that have an end date
   earlier than today.
2. For each past iteration, query work items assigned to it whose
   state category is "Proposed", "InProgress", or "Resolved".
3. Flag every such item. In the Finding column include how many days
   ago the iteration ended.
4. Severity: High = state category InProgress; Medium = Proposed;
   Low = Resolved (done-ish but never closed — common rot).
5. Group output by iteration, ordered by how long ago the iteration
   ended (oldest first). Include a per-iteration count line above
   each group.

Do NOT flag past iterations that are cleanly empty or fully closed.
Do NOT evaluate whether the items should be closed or moved — report
only.

Write the report to a Markdown file per the shared output contract,
using the standard backlog-check report format, grouped by
iteration.
```

## Prompt 13: Missing / Default Area Path

```
# Backlog Check: Missing Area Path

You are auditing backlog quality in Azure DevOps project "{project}".
Follow SHARED_CONVENTIONS.md v2. Use only Azure DevOps MCP tools. Do not
modify any work items. Run the preflight before anything else.

Objective (single): identify active backlog items still sitting on the project
root area path (never triaged to a team/component area).

Steps:
1. Determine the project root area path (the node equal to the project name,
   with no child segment).
2. Select items at any backlog level whose state category is Proposed or
   InProgress. Dedup by ID.
3. Flag items whose AreaPath equals the project root (no sub-area assigned).
4. Severity: Medium = InProgress on root area; Low = Proposed on root area.

Do NOT evaluate whether the assigned area is the "correct" one — root vs
non-root only.

Write the report per the v2 output contract, standard table format.
```

## Prompt 14: Work Item Type at Wrong Backlog Level

```
# Backlog Check: Type/Level Mismatch

You are auditing backlog quality in Azure DevOps project "{project}".
Follow SHARED_CONVENTIONS.md v2. Use only Azure DevOps MCP tools. Do not
modify any work items. Run the preflight before anything else.

Objective (single): identify parent-child links where the child's backlog level
is not exactly one level below the parent's (level skips or inversions).

Steps:
1. Use the backlog hierarchy resolved in preflight (Epic > Feature >
   Requirement) and the type->level map.
2. Traverse all parent-child links between items whose state category is
   Proposed or InProgress.
3. Flag a link when the child level is not exactly one step below the parent
   level — e.g., a Requirement parented directly to an Epic (skipped Feature),
   or a Feature parented under a Requirement (inverted).
4. Report the CHILD as the finding row; name the parent ID/level and child level
   in the Finding column.
5. Severity: High = inverted hierarchy (child level above parent); Medium =
   skipped level.

Do NOT flag missing parents (that is Prompt 4). Only mismatched EXISTING links.

Write the report per the v2 output contract, standard table format.
```

---

# Category 3 — Hygiene

## Prompt 7: Stale Item Report

```
# Backlog Check: Stale Items

You are auditing backlog quality in Azure DevOps project "{project}".
Use only Azure DevOps MCP tools. Do not modify any work items.

Objective (single): identify backlog items untouched beyond an aging
threshold while still in pre-committed states.

Steps:
1. Select items at any backlog level whose state category is
   "Proposed".
2. Flag items whose ChangedDate is older than {stale_days:=90} days.
3. In the Finding column report days since last change.
4. Severity: High = older than {stale_days} * 2; Medium = older than
   {stale_days}.
5. Sort output oldest first.

Do NOT flag items in InProgress or later categories regardless of
age. Do NOT interpret why items are stale.

Write the report to a Markdown file per the shared output contract,
using the standard backlog-check report format.
```

## Prompt 8 (revised): Duplicate Candidates

```
# Backlog Check: Duplicate Candidates

You are auditing backlog quality in Azure DevOps project "{project}".
Follow SHARED_CONVENTIONS.md v2. Use only Azure DevOps MCP tools. Do not
modify any work items. Run the preflight before anything else.

NOTE: Per v2, this is the deliberate exception to the determinism rule. Its
findings and severities are similarity JUDGMENTS, not factual measurements.

Objective (single): surface pairs of active requirement-level items whose
titles are similar enough to warrant human review as potential duplicates.

Steps:
1. Select all Requirements-level items whose state category is Proposed or
   InProgress. Retrieve ID, title, area path, iteration path. Dedup by ID.
2. To stay tractable at scale, DO NOT do an O(n^2) all-pairs comparison. For
   each item, use search_workitem (searchText from the title, optionally scoped
   with areaPath) to retrieve a small set of candidate neighbors, then compare
   only within those candidate sets. If the total item count is small enough to
   compare directly, you may, but state which strategy you used in the summary.
3. Compare titles by semantic similarity — not exact matching. Ignore casing,
   punctuation, and common prefix tags like "[Backend]".
4. Report candidate PAIRS. The Finding column must contain a one-line rationale
   for why they may be duplicates.
5. Severity: High = near-identical titles in the same area path; Medium =
   semantically similar titles; Low = same-topic titles in different area paths.
6. These are candidates for HUMAN review. Never state that two items ARE
   duplicates — only that they may be.

Do NOT close, merge, tag, or link any items. Do NOT compare descriptions in
v1 — titles only.

Write the report per the v2 output contract, one row per pair (both IDs in the
ID column, e.g., "1234 / 5678"). The summary MUST state that this check is
non-deterministic and its output is candidates for human review only.
```

## Prompt 12 (revised): Invalid Assignments

```
# Backlog Check: Invalid Assignments (best-effort)

You are auditing backlog quality in Azure DevOps project "{project}".
Follow SHARED_CONVENTIONS.md v2. Use only Azure DevOps MCP tools. Do not
modify any work items. Run the preflight before anything else.

NOTE: Per v2 "Known capability limits", this is a BEST-EFFORT check. No MCP tool
returns a team's full member roster, and org-level identity status likely cannot
be verified. This check cannot reliably distinguish a departed user from a valid
member who simply has no capacity record. Treat every finding accordingly.

Objective (single): surface work items in active states whose assignee cannot be
confirmed as a current member of any team in the project.

Steps:
1. Build the best-available valid-identity set: enumerate teams with
   core_list_project_teams; for each team's current iteration, read
   work_get_team_capacity and collect member identities (match by unique
   name/descriptor, not display name). Record explicitly that this roster is
   capacity-derived and therefore incomplete.
2. Select work items at any backlog level whose state category is Proposed or
   InProgress and whose AssignedTo is not empty. Dedup by ID.
3. Flag items whose AssignedTo identity is NOT in the valid-identity set.
4. Severity: report ALL findings as Medium (org-level disabled/removed status
   cannot be verified through available tools). If a future tool enables
   org-level verification, upgrade confirmed-disabled identities to High.
5. In the Finding column include the assignee display name and the note
   "not found in capacity-derived team rosters — verify manually".
6. Group output by assignee.

Do NOT flag unassigned items. Do NOT reassign or clear any AssignedTo values.

Write the report per the v2 output contract, grouped by assignee. The summary
MUST state the roster limitation and that findings require manual verification.
```

## Prompt 16: Blocked Items Without Recent Movement

```
# Backlog Check: Stalled Blocked Items

You are auditing backlog quality in Azure DevOps project "{project}".
Follow SHARED_CONVENTIONS.md v2. Use only Azure DevOps MCP tools. Do not
modify any work items. Run the preflight before anything else.

Objective (single): identify items marked blocked that have not changed in some
time (a block that is being ignored).

Steps:
1. Determine how "blocked" is expressed in this project, by existence in order:
   the Microsoft.VSTS.CMMI.Blocked field = "Yes", OR a tag named "Blocked"
   (case-insensitive). If neither signal exists, emit 0 findings with a note.
2. Select items at any backlog level whose state category is Proposed or
   InProgress and that carry the blocked signal. Dedup by ID.
3. Flag items whose ChangedDate is older than {blocked_days:=14} days.
4. In the Finding column report days since last change and the blocked signal
   used.
5. Severity: High = blocked and InProgress; Medium = blocked and Proposed.
6. Sort oldest first.

Do NOT flag blocked items changed within the threshold. Do NOT interpret the
reason for the block.

Write the report per the v2 output contract, standard table format.
```

---

# Category 4 — Readiness

## Prompt 9: Definition of Ready Audit

```
# Backlog Check: Definition of Ready Audit

You are auditing backlog quality in Azure DevOps project "{project}".
Use only Azure DevOps MCP tools. Do not modify any work items.

Objective (single): score the top of the backlog against a fixed
Definition of Ready checklist, as a pass/fail compliance matrix.

Steps:
1. Identify Requirements-level types, the estimate field, and the
   acceptance criteria field (per shared conventions).
2. Select the top {top_n:=20} items per team backlog whose state
   category is "Proposed", ordered by backlog priority
   (StackRank/BacklogPriority).
3. Evaluate each item against these criteria, each strictly pass/fail:
   - DESC: Description present and ≥ {min_chars:=140} chars
   - AC: Acceptance criteria present and ≥ 50 chars
   - EST: Estimate field populated and > 0
   - PARENT: Parent link to the level above exists
   - SIZE: Estimate ≤ {max_points:=8}
4. Output a compliance matrix instead of the standard table:

   | ID | Title | DESC | AC | EST | PARENT | SIZE | Ready? |

   where each cell is ✅ or ❌, and Ready? is ✅ only if all pass.
5. Summary line: "X of Y top-of-backlog items meet the Definition of
   Ready (Z%)."

Do NOT add prose recommendations per item. Do NOT re-explain failures
already visible in the matrix. The matrix IS the output.

Write the report to a Markdown file per the shared output contract,
using the standard report header and summary frame around the matrix.
```

## Prompt 10 (revised): Oversized Items

```
# Backlog Check: Oversized Items

You are auditing backlog quality in Azure DevOps project "{project}".
Follow SHARED_CONVENTIONS.md v2. Use only Azure DevOps MCP tools. Do not
modify any work items. Run the preflight before anything else.

Objective (single): identify near-term backlog items whose estimate exceeds a
splittable-size threshold.

Steps:
1. Use the estimate field resolved in preflight. Determine near-term scope
   exactly as in Prompt 3 (date-based approximation; state it in the summary).
2. Select Requirements-level items in near-term scope whose state category is
   Proposed or InProgress. Dedup by ID.
3. Flag items whose estimate is greater than {max_points:=8}.
4. In the Finding column report the estimate value.
5. Severity: High = in a current iteration; Medium = future near-term.

Do NOT flag unestimated items (that is Prompt 3). Do NOT suggest how to split.

Write the report per the v2 output contract, sorted by estimate descending.
```

---

# Appendix — Composition (future)

Candidate orchestrator prompt, not yet drafted: **Backlog Health Report
(orchestrator)** — runs checks 1–16 and concatenates their output files into a
single report with a roll-up scorecard. The per-check MD files in `{output_dir}`
make this a pure merge step. Deferred until the individual prompts have been
exercised against a real project. Since 13–16 are now real checks, the
orchestrator would become #17 when drafted.

---

# Prompt Index

Canonical index of all checks. `#` is a stable ID (not presentation order).
All inherit `SHARED_CONVENTIONS.md` v2.

## By ID

| #  | Check                         | Category     | File slug                  | Severity anchor                     | v2 status |
|----|-------------------------------|--------------|----------------------------|-------------------------------------|-----------|
| 1  | Description completeness      | Completeness | `description-completeness` | Empty = High                        | unchanged |
| 2  | Acceptance criteria presence  | Completeness | `acceptance-criteria`      | Empty = High                        | unchanged |
| 3  | Missing estimates             | Completeness | `missing-estimates`        | Current iteration = High            | revised   |
| 4  | Orphan detector               | Structure    | `orphans`                  | Requirement orphan = Medium         | unchanged |
| 5  | Empty parent detector         | Structure    | `empty-parents`            | InProgress empty parent = High      | unchanged |
| 6  | Misplaced state detector      | Structure    | `misplaced-states`         | Done parent, active child = High    | unchanged |
| 7  | Stale item report             | Hygiene      | `stale-items`              | 2× threshold = High                 | unchanged |
| 8  | Duplicate candidate finder    | Hygiene      | `duplicate-candidates`     | Same-area near-match = High         | revised   |
| 9  | Definition of Ready audit     | Readiness    | `dor-audit`                | Matrix, no severity                 | unchanged |
| 10 | Oversized items               | Readiness    | `oversized-items`          | Current iteration = High            | revised   |
| 11 | Lost iteration detector       | Structure    | `lost-iterations`          | InProgress in past sprint = High    | unchanged |
| 12 | Invalid assignment detector   | Hygiene      | `invalid-assignments`      | All = Medium (best-effort)          | revised   |
| 13 | Missing / default area path   | Structure    | `missing-area-path`        | InProgress on root = Medium         | new       |
| 14 | Type / level mismatch         | Structure    | `type-level-mismatch`      | Inverted hierarchy = High           | new       |
| 15 | Estimate rollup mismatch      | Completeness | `rollup-mismatch`          | All = Medium                        | new       |
| 16 | Stalled blocked items         | Hygiene      | `blocked-stalled`          | Blocked + InProgress = High         | new       |

## By category

- **Completeness:** 1, 2, 3, 15
- **Structure:** 4, 5, 6, 11, 13, 14
- **Hygiene:** 7, 8, 12, 16
- **Readiness:** 9, 10

## v2 status roll-up

- **Unchanged (inherit v2 by reference):** 1, 2, 4, 5, 6, 7, 9, 11
- **Revised:** 3, 8, 10, 12
- **New:** 13, 14, 15, 16

## Notes

- Report filenames follow `backlog-check-<file slug>-<project>-<YYYY-MM-DD>.md`.
- Prompt 8 is the deliberate non-deterministic exception (similarity judgments).
- Prompt 9 uses a pass/fail matrix instead of the standard table.
- Prompt 12 is best-effort: no MCP tool returns full team rosters (see v2
  "Known capability limits").
- Prompt 9's DESC/AC length checks use the single v2 text-normalization
  procedure, which guarantees agreement with Prompts 1/2.
