---
name: oracreek-implement-feature
description: Implement to story acceptance criteria; end at Built - Unverified. Never mark Verified.
---

# Implement feature (code + Built - Unverified)

Feature: $ARGUMENTS

## Required reads

- `_oracreek/README.md`
- Matching story under `_oracreek/stories/` (stories are grouped in subfolders by status)
- Linked `_oracreek/architecture/` and `_oracreek/decisions/`
- OraCreek Charter rules (plugin or project)
- Relevant application source, schema, and UI entry points for this project

## Steps

1. Resolve story from $ARGUMENTS (catalog ID, slug, or name).
2. If story is missing or status is **Proposed** without approval, run pre-flight logic from `/oracreek-start-feature` first or ask me to confirm scope.
3. Implement only what matches **acceptance criteria** and **planned behavior** in the story. Match existing code conventions.
4. If implementation requires an architecture fork not covered by ADRs, **stop and ask** or draft ADR via `/oracreek-new-adr` before proceeding.
5. After code changes:
   - Update story: **current behavior**, **code evidence**, set status to **Built - Unverified**
   - Move the story file (`git mv`) into `_oracreek/stories/built-unverified/` and fix its internal relative links plus every cross-link to it (see `_oracreek/WORKFLOW.md` "Story file location")
   - Note remaining **gaps** and unchecked verification items
   - List doc updates still needed (catalog, architecture)
6. Do **not** mark **Verified** in this command — use `/oracreek-verify-feature` or `/oracreek-sync-after-build` next.

## Stop / ask rules

Pause if:

- Conflicts with accepted ADRs or the project's security model
- Scope creep beyond the story
- Unclear UX that would hard-code wrong behavior

## Outputs

Return:

- Summary of code changes (files touched)
- Story status set to **Built - Unverified**
- Verification checklist items still open
- Reminder: run `/oracreek-sync-after-build` then `/oracreek-verify-feature`

## Do not

- Do not mark **Verified** (only `/oracreek-verify-feature` may do that after checklist pass).
- Do not leave competing docs outside `_oracreek/`.
