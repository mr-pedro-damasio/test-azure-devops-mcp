## Estimate Rollup Mismatch
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 0 issues found across 18 items scanned

### What this check looks for
Feature-level parents whose own estimate differs materially from the sum of
their children's estimates.

### How it was checked
- **Population:** Feature-level items whose state category is Proposed or
  InProgress and whose estimate is populated and greater than zero.
- **Flagging rule:** the absolute difference between the parent estimate and the
  summed estimates of its active (Proposed/InProgress) children exceeds 20% of
  the parent estimate, and at least one child is estimated; children with empty
  or zero estimates are ignored but counted.
- **Fields used:** `Microsoft.VSTS.Scheduling.Effort`, parent/child hierarchy
  links (`System.Parent`).
- **Severity key:** Medium for all findings (rollup conventions vary by team).

### Findings
Each row would name a parent whose estimate and children's sum diverge; of the
18 active Features scanned none had a populated non-zero estimate, so none
qualified and the table is empty.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|

**Summary:** Complete scan of all 18 Feature-level items in state category Proposed/InProgress (states New/In Progress); none has a populated Effort greater than 0, so no parent qualified for rollup comparison and no mismatch could be flagged.
