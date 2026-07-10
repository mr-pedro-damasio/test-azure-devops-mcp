## Lost Iterations
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 47 issues found across 47 items scanned

### What this check looks for
Iterations that have already ended but still hold work items in non-closed
states.

### How it was checked
- **Population:** iterations whose end date is before 2026-07-08 — Sprints 0.1,
  0.2, and 0.3. Sprints 4–6 have no end date and so are not "past" (excluded).
- **Flagging rule:** a work item in a past iteration whose state category is
  Proposed, InProgress, or Resolved (this process defines no Resolved category).
  Cleanly-empty or fully-closed past iterations are not flagged.
- **Fields used:** `System.IterationPath`, state category, iteration finish
  dates.
- **Severity key:** High = InProgress; Medium = Proposed; Low = Resolved (none
  possible here).

### Findings
Rows are grouped by iteration, oldest-ended first, with a count line above each
group; the Finding column reports how many days ago the iteration ended.

**Sprint 0.1 — ended 54 days ago (2026-05-15) — 47 items**

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|
| 145735 | Epic | Discovery | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 145736 | Product Backlog Item | Levantamento e Inventário de Value Sets e Code Systems | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 145737 | Product Backlog Item | Definição inicial de modelo FHIR (Profiles + Terminologies) | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 145839 | Product Backlog Item | Construção de fluxo de validação de ficheiro de carregamento | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 145840 | Product Backlog Item | Implementação de mecanismo de feedback | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146533 | Feature | EP-02 | Ingestão e Trigger | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146534 | Product Backlog Item | PBI-02.01 — Implementar trigger de nova tarefa no Planner | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146535 | Product Backlog Item | PBI-02.02 — Resolver referência do ficheiro | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146536 | Product Backlog Item | PBI-02.03 — Implementar retry controlado para referências tardias | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146537 | Product Backlog Item | PBI-02.04 — Copiar ficheiro para localização de processamento controlada | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146538 | Product Backlog Item | PBI-02.05 — Atualizar estado para `Validating` e chamar o Validation Service | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146540 | Feature | EP-03 | Validation Service — Estrutural e Normalização | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146541 | Product Backlog Item | PBI-03.01 — Definir e versionar o template de input (contrato do workbook) | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146542 | Product Backlog Item | PBI-03.02 — Implementar parser do workbook em OutSystems | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146543 | Product Backlog Item | PBI-03.03 — Implementar validação estrutural e de campos obrigatórios | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146544 | Product Backlog Item | PBI-03.04 — Implementar normalização server-side (workbook → payload canónico) | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146545 | Product Backlog Item | PBI-03.05 — Definir e expor o contrato do Validation Service | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146547 | Feature | EP-04 | Validation Service | Terminologia | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146548 | Product Backlog Item | PBI-04.01 — Definir bindings terminológicos | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146551 | Product Backlog Item | PBI-04.02 — Implementar integração com Ontoserver | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146552 | Product Backlog Item | PBI-04.03 — Implementar tratamento de erros e timeout do Ontoserver | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146555 | Feature | EP-05 | Decisão Automática e Feedback | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146556 | Product Backlog Item | PBI-05.01 — Implementar lógica de decisão automática no flow | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146557 | Product Backlog Item | PBI-05.02 — Atualizar estado do Planner após decisão | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146558 | Product Backlog Item | PBI-05.03 — Gerar e enviar feedback ao negócio em caso de rejeição | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146560 | Feature | EP-06 | Execution Adapter | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146562 | Product Backlog Item | PBI-06.01 — Definir e expor o contrato do Execution Adapter | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146563 | Product Backlog Item | PBI-06.02 — Implementar OutSystems Extension para acesso Oracle | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146565 | Product Backlog Item | PBI-06.03 — Implementar lógica de execução no Execution Adapter | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146567 | Product Backlog Item | PBI-06.04 — Implementar spike técnico de OutSystems Extensions | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146569 | Feature | EP-07 | Logging, Auditoria e Notificações | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146570 | Product Backlog Item | PBI-07.01 — Definir modelo de dados do Audit Store | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146572 | Product Backlog Item | PBI-07.02 — Implementar logging de eventos em todos os componentes | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146573 | Product Backlog Item | PBI-07.03 — Implementar notificações Teams finais | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146575 | Feature | EP-08 | Hardening, Testes e UAT | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146576 | Product Backlog Item | PBI-08.01 — Testes de configuração M365 e Planner | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146577 | Product Backlog Item | PBI-08.02 — Testes funcionais de validação estrutural e terminológica | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146578 | Product Backlog Item | PBI-08.03 — Testes de execução e idempotência | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146579 | Product Backlog Item | PBI-08.04 — Testes de paridade com template legado | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146580 | Product Backlog Item | PBI-08.05 — Produzir runbook operacional | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146581 | Product Backlog Item | PBI-08.06 — UAT com negócio e IT | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146582 | Epic | EPIC-01 | MVP - Board Planner  for Pricing Management | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146911 | Product Backlog Item | PBI-03.06 — Extrair e implementar validações de negócio | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146912 | Product Backlog Item | PBI-05.04 — Definir e implementar matriz de transição de estados | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146914 | Product Backlog Item | PBI-06.05 — Implementar estratégia de chunking transacional | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146915 | Product Backlog Item | PBI-06.06 — Implementar política de reprocessamento com commits parciais | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |
| 146916 | Product Backlog Item | PBI-07.04 — Expor métricas operacionais no fluxo | Catalog Framework | Catalog Framework\Sprint 0.1 | Active (Proposed=New) in past iteration; ended 54 days ago | Medium |

**Summary:** Complete scan of the three past iterations returned 47 active (all Proposed=New) items, all in Sprint 0.1 (ended 54 days ago); Sprint 0.2 (ended 40 days ago) and Sprint 0.3 (ended 26 days ago) held no non-closed active items and were not flagged, and Sprint 4/5/6 have no end date so are not past and were excluded.
