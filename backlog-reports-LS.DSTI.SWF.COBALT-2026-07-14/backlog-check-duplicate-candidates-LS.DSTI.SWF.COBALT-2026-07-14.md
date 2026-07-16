## Duplicate Candidates
**Project:** LS.DSTI.SWF.COBALT | **Run:** 2026-07-14 | **Scope:** all areas/iterations/teams
**Result:** 22 issues found across 242 items scanned

### What this check looks for
This check identifies pairs of active requirement-level work items whose titles
are sufficiently similar to be candidates for human review as potential
duplicates.

### How it was checked
- **Population:** Requirement-level types `Product Backlog Item` and `Bug` in
  Proposed or InProgress state categories, across all area and iteration paths.
- **Flagging rule:** Titles were compared directly across the 242-item
  population, ignoring casing and punctuation. A pair is included when its
  titles are identical.
- **Fields used:** `System.Id`, `System.WorkItemType`, `System.Title`,
  `System.AreaPath`, `System.IterationPath`, and `System.State`.
- **Severity key:** High = near-identical titles in the same area path; Medium
  = semantically similar titles; Low = same-topic titles in different area
  paths. Similarity and severity are non-deterministic judgments.

### Findings
Each row is a candidate pair for human review only; the Finding explains why
the two work items may be duplicates.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|
| 69937 / 95207 | Product Backlog Item / Product Backlog Item | [DiagnosticReport][Get_v1] - Implementação do método (ver desc) / [DiagnosticReport][Get_v1] - Implementação do método (ver desc) | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113544 / 113545 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113544 / 113546 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113544 / 113547 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113544 / 113548 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113544 / 113549 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113544 / 113550 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113545 / 113546 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113545 / 113547 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113545 / 113548 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113545 / 113549 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113545 / 113550 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113546 / 113547 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113546 / 113548 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113546 / 113549 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113546 / 113550 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113547 / 113548 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113547 / 113549 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113547 / 113550 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113548 / 113549 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113548 / 113550 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |
| 113549 / 113550 | Product Backlog Item / Product Backlog Item | Retornar BaseURI / Retornar BaseURI | LS.DSTI.SWF.COBALT | LS.DSTI.SWF.COBALT\Archive | Identical titles in the same area; may be duplicates. | High |

**Summary:** This non-deterministic check produced 22 candidates for human
review only from 242 active requirement-level items; the WIQL result was below
its 10,000-item cap and all items were read in two batches, while the Readers
team's backlog could not be listed because its configured backlog iteration
path is invalid.
