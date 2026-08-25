---
name: oracreek-sync-after-build
description: Update story, catalog, and architecture after code lands. Prefer Built - Unverified over Verified.
---

# Sync docs after build

Feature: $ARGUMENTS

## Required reads

- `_oracreek/WORKFLOW.md`
- Matching story under `_oracreek/stories/` (resolve via the catalog link — stories are grouped in subfolders by status)
- `_oracreek/feature-catalog.md`
- Linked `_oracreek/architecture/` and `_oracreek/decisions/`
- Oracreek Charter rules (plugin or project)
- Relevant code paths changed (verify evidence links are accurate)

## Steps

1. Resolve story from $ARGUMENTS.
2. Update the story file:
   - **Current behavior** and **known gaps**
   - **Code evidence** table (routes, handlers, UI, schema as applicable)
   - **Last reviewed** date
   - Status: **Built - Unverified** unless verification was completed in this session
   - Verification checklist checkboxes (only check items actually validated)
3. If status changed, move the story file (`git mv`) into the matching status subfolder per `_oracreek/WORKFLOW.md` "Story file location", and fix its internal relative links plus every cross-link to it.
4. Update `_oracreek/feature-catalog.md` status column and link path if changed.
5. Update linked `_oracreek/architecture/` notes if data flow or tables changed.
6. Add or update `_oracreek/decisions/` if implementation forked from prior docs.
7. Move superseded content to `_oracreek/archive/` — do not leave duplicate sources of truth.

## Stop / ask rules

Ask if:

- Catalog status should be **Verified** but checklist was not run — redirect to `/oracreek-verify-feature`
- Two docs claim to be canonical for the same feature

## Outputs

Return:

- List of doc files updated
- Current story status and catalog status
- Items still needing `/oracreek-verify-feature`

## Do not

- Do not mark **Verified** unless you completed the full checklist from `_oracreek/WORKFLOW.md` against live code in this turn. Prefer leaving **Built - Unverified** and recommending `/oracreek-verify-feature`.
