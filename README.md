# Oracreek Design Tracker

Cursor plugin marketplace for the reusable **design-tracker** workflow (feature stories, ADRs, catalog, `/design-*` commands), plus the upstream starter plugin examples.

## Plugins

| Plugin | Path | Purpose |
|--------|------|---------|
| **design-tracker** | [`plugins/design-tracker`](plugins/design-tracker) | Production workflow: rules, skills, slash commands, `_designs` bootstrap |
| starter-simple | `plugins/starter-simple` | Minimal Cursor plugin starter |
| starter-advanced | `plugins/starter-advanced` | Full-featured starter (rules, skills, agents, commands, hooks, MCP) |

## Quick start (design-tracker)

1. Install locally for iteration:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.cursor\plugins\local" | Out-Null
New-Item -ItemType Junction -Force `
  -Path "$env:USERPROFILE\.cursor\plugins\local\design-tracker" `
  -Target "$PWD\plugins\design-tracker"
```

2. Reload the Cursor window.
3. In any project: `/design-bootstrap`, then `/design-e2e-feature <topic>`.

See [`plugins/design-tracker/README.md`](plugins/design-tracker/README.md) for the full command map.

## Validate

```bash
node scripts/validate-template.mjs
```

## Add another plugin

Follow [`docs/add-a-plugin.md`](docs/add-a-plugin.md).
