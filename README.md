# agents-scaffold

<p align="center">
  <img src="./assets/readme/hero.svg" width="100%" alt="Root AGENTS.md, state files read when relevant, and scoped subtree contracts.">
</p>

<p align="center">
  <a href="./LICENSE"><img src="https://img.shields.io/badge/License-MIT-14b8a6.svg?style=flat-square" alt="MIT license"></a>
  <a href="https://agents.md/"><img src="https://img.shields.io/badge/AGENTS.md-convention-0f172a?style=flat-square" alt="AGENTS.md convention"></a>
</p>

A small `AGENTS.md` contract, state files read when relevant, and optional
subtree contracts. Based on the [AGENTS.md convention](https://agents.md/)
and the [DOX hierarchy](https://github.com/agent0ai/dox).

It exists so agents can be high-quality without one giant instruction blob:
the root stays short, state files are read when relevant, and local rules stay
scoped to where they apply.

## Use it

### Manual

1. Copy [`AGENTS.md`](./AGENTS.md) into your repository root.
2. Copy the six files in [`templates/`](./templates) into `.agents/`.
3. Fill the placeholders, then add the ignore rules from [`INSTALL.md`](./INSTALL.md).

### Agent

Give your coding agent this file:

<https://raw.githubusercontent.com/jr2804/agents-scaffold/main/INSTALL.md>

## Context Tree

The root `AGENTS.md` is the entry point. `.agents/` holds current project
contracts, read when their trigger applies. Subtree `AGENTS.md` files add rules
for a specific directory. Clients differ in discovery; explicit user
instructions win.

## Principles

- Keep the root short.
- No tree views, history logs, or TODO lists in instructions.
- One canonical home per rule; reference instead of restating.
- Add subtree contracts only where local rules need their own scope.
- Keep the ⛔ No Patching section last.

## License

MIT. Upstream notices are in [`THIRD_PARTY_NOTICES.md`](./THIRD_PARTY_NOTICES.md).

<p align="center">
  <a href="https://github.com/oil-oil/beautify-github-readme"><img
    src="./assets/readme/made-with-beautify.svg"
    width="480"
    alt="Footer credit for the README design skill."></a>
</p>
