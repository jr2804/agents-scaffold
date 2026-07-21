# AGENTS.md — FILES

Single source of truth for paths, config keys, and naming conventions.
Kept compact — agents hallucinate less when they know where definitions live.

## Pattern

- One file owns each class of definition (paths, config defaults, enums).
- Import from that file. Never hard-code values in other modules.
- Variables that address files get `_file` suffix; directories get `_dir`.

## Project-specific sources of truth

| What | Where | Key names |
|------|-------|-----------|
| Path constants | `src/project/paths.py` | `CONFIG_DIR`, `CACHE_DIR`, ... |
| Config defaults | `src/project/config.py` | `DEFAULTS` dict, `Settings` model |
| Enums | `src/project/enums.py` | StrEnum members for roles, tasks, ... |
| CLI commands | `src/project/cli/` | Typer app entry points |
| [add more] | | |