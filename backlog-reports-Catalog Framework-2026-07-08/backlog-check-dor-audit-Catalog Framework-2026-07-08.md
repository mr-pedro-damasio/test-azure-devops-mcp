## Definition of Ready Audit
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 20 issues found across 20 items scanned

### What this check looks for
How the top of the backlog measures against a fixed Definition of Ready, scored
as a pass/fail compliance matrix rather than a findings list.

### How it was checked
- **Population:** the top 20 requirement-level items (Product Backlog Item, Bug)
  whose state category is Proposed, ordered by backlog priority.
- **Flagging rule — five pass/fail criteria per item:** DESC = Description
  present and ≥ 140 normalized chars; AC = acceptance criteria present and ≥ 50
  normalized chars; EST = estimate populated and > 0; PARENT = parent link to a
  Feature-level item; SIZE = estimate ≤ 8.
- **Fields used:** `System.Description`,
  `Microsoft.VSTS.Common.AcceptanceCriteria`,
  `Microsoft.VSTS.Scheduling.Effort`, parent link,
  `Microsoft.VSTS.Common.BacklogPriority`.
- **Severity key:** none — each cell is ✅ or ❌, and Ready? is ✅ only when all
  five criteria pass.

### Findings
Each row is one top-of-backlog item; the five criteria columns show ✅/❌ and the
Ready? column is ✅ only if every criterion passes.

| ID | Title | DESC | AC | EST | PARENT | SIZE | Ready? |
|----|-------|------|----|-----|--------|------|--------|
| 146506 | PBI-01.01 — Criar e configurar o Planner board | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146576 | PBI-08.01 — Testes de configuração M365 e Planner | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146573 | PBI-07.03 — Implementar notificações Teams finais | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146572 | PBI-07.02 — Implementar logging de eventos em todos os componentes | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146570 | PBI-07.01 — Definir modelo de dados do Audit Store | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146567 | PBI-06.04 — Implementar spike técnico de OutSystems Extensions | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146565 | PBI-06.03 — Implementar lógica de execução no Execution Adapter | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146563 | PBI-06.02 — Implementar OutSystems Extension para acesso Oracle | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146562 | PBI-06.01 — Definir e expor o contrato do Execution Adapter | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146558 | PBI-05.03 — Gerar e enviar feedback ao negócio em caso de rejeição | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146557 | PBI-05.02 — Atualizar estado do Planner após decisão | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146556 | PBI-05.01 — Implementar lógica de decisão automática no flow | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146552 | PBI-04.03 — Implementar tratamento de erros e timeout do Ontoserver | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146551 | PBI-04.02 — Implementar integração com Ontoserver | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146548 | PBI-04.01 — Definir bindings terminológicos | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146545 | PBI-03.05 — Definir e expor o contrato do Validation Service | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146544 | PBI-03.04 — Implementar normalização server-side (workbook → payload canónico) | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146543 | PBI-03.03 — Implementar validação estrutural e de campos obrigatórios | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146542 | PBI-03.02 — Implementar parser do workbook em OutSystems | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| 146541 | PBI-03.01 — Definir e versionar o template de input (contrato do workbook) | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |

**Summary:** 0 of 20 top-of-backlog items meet the Definition of Ready (0%).

_Note: All 20 items pass DESC (description >= 140 normalized chars), AC (acceptance
criteria >= 50 normalized chars), and PARENT (each links to a Feature-level parent).
Every item fails EST because Microsoft.VSTS.Scheduling.Effort is unpopulated, and
consequently fails SIZE (no Effort value can satisfy Effort <= 8). Effort was
explicitly requested in the batch read and returned empty for all 20 items. Scan
was complete; no truncation or capability gaps._
