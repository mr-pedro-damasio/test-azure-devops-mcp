# Azure DevOps Backlog Quality Toolkit

> A ready-to-run dev container wired to the **Azure DevOps MCP server**, with a suite of single-purpose prompts for auditing backlog quality in Azure DevOps — driven from Claude Code and other pre-installed AI assistants.

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/mr-pedro-damasio/test-azure-devops-mcp)

---

## Overview

This repository is a self-contained environment for **auditing Azure DevOps backlog quality**. It pairs a zero-configuration dev container with the [Azure DevOps MCP server](https://github.com/microsoft/azure-devops-mcp) and a curated suite of read-only audit prompts.

The scope is **work items only** — descriptions, acceptance criteria, estimates, hierarchy, iterations, and hygiene. It never touches repos, pipelines, or code, and every check is **strictly read-only**: it reports findings and never creates, updates, or links work items.

The development environment runs identically in GitHub Codespaces and in a local VS Code dev container.

---

## What's Included

- **Backlog audit suite** — 16 single-purpose prompts in [`PROMPTS.md`](PROMPTS.md), grouped into Completeness, Structure, Hygiene, and Readiness. Each produces a deterministic, factual Markdown report.
- **Shared conventions** — [`SHARED_CONVENTIONS.md`](SHARED_CONVENTIONS.md) (v2) defines the process-agnostic rules every prompt inherits: preflight capability checks, category→state-name translation, pagination/truncation handling, text normalization, and the report output contract.
- **Azure DevOps MCP server** — pre-configured in [`.mcp.json`](.mcp.json) for the `DSTILuzSaude` project, run via `npx -y @azure-devops/mcp`.
- **Dev Container** — Ubuntu-based, with Node.js, GitHub CLI, and Azure CLI.
- **AI Assistants** — Claude Code, GitHub Copilot, Antigravity CLI, Codex, and opencode — all pre-installed.
- **Git configuration** — `.gitignore` for env files, OS artifacts, and editor files.

---

## Getting Started

### Option 1 — GitHub Codespaces (recommended)

1. Click **Open in GitHub Codespaces** above, or go to **Code → Codespaces → New codespace**.
2. Wait for the environment to build (first run takes a few minutes — `post-create.sh` installs the AI CLIs).
3. Authenticate to Azure DevOps (see [Authentication](#authentication)).
4. Run an audit (see [Running an audit](#running-an-audit)).

### Option 2 — Dev Container (local)

**Prerequisites:** [Docker Desktop](https://www.docker.com/products/docker-desktop) and the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) for VS Code.

1. Clone the repository and open it in VS Code.
2. When prompted, click **Reopen in Container** (or run `Dev Containers: Reopen in Container` from the command palette).
3. Authenticate to Azure DevOps (see [Authentication](#authentication)).
4. Run an audit (see [Running an audit](#running-an-audit)).

---

## Authentication

The Azure DevOps MCP server authenticates through the Azure CLI. Sign in once per environment:

```bash
az login
```

The MCP server is scoped to the `DSTILuzSaude` Azure DevOps organization/project via [`.mcp.json`](.mcp.json). To target a different project, change the argument passed to `@azure-devops/mcp`. If you need to (re)register the server manually:

```bash
claude mcp add --scope project azure-devops -- npx -y @azure-devops/mcp DSTILuzSaude
```

(This is the command recorded in `INSTALL_AZURE_DEVOPS_MSCP.md`.)

---

## Running an audit

Each prompt in [`PROMPTS.md`](PROMPTS.md) is a self-contained backlog check. To run one, open Claude Code and give it the prompt text along with the target project:

1. Pick a check from `PROMPTS.md` (e.g. *Prompt 4: Orphan Detector*).
2. Paste its prompt into Claude Code, supplying the required `project` parameter.
3. The check runs the preflight from `SHARED_CONVENTIONS.md`, queries Azure DevOps via the MCP server, and writes a report.

Reports are written to `./backlog-reports/` as
`backlog-check-<check-slug>-<project>-<YYYY-MM-DD>.md`. They share a common table format so multiple check reports can be concatenated into a single backlog-health document. Re-running a check on the same day overwrites its own file (reports are idempotent per day).

See the [Prompt Index](PROMPTS.md#prompt-index) in `PROMPTS.md` for the full catalogue of checks, file slugs, and severity anchors.

---

## AI Tools

The following AI coding assistants are pre-installed in this environment:

| Tool | CLI | VS Code Extension |
|------|-----|-------------------|
| [Claude Code](https://claude.ai/code) | `claude` | Anthropic Claude Code |
| [GitHub Copilot](https://github.com/features/copilot) | `copilot` | GitHub Copilot / Copilot Chat |
| [Antigravity CLI](https://antigravity.google/product/antigravity-cli) | `agy` | Gemini Code Assist |
| [Codex](https://developers.openai.com/codex/cli) | `codex` | OpenAI ChatGPT |
| [opencode](https://opencode.ai) | `opencode` | — |

Agent behavior and repository conventions are defined in `CLAUDE.md` → `AGENTS.md` → `.github/copilot-instructions.md`.

---

## Repository Layout

| Path | Purpose |
|------|---------|
| `PROMPTS.md` | The 16 backlog-quality audit prompts, grouped by category. |
| `SHARED_CONVENTIONS.md` | v2 conventions inherited by every prompt (preflight, guardrails, output contract). |
| `.mcp.json` | Azure DevOps MCP server configuration. |
| `INSTALL_AZURE_DEVOPS_MSCP.md` | Manual MCP registration command. |
| `.devcontainer/` | Dev container definition and post-create setup. |
| `AGENTS.md` / `CLAUDE.md` | Agent instructions and repository conventions. |

---

## License

[MIT](LICENSE) © 2026 mr-pedro-damasio
