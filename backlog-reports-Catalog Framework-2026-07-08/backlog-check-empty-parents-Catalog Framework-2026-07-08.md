## Empty Parents
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 6 issues found across 20 items scanned

### What this check looks for
Feature-level and Epic-level items in active states that have no active children.

### How it was checked
- **Population:** Feature-level and Epic-level items whose state category is
  Proposed or InProgress.
- **Flagging rule:** zero child links to items whose state category is Proposed
  or InProgress. Content completeness and child estimates are not considered —
  child count and child state only.
- **Fields used:** parent/child hierarchy links and child state category.
- **Severity key:** High = InProgress parent with no active children; Medium =
  Proposed parent with no active children.

### Findings
Rows are grouped by work item type; the Finding column distinguishes "no children
at all" from "children exist but all completed/removed", and Severity follows the
key above.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|
| 144177 | Feature | Discovery \| Data Volume, Growth & Criticality Analysis | Catalog Framework | Catalog Framework | No children at all | Medium |
| 144178 | Feature | Discovery \| Application Responsibilities & Boundaries | Catalog Framework | Catalog Framework | No children at all | Medium |
| 144179 | Feature | Discovery \| API & Consumption Patterns Exploration | Catalog Framework | Catalog Framework | No children at all | Medium |
| 144180 | Feature | Discovery \| Platform & Infrastructure Constraints | Catalog Framework | Catalog Framework | No children at all | Medium |
| 144181 | Feature | Discovery \| Security, Compliance & Access Model Exploration | Catalog Framework | Catalog Framework | No children at all | Medium |
| 144182 | Feature | Discovery \| Discovery Synthesis & Go / No-Go | Catalog Framework | Catalog Framework | No children at all | Medium |

**Summary:** Full scan of all 20 active (Proposed/InProgress) Epic- and Feature-level items completed with no truncation; 6 Proposed Features have no children at all, and all remaining Epics and Features have at least one active child.
