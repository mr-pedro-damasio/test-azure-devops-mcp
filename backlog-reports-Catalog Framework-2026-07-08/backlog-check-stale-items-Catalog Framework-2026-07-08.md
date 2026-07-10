## Stale Items
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 0 issues found across 82 items scanned

### What this check looks for
Backlog items left untouched past an aging threshold while still in a
pre-committed state.

### How it was checked
- **Population:** items at any backlog level whose state category is Proposed
  (states New or Approved).
- **Flagging rule:** `ChangedDate` older than 90 days before the run — i.e.
  before 2026-04-09.
- **Fields used:** `System.ChangedDate`.
- **Severity key:** High = older than 180 days (before 2026-01-09); Medium =
  older than 90 days. Rows sort oldest first.

### Findings
Each row would be one stale item with days-since-last-change in the Finding
column; the newest-touched items still change within ~64 days, so none crossed
the 90-day threshold and the table is empty.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|

**Summary:** Scanned all 82 Proposed-category items (states New/Approved) across every backlog level; the oldest System.ChangedDate returned is 2026-05-05 (~64 days), so no item crosses the 90-day staleness threshold (before 2026-04-09) — scan complete, no truncation or capability limitation.
