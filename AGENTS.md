# Agent Instructions

Repository conventions for AI assistants (Claude Code, Copilot, Antigravity, Codex, opencode). `CLAUDE.md` and `.github/copilot-instructions.md` both defer to this file.

## What this repository is

An **Azure DevOps backlog-quality audit toolkit**. It is a dev container wired to the Azure DevOps MCP server (see `.mcp.json`) plus a suite of read-only audit prompts:

- `PROMPTS.md` — the 16 backlog-quality checks, grouped into Completeness, Structure, Hygiene, and Readiness.
- `SHARED_CONVENTIONS.md` — the v2 conventions every prompt inherits (preflight, field resolution, pagination, output contract).

The scope is **work items only** — never repos, pipelines, or source code.

## Guardrails (non-negotiable)

- **Read-only against Azure DevOps.** When running or reasoning about a backlog check, never call a mutating MCP tool (`wit_create_work_item`, `wit_update_work_item`, `wit_update_work_items_batch`, `wit_work_items_link`, `wit_work_item_unlink`, `wit_add_child_work_items`, `wit_add_work_item_comment`, etc.) — even if a finding looks trivially fixable. Report; do not fix.
- **Use only Azure DevOps MCP tools** for backlog data. Do not approximate results from partial data — if a required tool or permission is unavailable, say so and stop.
- **Never invent findings.** Every reported issue must trace to data actually returned by the MCP server. If a scan is truncated or a capability is missing, state it in the report summary rather than presenting a partial scan as complete.
- **Process-agnostic always.** Identify work item types by backlog level (Epic / Feature / Requirement) and states by category (Proposed / InProgress / Resolved / Completed / Removed) — never by hard-coded names like "User Story" or "PBI". Run the `SHARED_CONVENTIONS.md` preflight before any check.

## Running a check

Follow the prompt in `PROMPTS.md` verbatim and inherit `SHARED_CONVENTIONS.md`. Required input is `project`; thresholds use the prompt's inline `{name:=default}` values unless overridden.

Reports are written to `./backlog-reports/` as `backlog-check-<check-slug>-<project>-<YYYY-MM-DD>.md`, using the standard report block defined in the output contract. One check → one file; re-running on the same day overwrites its own file. If the runtime has no filesystem access, print the report inline and say so — never silently drop it.

## Editing behavior

- **Keep the two prompt files consistent.** `PROMPTS.md` and `SHARED_CONVENTIONS.md` cross-reference each other (check IDs, file slugs, severity anchors, v2 status). When you change a prompt, update the [Prompt Index](PROMPTS.md#prompt-index) and any matching entry in `SHARED_CONVENTIONS.md` in the same edit.
- **Preserve the stable check IDs and file slugs.** They are contracts (report filenames depend on them); do not renumber or rename them casually.
- **Preserve the output contract.** Every prompt must still write the standard report block so files remain concatenable. Prompt 9 (compliance matrix) and Prompt 8 (non-deterministic duplicate candidates) are the documented exceptions — keep their carve-outs intact.
- Make minimal, targeted edits. Match the surrounding tone: factual, imperative, no prose recommendations inside reports.

## Markup rules

- Markdown only. Wrap prose at ~80 columns to match the existing files.
- Keep prompt bodies inside fenced code blocks (```) exactly as they appear — they are copy-pasted into agents verbatim.
- Use tables with the existing column layouts; do not reorder or rename columns.

## Validation

There is no build or test step. Before finishing an edit:

- Confirm internal links and anchors still resolve (index ↔ prompts ↔ conventions).
- Confirm any check ID, slug, category, or severity you touched matches across `PROMPTS.md` and `SHARED_CONVENTIONS.md`.
