# design-tracker

Cursor plugin for a reusable **feature design tracker**: status-based stories, ADRs, catalog, and `/design-*` slash commands.

This is the product plugin in the [design-tracker](https://github.com/jesgorsuch/design-tracker) repository. Cursor Marketplace listing is planned after the repository is public.

## Included

| Component | Contents |
|-----------|----------|
| `rules/` | Always-on design tracker + `_designs/**` folder guidance |
| `commands/` | Full lifecycle: bootstrap, plan, e2e, implement, sync, verify, hygiene |
| `skills/design-tracker/` | Workflow reference for agents |
| `skills/design-bootstrap/` | Scaffold `_designs/` into a project (templates included) |

## Install (local iteration)

From this marketplace repo (or after publishing):

1. Link or copy this plugin folder into your Cursor local plugins dir:

```text
%USERPROFILE%\.cursor\plugins\local\design-tracker
```

On Windows (PowerShell), from the marketplace root:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.cursor\plugins\local" | Out-Null
New-Item -ItemType Junction -Force -Path "$env:USERPROFILE\.cursor\plugins\local\design-tracker" -Target "$PWD\plugins\design-tracker"
```

2. **Developer: Reload Window** in Cursor.
3. Confirm under **Customize** that rules/skills/commands from **Design Tracker** appear.
4. In a target project, run `/design-bootstrap`, then `/design-plan-feature` or `/design-e2e-feature`.

## What stays project-local

The plugin ships **process + empty templates**. Each product repo owns:

- `_designs/stories/`, `_designs/decisions/`, `_designs/architecture/`
- Stack-specific verify wording (optional edits after bootstrap)
- `AGENTS.md` / project rules for runtime specifics

## Command overview

Type `/design-` in Agent chat:

- `/design-bootstrap` — scaffold `_designs/`
- `/design-e2e-feature` — plan → build → sync (optional `verify now`)
- `/design-finish-feature` — resume an existing story
- `/design-plan-feature` / `/design-new-story` / `/design-new-adr`
- `/design-start-feature` → `/design-implement-feature` → `/design-sync-after-build` → `/design-verify-feature`
- `/design-review-unverified` / `/design-audit-catalog`

## Iterate on this standard

Edit files under `plugins/design-tracker/` in this repo. With a junction into `~\.cursor\plugins\local\`, Reload Window to pick up changes across all projects.
