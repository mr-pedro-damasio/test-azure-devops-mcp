## Oversized Items
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 0 issues found across 0 items scanned

### What this check looks for
Near-term requirement-level work items whose estimate is larger than a
splittable-size threshold.

### How it was checked
- **Population:** Product Backlog Item and Bug in near-term scope whose state
  category is Proposed or InProgress.
- **Near-term scope:** same date-based approximation as Missing Estimates — no
  date-current iteration exists on 2026-07-08, best-effort near-term is the
  undated Sprints 4–6, and no active requirement items sit there, so scope is
  empty.
- **Flagging rule:** estimate greater than 8.
- **Fields used:** `Microsoft.VSTS.Scheduling.Effort`.
- **Severity key:** High = item in a current iteration (cannot apply here);
  Medium = future near-term. Rows sort by estimate descending.

### Findings
Each row would be one oversized near-term item with its estimate in the Finding
column; none were in scope, so the table is empty.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|

**Summary:** Complete scan; near-term scope was approximated as the only non-past iterations (Sprint 4/5/6, all undated) because as of 2026-07-08 no iteration's date range covers today, so the High="current iteration" severity cannot apply by date; zero requirement-level items are assigned to Sprint 4/5/6, so the scan population was empty and no oversized (Effort > 8) items exist.
