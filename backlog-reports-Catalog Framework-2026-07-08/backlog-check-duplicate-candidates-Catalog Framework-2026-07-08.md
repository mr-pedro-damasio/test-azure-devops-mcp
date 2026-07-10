## Duplicate Candidates
**Project:** Catalog Framework | **Run:** 2026-07-08 | **Scope:** all areas/iterations/teams
**Result:** 7 issues found across 63 items scanned

### What this check looks for
Pairs of active requirement-level items whose titles are similar enough to
warrant human review as possible duplicates. This check is non-deterministic —
its findings are similarity judgments, not measurements, and are candidates for
human review only; it never asserts two items ARE duplicates.

### How it was checked
- **Population:** Product Backlog Item and Bug whose state category is Proposed
  or InProgress, deduplicated by ID.
- **Comparison strategy:** the active set (63 items) was small enough to compare
  in full pairwise rather than sampling neighbours via `search_workitem`.
- **Flagging rule:** titles judged semantically similar, ignoring casing,
  punctuation, and common prefix tags like "[Backend]". Titles only — no
  descriptions.
- **Fields used:** `System.Title`, `System.AreaPath`, `System.IterationPath`.
- **Severity key:** High = near-identical titles in the same area path; Medium =
  semantically similar titles; Low = same-topic titles in different area paths.

### Findings
Each row is a candidate pair (both IDs in the ID column) with a one-line
rationale in the Finding column; treat every row as a prompt for human review,
not a confirmed duplicate.

| ID | Type | Title | Area Path | Iteration | Finding | Severity |
|----|------|-------|-----------|-----------|---------|----------|
| 145828 / 145829 | Product Backlog Item / Product Backlog Item | indicadores de qualidade do CID ; indicadores de qualidade dados no Insurance Plan | Catalog Framework | Catalog Framework | Same "indicadores de qualidade" template differing only by target entity (CID vs Insurance Plan) | Medium |
| 145828 / 145830 | Product Backlog Item / Product Backlog Item | indicadores de qualidade do CID ; indicadores de qualidade dados do Healthcare Provider | Catalog Framework | Catalog Framework | Same "indicadores de qualidade" template differing only by target entity (CID vs Healthcare Provider) | Medium |
| 145829 / 145830 | Product Backlog Item / Product Backlog Item | indicadores de qualidade dados no Insurance Plan ; indicadores de qualidade dados do Healthcare Provider | Catalog Framework | Catalog Framework | Near-parallel titles differing only by target entity (Insurance Plan vs Healthcare Provider) | Medium |
| 145840 / 146558 | Product Backlog Item / Product Backlog Item | Implementação de mecanismo de feedback ; PBI-05.03 — Gerar e enviar feedback ao negócio em caso de rejeição | Catalog Framework | Sprint 0.1 | Both describe implementing the business-feedback mechanism | Medium |
| 145838 / 146551 | Product Backlog Item / Product Backlog Item | Instanciação inicial no OntoServer ; PBI-04.02 — Implementar integração com Ontoserver | Catalog Framework | Catalog Framework / Sprint 0.1 | Both cover standing up / integrating with Ontoserver | Medium |
| 145836 / 146530 | Product Backlog Item / Product Backlog Item | Acessos da equipa ; PBI-01.03 — Definir e configurar contas técnicas e permissões | Catalog Framework | Catalog Framework | Both concern team access / technical accounts and permissions | Medium |
| 145839 / 146538 | Product Backlog Item / Product Backlog Item | Construção de fluxo de validação de ficheiro de carregamento ; PBI-02.05 — Atualizar estado para `Validating` e chamar o Validation Service | Catalog Framework | Sprint 0.1 | Both describe the load-file validation workflow / invoking the Validation Service | Medium |

**Summary:** This check is NON-DETERMINISTIC and its output is candidate pairs for human review only — no two items are asserted to be duplicates. Comparison strategy: the complete requirement-level active set (63 PBI/Bug items in Proposed/InProgress, deduped) was small enough to enumerate in full, so titles were compared pairwise semantically across the whole set (ignoring casing, punctuation, and prefix tags like "PBI-xx.xx") rather than sampling neighbors via search_workitem; all items sit in a single area path (Catalog Framework), so no Low same-topic-different-area candidates apply. Titles only; scan complete.
