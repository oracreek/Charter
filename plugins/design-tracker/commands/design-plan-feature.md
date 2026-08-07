---
name: design-plan-feature
description: Explore a feature idea; clarify UX and status; no code. Use when planning before build.
---

# Plan feature (explore — no code)

Feature or topic: $ARGUMENTS

## Required reads

- `_designs/README.md`
- `_designs/feature-catalog.md`
- `_designs/WORKFLOW.md`
- Matching story under `_designs/stories/` (if it exists)
- Linked `_designs/architecture/` and `_designs/decisions/` files
- Design tracker rules (plugin or project)

## Steps

1. Locate the feature in the catalog by ID, name, or slug. If missing, note that a new story may be needed.
2. Summarize **current behavior** (from story + code evidence if present), **planned behavior**, and **known gaps**.
3. Propose an appropriate status: **Proposed**, **Planned**, or **In Design** — with rationale.
4. List **open questions** for the user (UX, schema, permissions, scope).
5. Flag conflicts with accepted ADRs or architecture notes. Prefer the simpler future-state approach.

## Stop / ask rules

Pause and ask clarifying questions before recommending build if the idea:

- Conflicts with an accepted ADR in `_designs/decisions/`
- Adds avoidable complexity relative to documented future state
- Weakens security (unscoped public endpoints, auth gaps)
- Diverges from project practices in `AGENTS.md` or project rules

## Outputs

Return:

- Feature summary and recommended status
- Open questions (numbered)
- Whether `_designs/stories/` or a new ADR is needed
- Suggested next command: `/design-new-story`, `/design-new-adr`, or `/design-start-feature`

## Do not

- Do not write or modify application code.
- Do not mark any feature **Verified**.
- Do not create competing docs outside `_designs/`.
