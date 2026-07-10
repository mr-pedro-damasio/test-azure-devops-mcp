## Acceptance Criteria Presence
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 16 issues found across 62 items scanned

### What this check looks for
Requirement-level work items (Product Backlog Item, Bug) in pre-committed states
that have no acceptance criteria — presence and length only, not testability or
correctness.

### How it was checked
- **Population:** Product Backlog Item and Bug (Requirement backlog level) whose
  state category is Proposed or InProgress; both types expose the acceptance
  criteria field, so none were excluded.
- **Flagging rule:** `AcceptanceCriteria` is empty, or under 50 characters after
  stripping HTML tags, decoding entities, and collapsing whitespace.
- **Fields used:** `Microsoft.VSTS.Common.AcceptanceCriteria`.
- **Severity key:** High = acceptance criteria empty; Medium = present but under
  the 50-character threshold.

### Findings
Each row is one flagged item; the Finding column states whether acceptance
criteria were empty or under-length, and Severity follows the key above.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|
| 145397 | Product Backlog Item | Definição de Scope In / Scope Out do Catálogo | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145398 | Product Backlog Item | Modelo de decisão e ownership | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145399 | Product Backlog Item | Matriz de stakeholders e responsabilidades | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145400 | Product Backlog Item | Identificação e registo inicial de riscos do Catálogo | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145401 | Product Backlog Item | Mapear value streams dependentes do Catálogo | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145402 | Product Backlog Item | Identificar de pain points atuais | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145403 | Product Backlog Item | Critérios de sucesso de negócio | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145404 | Product Backlog Item | Dependências entre processos de negócio | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145405 | Product Backlog Item | Identificar de entidades de negócio core | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145406 | Product Backlog Item | Levantamento de regras críticas de negócio | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145407 | Product Backlog Item | Exceções e variabilidade | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145408 | Product Backlog Item | Riscos associados a inconsistências de regras | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145828 | Product Backlog Item | indicadores de qualidade do CID | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145829 | Product Backlog Item | indicadores de qualidade dados no Insurance Plan | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145830 | Product Backlog Item | indicadores de qualidade dados do Healthcare Provider | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |
| 145836 | Product Backlog Item | Acessos da equipa | Catalog Framework | Catalog Framework | Acceptance Criteria empty | High |

**Summary:** Scanned 62 active requirement-level items (Product Backlog Item, Bug in Proposed/InProgress states); 16 had an empty or under-50-char Acceptance Criteria after HTML strip/normalize; no scan degradation.
