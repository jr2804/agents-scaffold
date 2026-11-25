# agents-scaffold

<p align="center">
  <img src="./assets/readme/hero.svg" width="100%" alt="Three tiers of agent context: a root AGENTS.md, conditionally read .agents state files, and scoped subtree contracts.">
</p>

<p align="center">
  <a href="https://github.com/jr2804/agents-scaffold/releases"><img src="https://img.shields.io/github/v/release/jr2804/agents-scaffold?style=flat-square" alt="Latest release"></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/License-MIT-14b8a6.svg?style=flat-square" alt="MIT license"></a>
  <a href="https://agents.md/"><img src="https://img.shields.io/badge/AGENTS.md-convention-0f172a?style=flat-square" alt="AGENTS.md convention"></a>
</p>

> **AGENTS.md is for agents, not humans.** Keep the root focused on the rules
> that matter; move detail into files the agent reads only when relevant.

**agents-scaffold** is a copy-paste convention for keeping coding-agent context
lean, scoped, and maintainable. It combines a small root contract, conditionally
read `.agents/` state files, and optional subtree `AGENTS.md` files.

It is **not a runtime, parser, or universal loader**. AGENTS.md clients differ
in how they discover and inject files. This scaffold gives supporting agents
explicit read triggers and update rules; explicit user instructions still take
precedence.

## Why

Most `AGENTS.md` files accumulate tree views, history, TODO lists, and verbose
explanations. Those bytes dilute the signal on every request and drift quickly.

DOX separates stable contracts from discoverable detail:

| Tier | Read when | Owns |
| ---- | --------- | ---- |
| Root `AGENTS.md` | Starting work in the repository | One-sentence description, essential rules, indexes, patch protection |
| `.agents/*.md` | The stated trigger applies | Onboarding, policies, paths, tools, decisions, maintenance |
| Subtree `AGENTS.md` | Working inside that subtree | Local contracts that need their own scope |

The convention also sets size budgets, keeps implementation plans out of Git,
and archives completed plans as durable decisions.

## Quick start

### Manual integration

1. Copy `AGENTS.md`, `.agents/`, `INSTALL.md`, `LICENSE`, and `THIRD_PARTY_NOTICES.md` into your repository.
2. Fill the one-sentence description, **Project rules**, and **Child DOX Index** in `AGENTS.md`.
3. Feed `INSTALL.md` to your coding agent for the full migration and verification pass.

See [`INSTALL.md`](./INSTALL.md) for fresh-install, partial-install, and update modes.

### Agent setup

Pipe `INSTALL.md` from GitHub into your coding agent:

```bash
# macOS / Linux — pin SCAFFOLD_REF to a release tag or commit for reproducibility
SCAFFOLD_REF=main
curl -fsSL "https://raw.githubusercontent.com/jr2804/agents-scaffold/${SCAFFOLD_REF}/INSTALL.md" | <agent-cli>
```

```powershell
# Windows (PowerShell)
$SCAFFOLD_REF = "main"
irm "https://raw.githubusercontent.com/jr2804/agents-scaffold/$SCAFFOLD_REF/INSTALL.md" | <agent-cli>
```

Adapt `<agent-cli>` to your tool's prompt-from-stdin entry point. You can also
paste this instruction into an agent:

```text
Install or update the agents-scaffold convention from
https://raw.githubusercontent.com/jr2804/agents-scaffold/main/INSTALL.md
Use an immutable release tag or commit when reproducibility matters, and stop
with a clear report if the source cannot be fetched.
```

## Principles

| Principle | Why it matters |
| --------- | -------------- |
| AGENTS.md is for agents, not humans | Maximize signal density in repository instructions |
| No tree views | Generate them on demand |
| No routine history | Git owns the past; keep only decisions costly to rediscover |
| No TODO lists | Use an issue tracker or `beads` |
| One canonical home per rule | Reference detail instead of restating it |
| Scoped subtree contracts | Keep local rules near the code they govern |
| ⛔ No Patching | Prevent autonomous injection after the final marker |

## Relationship to related projects

Reviewed on 2026-11-25 against DOX at
[`765ae4a`](https://github.com/agent0ai/dox/commit/765ae4ac02cc884eefcd41a3d0f71941721adb89)
and AGENTS.md at
[`d001185`](https://github.com/agentsmd/agents.md/commit/d001185d792eb6402a58e4cbef1c228b309ec25d).

| Project | Role | How this scaffold relates |
| ------- | ---- | ------------------------- |
| [agentsmd/agents.md](https://github.com/agentsmd/agents.md) | Portable, open Markdown convention and ecosystem | Provides the baseline format; it is not a scaffold, schema, parser, or installer |
| [agent0ai/dox](https://github.com/agent0ai/dox) | Tiny parent/child instruction hierarchy | Conceptual ancestor; this project adds state files, budgets, migration, tooling, and patch protection |
| [anomalyco/knox](https://github.com/anomalyco/knox) | Structured `.agents/` context and anti-bloat patterns | Source of the state-layer and maintenance ideas |

This project is an intentional extension of DOX, not an outdated copy. Its
`.agents/` layout and numeric budgets are local conventions, not requirements
of the AGENTS.md format.

## Development

```bash
mise install
mise run check
mise run format-md
```

`check` is non-mutating and runs Markdown lint/format checks plus SVG XML
validation. GitHub Releases run the same check before tagging.

## Credits and license

- Base convention: [dox](https://github.com/agent0ai/dox) by Agent Zero.
- Structured state and anti-bloat patterns: [knox](https://github.com/anomalyco/knox).
- Portable format and precedence guidance: [AGENTS.md](https://github.com/agentsmd/agents.md).

Licensed under [MIT](./LICENSE). Upstream attributions and notices are preserved
in [`THIRD_PARTY_NOTICES.md`](./THIRD_PARTY_NOTICES.md).

<p align="center">
  <a href="https://github.com/oil-oil/beautify-github-readme"><img src="./assets/readme/made-with-beautify.svg" width="480" alt="Footer credit for the README design skill."></a>
</p>
