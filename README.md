# agents-scaffold

<p align="center">
  <img src="./assets/readme/hero.svg" width="100%" alt="agents-scaffold — self-documenting AGENTS.md hierarchy. AGENTS.md at the root always injected, with demand-loaded files under .agents/ (ONBOARDING, POLICIES, FILES, HISTORY, MAINTENANCE, plans, history).">
</p>

> **AGENTS.md is for agents, not humans.** One sentence of project
> description, then rules. Everything else is demand-loaded.

**agents-scaffold** ships a copy-paste convention for keeping
`AGENTS.md` lean. The root file holds only the rules every LLM call
needs; everything else lives in `.agents/` files (loaded on demand)
or subtree `AGENTS.md` files (loaded on directory entry).

## Problem

`AGENTS.md` is injected on every LLM call. Most files are bloated with
tree views, history entries, TODO lists, and verbose descriptions — all
things the agent can discover on demand. Every redundant byte dilutes
the signal-to-noise ratio of every call.

## Mechanism

```mermaid
%%{init: {
  'theme': 'base',
  'themeVariables': {
    'primaryColor': '#eff6ff',
    'primaryTextColor': '#1e293b',
    'primaryBorderColor': '#3b82f6',
    'lineColor': '#64748b',
    'fontSize': '13px',
    'fontFamily': 'Inter, system-ui, -apple-system, sans-serif'
  }
}}%%
flowchart LR
  LLM(["🤖 <b>LLM Call</b><br/><i>Prompt Context</i>"]):::main

  subgraph S_Root[" <b>Root AGENTS.md</b> · Always Injected "]
    direction TB
    R["<b>Root Rail</b><br/>• 1-sentence description<br/>• 5–10 essential rules<br/>• ⛔ No-patching block"]:::rootNode
  end

  subgraph S_Agents[" <b>.agents/</b> · Demand-Loaded "]
    direction TB
    A_Core["<b>Core Policies & Entry</b><br/>• ONBOARDING.md <i>(new session)</i><br/>• POLICIES.md <i>(always / standards)</i><br/>• FILES.md <i>(file & path constants)</i>"]:::agentNode
    A_Context["<b>Context & Knowledge</b><br/>• HISTORY.md & history/ <i>(decisions)</i><br/>• MAINTENANCE.md <i>(keeping DOX lean)</i><br/>• plans/ <i>(active features, gitignored)</i>"]:::agentNode
  end

  subgraph S_Sub[" <b>Subtree DOX</b> · On Dir Entry "]
    direction TB
    S_Tree["<b>Scoped AGENTS.md</b><br/>• src/api/AGENTS.md<br/>• tests/AGENTS.md<br/>• <i>Local contracts & rules</i>"]:::subNode
  end

  LLM ==>|Always Injected| S_Root
  LLM -.->|Demand: New Session / Policy / Paths| A_Core
  LLM -.->|Demand: Decisions / Plans| A_Context
  LLM -.->|Context: Working in Subtree| S_Sub

  classDef main fill:#f1f5f9,stroke:#0284c7,stroke-width:2px,color:#0f172a;
  classDef rootNode fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e3a8a;
  classDef agentNode fill:#f0fdf4,stroke:#16a34a,stroke-width:1.5px,color:#14532d;
  classDef subNode fill:#faf5ff,stroke:#9333ea,stroke-width:1.5px,color:#581c87;
  classDef default rx:6px,ry:6px;
```

## Quick start

### Manual Integration

1. Copy `AGENTS.md`, `.agents/`, and `INSTALL.md` into any repository.
2. Fill `AGENTS.md` §2–4: one-sentence description, 5–10 always-on rules, child DOX index.
3. Feed `INSTALL.md` to your agent — it performs the full migration.

See [`INSTALL.md`](./INSTALL.md) for the complete migration checklist.

### Agent Setup

Pipe `INSTALL.md` straight from this repo into your coding agent and let it perform the migration autonomously:

```bash
# macOS / Linux
curl -fsSL https://codeberg.org/jr2804/agents-scaffold/raw/branch/main/INSTALL.md | <agent-cli>

# Windows (PowerShell)
irm https://codeberg.org/jr2804/agents-scaffold/raw/branch/main/INSTALL.md | <agent-cli>
```

Adapt `<agent-cli>` to your tool's prompt-from-stdin entry point (e.g. Claude Code, opencode, aider, fabric).

Or paste this single instruction into any agent:

```text
Please install or update the framework given in https://codeberg.org/jr2804/agents-scaffold/raw/branch/main/INSTALL.md
```

## Principles

| Principle                           | Why it matters                                                            |
| ----------------------------------- | ------------------------------------------------------------------------- |
| AGENTS.md is for agents, not humans | Max signal density on every call                                          |
| No tree views                       | Generate on demand: `rg --files \| tree-cli --fromfile`                   |
| No history                          | Git log has it; only record decisions costly to rediscover                |
| No TODO lists                       | Use an issue tracker or `beads`                                           |
| DOX hierarchy                       | Subtree AGENTS.md files own local contracts; root stays lean              |
| ⛔ No Patching                      | Content appended after the blocker section is invalid and must be removed |

## Credits

- Base convention: [dox](https://github.com/agent0ai/dox) — self-documenting AGENTS.md hierarchy.
- Extended with structured `.agents/` files and anti-bloat patterns from [knox](https://github.com/anomalyco/knox).

<p align="center">
  <a href="https://github.com/oil-oil/beautify-github-readme"><img src="./assets/readme/made-with-beautify.svg" width="300" alt="README made with beautify-github-readme"></a>
</p>
