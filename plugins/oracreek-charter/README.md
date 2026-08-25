# oracreek-charter

Cursor plugin for **agent governance**: architecture, design docs, status, and testing/validation, with `/oracreek-*` slash commands.

This is the product plugin in the [jesgorsuch/design-tracker](https://github.com/jesgorsuch/design-tracker) repository. Cursor Marketplace listing is planned after the repository is public.

## Included

| Component | Contents |
|-----------|----------|
| `rules/` | Always-on Oracreek Charter + `_oracreek/**` folder guidance |
| `commands/` | Full lifecycle: bootstrap, plan, e2e, implement, sync, verify, hygiene |
| `skills/oracreek-charter/` | Workflow reference for agents |
| `skills/oracreek-bootstrap/` | Scaffold `_oracreek/` into a project (templates included) |

## Install (local iteration)

From this marketplace repo (or after publishing):

1. Link or copy this plugin folder into your Cursor local plugins dir:

```text
%USERPROFILE%\.cursor\plugins\local\oracreek-charter
```

On Windows (PowerShell), from the marketplace root:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.cursor\plugins\local" | Out-Null
New-Item -ItemType Junction -Force -Path "$env:USERPROFILE\.cursor\plugins\local\oracreek-charter" -Target "$PWD\plugins\oracreek-charter"
```

2. **Developer: Reload Window** in Cursor.
3. Confirm under **Customize** that rules/skills/commands from **Oracreek Charter** appear.
4. In a target project, run `/oracreek-bootstrap`, then `/oracreek-plan-feature` or `/oracreek-e2e-feature`.

## What stays project-local

The plugin ships **process + empty templates**. Each product repo owns:

- `_oracreek/stories/`, `_oracreek/decisions/`, `_oracreek/architecture/`
- Stack-specific verify wording (optional edits after bootstrap)
- `AGENTS.md` / project rules for runtime specifics

## Command overview

Type `/oracreek-` in Agent chat:

- `/oracreek-bootstrap` — scaffold `_oracreek/`
- `/oracreek-e2e-feature` — plan → build → sync (optional `verify now`)
- `/oracreek-finish-feature` — resume an existing story
- `/oracreek-plan-feature` / `/oracreek-new-story` / `/oracreek-new-adr`
- `/oracreek-start-feature` → `/oracreek-implement-feature` → `/oracreek-sync-after-build` → `/oracreek-verify-feature`
- `/oracreek-review-unverified` / `/oracreek-audit-catalog`

## Iterate on this standard

Edit files under `plugins/oracreek-charter/` in this repo. With a junction into `~\.cursor\plugins\local\`, Reload Window to pick up changes across all projects.
