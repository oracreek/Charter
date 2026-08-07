---
name: design-bootstrap
description: >-
  Scaffold a project-local _designs/ tree (README, WORKFLOW, catalog, templates)
  for the design-tracker workflow. Use when adopting design tracker in a new or
  existing repo, or when the user runs /design-bootstrap.
disable-model-invocation: true
---

# Design bootstrap

## Instructions

1. Inspect the workspace for an existing `_designs/` directory.
2. If `README.md` and `WORKFLOW.md` already exist, list what is present and ask before overwriting.
3. Copy scaffold files from [scaffold/](scaffold/) into the project root as `_designs/...`:
   - `scaffold/README.md` → `_designs/README.md`
   - `scaffold/WORKFLOW.md` → `_designs/WORKFLOW.md`
   - `scaffold/feature-catalog.md` → `_designs/feature-catalog.md`
   - `scaffold/templates/*` → `_designs/templates/*`
4. Ensure empty dirs exist for durable areas (create `.gitkeep` if needed):
   - `_designs/architecture/`
   - `_designs/decisions/`
   - `_designs/archive/`
5. Do **not** pre-create empty `stories/<status>/` folders.
6. Optionally customize verification checklist wording in `WORKFLOW.md` from `AGENTS.md` / project README (routes path, auth). Keep the status model identical.
7. Report created paths and next steps: `/design-plan-feature` or `/design-e2e-feature`.

## Do not

- Invent product feature stories
- Mark anything **Verified**
- Copy product-specific ADRs from other repos
