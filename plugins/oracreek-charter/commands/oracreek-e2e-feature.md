---
name: design-e2e-feature
description: One-step orchestration — plan → document → build → sync; stop at Built - Unverified unless verify now.
---

# End-to-end feature (plan → Built - Unverified, optional Verified)

Feature or topic: $ARGUMENTS

## Orchestration rules

Run phases 1–6 in order. After **each** phase, **STOP** and return:

- **Phase summary** — what was done
- **Decisions** — status, scope, ADR, files
- **Open questions** — numbered, if any remain
- **Next phase** — name and what will happen next

Do **not** advance until the user replies, unless they said **`run all phases without stopping`** in the same message.

- Use **AskQuestion** for discrete choices (roles, initial status, ADR needed yes/no).
- Use plain chat for open-ended UX or scope questions.
- **Default:** after Phase 5, stop at **Built - Unverified**, list unchecked verification checklist items, and remind the user to reply **`verify now`** when ready. Only run Phase 6 if the user explicitly says **`verify now`** (or equivalent) in the same or a later message.
- Never mark **Verified** from schema evidence alone. Only Phase 6 may promote to **Verified** (see `/design-verify-feature`).
- On every story status change, **`git mv`** the file into the matching `_designs/stories/<status-folder>/` and fix catalog + cross-links per `_designs/WORKFLOW.md` "Story file location".

## Required reads (once at start)

- `_designs/README.md`
- `_designs/WORKFLOW.md`
- `_designs/feature-catalog.md`
- Design tracker rules (plugin or project)
- Matching story under `_designs/stories/` (if it exists)
- Linked `_designs/architecture/` and `_designs/decisions/` files

If `_designs/` is missing, run `/design-bootstrap` (or the design-bootstrap skill) first, then continue.

## Shortcuts

- Existing story in **Planned** or **In Design**: skip Phase 1–2 unless the user asks to replan.
- User says **`plan only`**: stop after Phase 2.
- User says **`skip to implement`** with an approved story: jump to Phase 3.
- User says **`verify now`** in $ARGUMENTS or a follow-up: run Phase 6 after Phase 5 (or after sync if resuming).

## Phase 1 — Plan

Follow all sections of `/design-plan-feature` (Required reads, Steps, Stop / ask rules, Outputs, Do not).

**Gate:** User answers open questions and approves recommended status (**Proposed**, **Planned**, or **In Design**).

## Phase 2 — Document

Follow `/design-new-story`. If an architecture fork is needed (schema, public API, identity, security, durable integrations), also follow `/design-new-adr`.

**Gate:** User approves story path, catalog row, and ADR (if drafted).

## Phase 3 — Pre-flight

Follow `/design-start-feature`.

**Gate:** User confirms implementation plan and scope. Then move story to `_designs/stories/in-build/` and fix links.

## Phase 4 — Implement

Follow `/design-implement-feature`.

No **Verified** in this phase. End at **Built - Unverified** with story moved to `built-unverified/` unless Phase 5 will handle final sync.

## Phase 5 — Sync

Follow `/design-sync-after-build`.

**Gate (default):** Stop at **Built - Unverified**. List verification checklist items still open. Tell user to reply **`verify now`** to run Phase 6.

## Phase 6 — Verify (optional)

Run only when the user explicitly says **`verify now`**.

Follow `/design-verify-feature`. Move story to `verified/` only if the full checklist passes.

## Final outputs

Return:

- Story path and current status
- Catalog status
- Phases completed and any deferred (e.g. verify pending manual UI check)
- Files updated (docs and code)

## Do not

- Do not skip user gates unless **`run all phases without stopping`** was requested.
- Do not mark **Verified** without completing Phase 6 checklist against live code.
- Do not create competing docs outside `_designs/`.
