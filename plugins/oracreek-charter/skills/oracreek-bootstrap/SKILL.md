---
name: oracreek-bootstrap
description: >-
  Scaffold a project-local _oracreek/ tree (README, WORKFLOW, catalog, templates)
  for the oracreek-charter workflow. Use when adopting Oracreek Charter in a new or
  existing repo, or when the user runs /oracreek-bootstrap.
disable-model-invocation: true
---

# Oracreek Charter bootstrap

## Instructions

1. Inspect the workspace for an existing `_oracreek/` directory.
2. If `README.md` and `WORKFLOW.md` already exist, list what is present and ask before overwriting.
3. Copy scaffold files from [scaffold/](scaffold/) into the project root as `_oracreek/...`:
   - `scaffold/README.md` → `_oracreek/README.md`
   - `scaffold/WORKFLOW.md` → `_oracreek/WORKFLOW.md`
   - `scaffold/feature-catalog.md` → `_oracreek/feature-catalog.md`
   - `scaffold/templates/*` → `_oracreek/templates/*`
4. Ensure empty dirs exist for durable areas (create `.gitkeep` if needed):
   - `_oracreek/architecture/`
   - `_oracreek/decisions/`
   - `_oracreek/archive/`
5. Do **not** pre-create empty `stories/<status>/` folders.
6. Optionally customize verification checklist wording in `WORKFLOW.md` from `AGENTS.md` / project README (routes path, auth). Keep the status model identical.
7. Report created paths and next steps: `/oracreek-plan-feature` or `/oracreek-e2e-feature`.

## Do not

- Invent product feature stories
- Mark anything **Verified**
- Copy product-specific ADRs from other repos
