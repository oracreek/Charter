# Design Tracker

[![CI](https://github.com/jesgorsuch/design-tracker/actions/workflows/ci.yml/badge.svg)](https://github.com/jesgorsuch/design-tracker/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A Cursor plugin for a reusable **feature design tracker**: status-based stories, architecture decision records (ADRs), a living catalog, and `/design-*` slash commands.

Oracreek project, maintained by [@jesgorsuch](https://github.com/jesgorsuch). Cursor Marketplace listing is planned after this repository is public and reviewed.

## What it does

Install the plugin, then in any product repo:

1. `/design-bootstrap` — scaffold a `_designs/` folder (stories, decisions, architecture, catalog).
2. `/design-e2e-feature <topic>` — plan → build → sync in one pass.
3. `/design-verify-feature` / `/design-audit-catalog` — close the loop so work does not stall as “unverified.”

The plugin ships **process and empty templates**. Each product repo owns its stories, ADRs, and stack-specific verify wording.

## Install (local)

Until the Marketplace listing is live, link the plugin from this clone:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.cursor\plugins\local" | Out-Null
New-Item -ItemType Junction -Force `
  -Path "$env:USERPROFILE\.cursor\plugins\local\design-tracker" `
  -Target "$PWD\plugins\design-tracker"
```

Then **Developer: Reload Window**. Confirm under **Customize** that Design Tracker rules, skills, and commands appear.

macOS / Linux:

```bash
mkdir -p ~/.cursor/plugins/local
ln -s "$PWD/plugins/design-tracker" ~/.cursor/plugins/local/design-tracker
```

Full command map: [`plugins/design-tracker/README.md`](plugins/design-tracker/README.md).

## Validate

```bash
node scripts/validate-template.mjs
```

## Versioning

`main` is the product. Published versions are git tags (`v0.1.0`, …) that match the plugin manifest. See [RELEASE.md](RELEASE.md).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Please read the [Code of Conduct](CODE_OF_CONDUCT.md) and [security policy](SECURITY.md).

## License

[MIT](LICENSE)
