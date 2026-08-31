---
name: oracreek-finish-feature
description: Resume an existing story from pre-flight, implement, sync, or verify. Skip plan/docs by default.
---

# Finish feature (resume → Built - Unverified, optional Verified)

Feature: $ARGUMENTS

## Orchestration rules

Resume an **existing** story from pre-flight or implement. **Skip Phase 1–2** by default.

After **each** phase, **STOP** and return:

- **Phase summary** — what was done
- **Decisions** — status, scope, files
- **Open questions** — numbered, if any remain
- **Next phase** — name and what will happen next

Do **not** advance until the user replies, unless they said **`run all phases without stopping`** in the same message.

- Use **AskQuestion** for discrete choices when scope or entry phase is ambiguous.
- **Default:** after Phase 5, stop at **Built - Unverified**, list unchecked verification checklist items, and remind the user to reply **`verify now`** when ready. Only run Phase 6 if the user explicitly says **`verify now`** (or equivalent).
- Never mark **Verified** from schema evidence alone. Only Phase 6 may promote to **Verified** (see `/oracreek-verify-feature`).
- On every story status change, **`git mv`** the file into the matching `_oracreek/stories/<status-folder>/` and fix catalog + cross-links per `_oracreek/WORKFLOW.md` "Story file location".

## Required reads (once at start)

- `_oracreek/README.md`
- `_oracreek/WORKFLOW.md`
- `_oracreek/feature-catalog.md`
- OraCreek Charter rules (plugin or project)
- Resolve matching story from $ARGUMENTS (catalog ID, slug, or name — stories live in status subfolders)
- Linked `_oracreek/architecture/` and `_oracreek/decisions/` files from that story

## Entry phase selection

1. Resolve story from catalog. **Error** if no story exists — suggest `/oracreek-e2e-feature` instead.
2. Read current story **Status** and choose starting phase:

| Status | Default start | Notes |
|--------|---------------|-------|
| **Proposed** | Phase 1 | Ask user to approve direction or run Phase 1 plan first |
| **Planned** / **In Design** | Phase 3 | Offer Phase 1 replan if acceptance criteria are incomplete |
| **In Build** | Phase 4 | User may say **`implement now`** to confirm |
| **Built - Unverified** | Phase 5 | Sync docs, then optional verify |
| **Verified** | Stop | Report already verified; offer hygiene audit only |

3. User says **`implement now`** and story is **In Build** or approved **Planned** / **In Design**: start at Phase 4.
4. User says **`verify now`**: run Phase 6 after Phase 5 (or immediately if story is already synced and checklist-ready).

## Phase 1 — Plan (only when needed)

Follow `/oracreek-plan-feature` when status is **Proposed** or user requests replan.

**Gate:** User approves status and scope before Phase 2 or Phase 3.

## Phase 2 — Document (only when needed)

Follow `/oracreek-new-story` and `/oracreek-new-adr` if needed. Skip when story and catalog are already complete unless user asks to extend docs.

**Gate:** User approves story path and catalog row.

## Phase 3 — Pre-flight

Follow `/oracreek-start-feature`.

**Gate:** User confirms implementation plan. Move story to `in-build/` if not already there.

## Phase 4 — Implement

Follow `/oracreek-implement-feature`.

End at **Built - Unverified** with story in `built-unverified/` unless Phase 5 handles sync.

## Phase 5 — Sync

Follow `/oracreek-sync-after-build`.

**Gate (default):** Stop at **Built - Unverified**. List verification checklist items still open. Tell user to reply **`verify now`** to run Phase 6.

## Phase 6 — Verify (optional)

Run only when the user explicitly says **`verify now`**.

Follow `/oracreek-verify-feature`. Move story to `verified/` only if the full checklist passes.

## Final outputs

Return:

- Story path and current status
- Catalog status
- Phases completed and starting phase used
- Files updated (docs and code)

## Do not

- Do not skip user gates unless **`run all phases without stopping`** was requested.
- Do not mark **Verified** without completing Phase 6 checklist against live code.
- Do not create a new story when one already exists — extend the existing story instead.
