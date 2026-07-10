## Missing Estimates
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 0 issues found across 0 items scanned

### What this check looks for
Requirement-level work items approaching commitment (current plus next two
iterations) that carry no estimate.

### How it was checked
- **Population:** Product Backlog Item and Bug whose state category is Proposed
  or InProgress and that fall in near-term scope.
- **Near-term scope:** derived by date from the project iteration tree. As of
  2026-07-08 no iteration's date range covers today (Sprints 0.1–0.3 are past;
  Sprints 4–6 are undated), so the only non-past iterations (Sprints 4–6) were
  taken as best-effort near-term — and no active requirement items are assigned
  there, so the scope resolved to empty.
- **Flagging rule:** the estimate field is empty or zero.
- **Fields used:** `Microsoft.VSTS.Scheduling.Effort`, `System.IterationPath`.
- **Severity key:** High = item in a current iteration (cannot apply here — no
  date-current iteration exists); Medium = future near-term.

### Findings
Each row would be one near-term item with no estimate; none were in scope, so the
table is empty.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|

**Summary:** Complete scan; near-term scope was approximated as the only non-past iterations (Sprint 4/5/6, all undated) because as of 2026-07-08 no iteration's date range covers today, so the High="current iteration" severity cannot apply by date; zero requirement-level items are assigned to Sprint 4/5/6, so the scan population was empty and no missing-estimate findings exist.
