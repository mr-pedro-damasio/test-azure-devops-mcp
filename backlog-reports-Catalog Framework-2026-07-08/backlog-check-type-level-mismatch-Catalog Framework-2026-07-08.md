## Type/Level Mismatch
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 0 issues found across 72 items scanned

### What this check looks for
Parent-child links where the child's backlog level is not exactly one step below
the parent's (level skips or inversions).

### How it was checked
- **Population:** parent-child links where both endpoints are in Proposed or
  InProgress.
- **Flagging rule:** child level is not exactly one below the parent level
  (Epic > Feature > Requirement) — e.g. a Requirement linked straight to an Epic
  (skipped Feature) or a Feature under a Requirement (inverted). Missing parents
  are out of scope.
- **Fields used:** parent/child hierarchy links, the type→level map.
- **Severity key:** High = inverted hierarchy (child level above parent);
  Medium = skipped level.

### Findings
Each row would be a child whose link skips or inverts a level, naming the parent
ID/level and child level; every existing link spans exactly one level, so the
table is empty.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|

**Summary:** All 72 existing parent-child links (both endpoints active) traversed with no truncation; every child sits exactly one backlog level below its parent (Requirement→Feature, Feature→Epic), so no skipped or inverted levels were found.
