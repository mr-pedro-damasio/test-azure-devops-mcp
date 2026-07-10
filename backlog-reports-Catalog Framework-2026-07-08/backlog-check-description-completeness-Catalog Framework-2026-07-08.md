## Description Completeness
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 20 issues found across 62 items scanned

### What this check looks for
Requirement-level work items (Product Backlog Item, Bug) in pre-committed states
whose Description field is missing or too short to brief anyone — presence and
length only, never writing quality.

### How it was checked
- **Population:** Product Backlog Item and Bug (Requirement backlog level) whose
  state category is Proposed or InProgress.
- **Flagging rule:** Description is empty, or under 140 characters after
  stripping HTML tags, decoding entities, and collapsing whitespace.
- **Fields used:** `System.Description` (plus type, title, state, area path,
  iteration path for context).
- **Severity key:** High = Description empty; Medium = present but under the
  140-character threshold.

### Findings
Each row is one flagged item; the Finding column states whether the description
was empty or under-length, and Severity follows the key above.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|
| 145398 | Product Backlog Item | Modelo de decisão e ownership | Catalog Framework | Catalog Framework | Description 106 chars (<140) | Medium |
| 145400 | Product Backlog Item | Identificação e registo inicial de riscos do Catálogo | Catalog Framework | Catalog Framework | Description 125 chars (<140) | Medium |
| 145401 | Product Backlog Item | Mapear value streams dependentes do Catálogo | Catalog Framework | Catalog Framework | Description 133 chars (<140) | Medium |
| 145402 | Product Backlog Item | Identificar de pain points atuais | Catalog Framework | Catalog Framework | Description 129 chars (<140) | Medium |
| 145403 | Product Backlog Item | Critérios de sucesso de negócio | Catalog Framework | Catalog Framework | Description 139 chars (<140) | Medium |
| 145404 | Product Backlog Item | Dependências entre processos de negócio | Catalog Framework | Catalog Framework | Description 122 chars (<140) | Medium |
| 145405 | Product Backlog Item | Identificar de entidades de negócio core | Catalog Framework | Catalog Framework | Description 124 chars (<140) | Medium |
| 145406 | Product Backlog Item | Levantamento de regras críticas de negócio | Catalog Framework | Catalog Framework | Description 124 chars (<140) | Medium |
| 145407 | Product Backlog Item | Exceções e variabilidade | Catalog Framework | Catalog Framework | Description 108 chars (<140) | Medium |
| 145408 | Product Backlog Item | Riscos associados a inconsistências de regras | Catalog Framework | Catalog Framework | Description 95 chars (<140) | Medium |
| 145828 | Product Backlog Item | indicadores de qualidade do CID | Catalog Framework | Catalog Framework | Description empty | High |
| 145829 | Product Backlog Item | indicadores de qualidade dados no Insurance Plan | Catalog Framework | Catalog Framework | Description empty | High |
| 145830 | Product Backlog Item | indicadores de qualidade dados do Healthcare Provider | Catalog Framework | Catalog Framework | Description empty | High |
| 145836 | Product Backlog Item | Acessos da equipa | Catalog Framework | Catalog Framework | Description empty | High |
| 145837 | Product Backlog Item | Preparação de dados de origem (extração xHIS / views) | Catalog Framework | Catalog Framework | Description 135 chars (<140) | Medium |
| 145838 | Product Backlog Item | Instanciação inicial no OntoServer | Catalog Framework | Catalog Framework | Description 94 chars (<140) | Medium |
| 145839 | Product Backlog Item | Construção de fluxo de validação de ficheiro de carregamento | Catalog Framework | Catalog Framework\Sprint 0.1 | Description 133 chars (<140) | Medium |
| 145840 | Product Backlog Item | Implementação de mecanismo de feedback | Catalog Framework | Catalog Framework\Sprint 0.1 | Description 115 chars (<140) | Medium |
| 145841 | Product Backlog Item | Setup técnico do ambiente POC | Catalog Framework | Catalog Framework | Description 91 chars (<140) | Medium |
| 145842 | Product Backlog Item | Definição de critérios de qualidade de dados | Catalog Framework | Catalog Framework | Description 67 chars (<140) | Medium |

**Summary:** Scanned 62 active requirement-level items (Product Backlog Item, Bug in Proposed/InProgress states); 20 had an empty or under-140-char Description after HTML strip/normalize; no scan degradation.
