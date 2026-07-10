## Orphaned Items
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 8 issues found across 80 items scanned

### What this check looks for
Backlog items missing a parent link at the level directly above them in the
hierarchy.

### How it was checked
- **Population:** items whose state category is Proposed or InProgress —
  Requirement-level items (checked for a Feature parent) and Feature-level items
  (checked for an Epic parent).
- **Flagging rule:** no parent link to the level immediately above. Epic-level
  items (top of the hierarchy) are never flagged; childless parents are out of
  scope (that is the Empty Parents check).
- **Fields used:** parent/child hierarchy links (`System.Parent`),
  `System.WorkItemType`.
- **Severity key:** Medium = Requirement-level orphan; Low = Feature-level
  orphan.

### Findings
Rows are grouped by work item type; the Finding column names which parent level
is missing, and Severity follows the key above.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|
| 145736 | Product Backlog Item | Levantamento e Inventário de Value Sets e Code Systems | Catalog Framework | Catalog Framework\Sprint 0.1 | No parent link to a Feature-level item | Medium |
| 145737 | Product Backlog Item | Definição inicial de modelo FHIR (Profiles + Terminologies) | Catalog Framework | Catalog Framework\Sprint 0.1 | No parent link to a Feature-level item | Medium |
| 145837 | Product Backlog Item | Preparação de dados de origem (extração xHIS / views) | Catalog Framework | Catalog Framework | No parent link to a Feature-level item | Medium |
| 145838 | Product Backlog Item | Instanciação inicial no OntoServer | Catalog Framework | Catalog Framework | No parent link to a Feature-level item | Medium |
| 145839 | Product Backlog Item | Construção de fluxo de validação de ficheiro de carregamento | Catalog Framework | Catalog Framework\Sprint 0.1 | No parent link to a Feature-level item | Medium |
| 145840 | Product Backlog Item | Implementação de mecanismo de feedback | Catalog Framework | Catalog Framework\Sprint 0.1 | No parent link to a Feature-level item | Medium |
| 145841 | Product Backlog Item | Setup técnico do ambiente POC | Catalog Framework | Catalog Framework | No parent link to a Feature-level item | Medium |
| 145842 | Product Backlog Item | Definição de critérios de qualidade de dados | Catalog Framework | Catalog Framework | No parent link to a Feature-level item | Medium |

**Summary:** Full scan of all 80 active (Proposed/InProgress) Requirement- and Feature-level items completed with no truncation; 8 Requirement-level orphans found and zero Feature-level orphans.
