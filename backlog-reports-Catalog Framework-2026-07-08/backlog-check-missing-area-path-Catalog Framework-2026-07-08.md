## Missing Area Path
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 82 issues found across 82 items scanned

### What this check looks for
Active backlog items still sitting on the project root area path (never triaged
to a team or component area).

### How it was checked
- **Population:** items at any backlog level (Epic, Feature, Product Backlog
  Item, Bug) whose state category is Proposed or InProgress, deduplicated by ID.
- **Flagging rule:** `AreaPath` equals the project root "Catalog Framework"
  exactly, with no sub-area segment. Whether a non-root area is the "correct" one
  is not assessed — root vs non-root only.
- **Fields used:** `System.AreaPath`.
- **Severity key:** Medium = InProgress on root area; Low = Proposed on root
  area.

### Findings
Each row is one item still on the root area path; Severity follows the key above.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|
| 144171 | Feature | Discovery | Discovery Governance & Scope Alignment | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 144174 | Feature | Discovery | Business Vision & Value Streams | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 144175 | Feature | Discovery | Business Domain & Rules Exploration | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 144176 | Feature | Discovery | Data Landscape & Source Assessment | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 144177 | Feature | Discovery | Data Volume, Growth & Criticality Analysis | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 144178 | Feature | Discovery | Application Responsibilities & Boundaries | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 144179 | Feature | Discovery | API & Consumption Patterns Exploration | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 144180 | Feature | Discovery | Platform & Infrastructure Constraints | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 144181 | Feature | Discovery | Security, Compliance & Access Model Exploration | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 144182 | Feature | Discovery | Discovery Synthesis & Go / No-Go | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145397 | Product Backlog Item | Definição de Scope In / Scope Out do Catálogo | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145398 | Product Backlog Item | Modelo de decisão e ownership | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145399 | Product Backlog Item | Matriz de stakeholders e responsabilidades | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145400 | Product Backlog Item | Identificação e registo inicial de riscos do Catálogo | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145401 | Product Backlog Item | Mapear value streams dependentes do Catálogo | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145402 | Product Backlog Item | Identificar de pain points atuais | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145403 | Product Backlog Item | Critérios de sucesso de negócio | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145404 | Product Backlog Item | Dependências entre processos de negócio | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145405 | Product Backlog Item | Identificar de entidades de negócio core | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145406 | Product Backlog Item | Levantamento de regras críticas de negócio | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145407 | Product Backlog Item | Exceções e variabilidade | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145408 | Product Backlog Item | Riscos associados a inconsistências de regras | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145735 | Epic | Discovery | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145736 | Product Backlog Item | Levantamento e Inventário de Value Sets e Code Systems | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145737 | Product Backlog Item | Definição inicial de modelo FHIR (Profiles + Terminologies) | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145828 | Product Backlog Item | indicadores de qualidade do CID | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145829 | Product Backlog Item | indicadores de qualidade dados no Insurance Plan | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145830 | Product Backlog Item | indicadores de qualidade dados do Healthcare Provider | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145836 | Product Backlog Item | Acessos da equipa | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145837 | Product Backlog Item | Preparação de dados de origem (extração xHIS / views) | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145838 | Product Backlog Item | Instanciação inicial no OntoServer | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145839 | Product Backlog Item | Construção de fluxo de validação de ficheiro de carregamento | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145840 | Product Backlog Item | Implementação de mecanismo de feedback | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145841 | Product Backlog Item | Setup técnico do ambiente POC | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 145842 | Product Backlog Item | Definição de critérios de qualidade de dados | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146506 | Product Backlog Item | PBI-01.01 — Criar e configurar o Planner board | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146528 | Feature | EP-01 | Setup M365 e Planner | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146529 | Product Backlog Item | PBI-01.02 — Configurar o Teams e canais de notificação | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146530 | Product Backlog Item | PBI-01.03 — Definir e configurar contas técnicas e permissões | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146531 | Product Backlog Item | PBI-01.04 — Validar conectividade do conector Planner em Power Automate | Catalog Framework | Catalog Framework | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146533 | Feature | EP-02 | Ingestão e Trigger | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146534 | Product Backlog Item | PBI-02.01 — Implementar trigger de nova tarefa no Planner | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146535 | Product Backlog Item | PBI-02.02 — Resolver referência do ficheiro | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146536 | Product Backlog Item | PBI-02.03 — Implementar retry controlado para referências tardias | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146537 | Product Backlog Item | PBI-02.04 — Copiar ficheiro para localização de processamento controlada | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146538 | Product Backlog Item | PBI-02.05 — Atualizar estado para `Validating` e chamar o Validation Service | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146540 | Feature | EP-03 | Validation Service — Estrutural e Normalização | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146541 | Product Backlog Item | PBI-03.01 — Definir e versionar o template de input (contrato do workbook) | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146542 | Product Backlog Item | PBI-03.02 — Implementar parser do workbook em OutSystems | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146543 | Product Backlog Item | PBI-03.03 — Implementar validação estrutural e de campos obrigatórios | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146544 | Product Backlog Item | PBI-03.04 — Implementar normalização server-side (workbook → payload canónico) | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146545 | Product Backlog Item | PBI-03.05 — Definir e expor o contrato do Validation Service | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146547 | Feature | EP-04 | Validation Service | Terminologia | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146548 | Product Backlog Item | PBI-04.01 — Definir bindings terminológicos | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146551 | Product Backlog Item | PBI-04.02 — Implementar integração com Ontoserver | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146552 | Product Backlog Item | PBI-04.03 — Implementar tratamento de erros e timeout do Ontoserver | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146555 | Feature | EP-05 | Decisão Automática e Feedback | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146556 | Product Backlog Item | PBI-05.01 — Implementar lógica de decisão automática no flow | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146557 | Product Backlog Item | PBI-05.02 — Atualizar estado do Planner após decisão | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146558 | Product Backlog Item | PBI-05.03 — Gerar e enviar feedback ao negócio em caso de rejeição | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146560 | Feature | EP-06 | Execution Adapter | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146562 | Product Backlog Item | PBI-06.01 — Definir e expor o contrato do Execution Adapter | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146563 | Product Backlog Item | PBI-06.02 — Implementar OutSystems Extension para acesso Oracle | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146565 | Product Backlog Item | PBI-06.03 — Implementar lógica de execução no Execution Adapter | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146567 | Product Backlog Item | PBI-06.04 — Implementar spike técnico de OutSystems Extensions | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146569 | Feature | EP-07 | Logging, Auditoria e Notificações | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146570 | Product Backlog Item | PBI-07.01 — Definir modelo de dados do Audit Store | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146572 | Product Backlog Item | PBI-07.02 — Implementar logging de eventos em todos os componentes | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146573 | Product Backlog Item | PBI-07.03 — Implementar notificações Teams finais | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146575 | Feature | EP-08 | Hardening, Testes e UAT | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146576 | Product Backlog Item | PBI-08.01 — Testes de configuração M365 e Planner | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146577 | Product Backlog Item | PBI-08.02 — Testes funcionais de validação estrutural e terminológica | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146578 | Product Backlog Item | PBI-08.03 — Testes de execução e idempotência | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146579 | Product Backlog Item | PBI-08.04 — Testes de paridade com template legado | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146580 | Product Backlog Item | PBI-08.05 — Produzir runbook operacional | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146581 | Product Backlog Item | PBI-08.06 — UAT com negócio e IT | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146582 | Epic | EPIC-01 | MVP - Board Planner  for Pricing Management | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146911 | Product Backlog Item | PBI-03.06 — Extrair e implementar validações de negócio | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146912 | Product Backlog Item | PBI-05.04 — Definir e implementar matriz de transição de estados | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146914 | Product Backlog Item | PBI-06.05 — Implementar estratégia de chunking transacional | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146915 | Product Backlog Item | PBI-06.06 — Implementar política de reprocessamento com commits parciais | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |
| 146916 | Product Backlog Item | PBI-07.04 — Expor métricas operacionais no fluxo | Catalog Framework | Catalog Framework\Sprint 0.1 | Area Path is project root (no sub-area); state Proposed=New | Low |

**Summary:** Complete scan across all Epic/Feature/PBI/Bug levels returned 82 active items (all state Proposed=New) sitting on the exact project-root Area Path "Catalog Framework" with no sub-area; no InProgress-on-root items were found, so all findings are severity Low.
