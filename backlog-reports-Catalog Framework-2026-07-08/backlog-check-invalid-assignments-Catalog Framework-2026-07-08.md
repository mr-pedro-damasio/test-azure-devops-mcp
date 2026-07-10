## Invalid Assignments (best-effort)
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 2 issues found across 2 items scanned

### What this check looks for
Work items in active states whose assignee cannot be confirmed as a current
member of any team in the project. This is a best-effort check: no MCP tool
returns a team's full roster, so findings require manual verification.

### How it was checked
- **Population:** items at any backlog level whose state category is Proposed or
  InProgress with a non-empty assignee, deduplicated by ID.
- **Valid-identity set:** intended to be built from team capacity for the current
  iteration; the team's current iteration returned no capacity records, so the
  roster could not be built and every active-assigned item is reported as
  unverifiable.
- **Fields used:** `System.AssignedTo`; team capacity (`work_get_team_capacity`).
- **Severity key:** all findings Medium (org-level disabled/removed status cannot
  be verified through available tools).

### Findings
Rows are grouped by assignee; the Finding column names the assignee and flags
that they were not found in the capacity-derived roster and must be verified
manually.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|
| 145400 | Product Backlog Item | Identificação e registo inicial de riscos do Catálogo | Catalog Framework | Catalog Framework | Assigned to Magda Ressurreição Silva (magda.ressurreicao.silva@luzsaude.pt) — not found in capacity-derived team rosters (roster could not be built); verify manually | Medium |
| 145736 | Product Backlog Item | Levantamento e Inventário de Value Sets e Code Systems | Catalog Framework | Sprint 0.1 | Assigned to Ana Margarida Roque Gonçalves (a.roquegoncalves@dedalus.eu) — not found in capacity-derived team rosters (roster could not be built); verify manually | Medium |

**Summary:** Best-effort check with a hard roster limitation: no MCP tool returns a full team roster, and the only candidate current iteration (Sprint 0.3, 2026-06-01/2026-06-12) returned "No team capacity assigned to the team", so the capacity-derived valid-identity set could NOT be built at all. With no valid set to match against, both active-assigned items (2 distinct assignees, one item each) are reported as unverifiable at Medium; all findings require manual verification and none should be treated as confirmed invalid. Unassigned items were not flagged; scan complete apart from the stated roster limitation.
