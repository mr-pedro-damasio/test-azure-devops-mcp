## Parent/Child State Inconsistencies
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 0 issues found across 72 items scanned

### What this check looks for
Parent-child pairs whose state categories are logically inconsistent.

### How it was checked
- **Population:** all existing parent-child links between backlog levels.
- **Flagging rule (one row per parent):** (a) parent Completed but a child is
  Proposed or InProgress; (b) parent Proposed but a child is InProgress or
  beyond; (c) parent Removed but a child is in any non-Removed active state.
  Missing links and empty parents are out of scope.
- **Fields used:** state category of both link endpoints; hierarchy links.
- **Severity key:** High = case (a) or (c); Medium = case (b).

### Findings
Each row is a parent, with offending child IDs in the Finding column. No
inconsistencies were found because the entire backlog is in a single Proposed
state.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|

**Summary:** All 72 existing parent-child links traversed with no truncation; every work item is in the Proposed state (New), so no Completed/Proposed/Removed parent-versus-child state inconsistencies exist.
