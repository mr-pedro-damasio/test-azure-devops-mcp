## Stalled Blocked Items
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 0 issues found across 0 items scanned

### What this check looks for
Items marked blocked that have not changed in some time — a block that is being
ignored.

### How it was checked
- **Population:** items at any backlog level whose state category is Proposed or
  InProgress that carry the blocked signal.
- **Blocked signal:** this project has no `Microsoft.VSTS.CMMI.Blocked` field, so
  the only usable signal is a tag named "Blocked" (case-insensitive); no item
  carried such a tag.
- **Flagging rule:** `ChangedDate` older than 14 days before the run — before
  2026-06-24.
- **Fields used:** `System.Tags`, `System.ChangedDate`.
- **Severity key:** High = blocked and InProgress; Medium = blocked and Proposed.

### Findings
Each row would be a stalled blocked item with days-since-last-change and the
blocked signal used; no blocked signal exists in this project, so the table is
empty.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|

**Summary:** The Microsoft.VSTS.CMMI.Blocked field does not exist in this project, so the only usable blocked signal is a case-insensitive "Blocked" tag in System.Tags; a WIQL scan of all active-state items (Proposed/InProgress) found no work item carrying that tag, so no blocked signal was present and there is nothing to evaluate for staleness — scan complete.
