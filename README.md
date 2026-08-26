# OraCreek Charter

[![CI](https://github.com/jesgorsuch/OraCreek-Charter/actions/workflows/ci.yml/badge.svg)](https://github.com/jesgorsuch/OraCreek-Charter/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A Cursor plugin for **agent governance**: architecture, design docs, status, and testing/validation.

OraCreek project, maintained by [@jesgorsuch](https://github.com/jesgorsuch). Cursor Marketplace listing is planned after this repository is public and reviewed.

## What it does

Install the plugin, then in any product repo:

1. `/oracreek-bootstrap` — scaffold `_oracreek/` (stories, decisions, architecture, catalog).
2. `/oracreek-e2e-feature <topic>` — plan → build → sync in one pass.
3. `/oracreek-verify-feature` / `/oracreek-audit-catalog` — close the loop so work does not stall as “unverified.”

The plugin ships **process and empty templates**. Each product repo owns its stories, ADRs, and stack-specific verify wording.

## Install (local)

Until the Marketplace listing is live, link the plugin from this clone:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.cursor\plugins\local" | Out-Null
New-Item -ItemType Junction -Force `
  -Path "$env:USERPROFILE\.cursor\plugins\local\oracreek-charter" `
  -Target "$PWD\plugins\oracreek-charter"
```

Then **Developer: Reload Window**. Confirm under **Customize** that OraCreek Charter rules, skills, and commands appear.

macOS / Linux:

```bash
mkdir -p ~/.cursor/plugins/local
ln -s "$PWD/plugins/oracreek-charter" ~/.cursor/plugins/local/oracreek-charter
```

Full command map: [`plugins/oracreek-charter/README.md`](plugins/oracreek-charter/README.md).

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
