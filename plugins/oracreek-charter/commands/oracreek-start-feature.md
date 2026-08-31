---
name: oracreek-start-feature
description: Pre-flight a feature from story and ADRs; plan scope; ask on conflicts. No code until confirmed.
---

# Start feature (pre-flight)

Feature: $ARGUMENTS

## Required reads

- `_oracreek/README.md`
- `_oracreek/feature-catalog.md`
- `_oracreek/WORKFLOW.md`
- Matching story under `_oracreek/stories/` (resolve from catalog or $ARGUMENTS — stories are grouped in subfolders by status)
- Linked `_oracreek/architecture/` and `_oracreek/decisions/` files from that story
- OraCreek Charter rules (plugin or project)

## Steps

1. Resolve the story file from catalog ID, slug, or feature name in $ARGUMENTS.
2. Summarize **current vs planned behavior**, acceptance criteria, and **open questions**.
3. List proposed **implementation scope**: application files, schema/migrations, client assets as applicable.
4. State whether a **new ADR** is needed before coding.
5. If the user's intent conflicts with accepted ADRs or architecture, **stop and ask** — do not proceed to implementation.
6. Propose setting story status to **In Build**, including moving the file into `_oracreek/stories/in-build/` and fixing its links (apply only if I confirm in this turn — see `_oracreek/WORKFLOW.md` "Story file location").

## Stop / ask rules

Pause and ask before any code if:

- Request conflicts with `_oracreek/decisions/`
- New public routes would expose data without proper auth or scoping
- Proposed schema or data model adds complexity that documented simpler approaches already cover

## Outputs

Return:

- Pre-flight summary and implementation plan
- Affected files list
- Open questions requiring my answer
- Explicit: "Ready for `/oracreek-implement-feature` after confirmation"

## Do not

- Do not mark **Verified**.
- Do not implement code until I confirm the plan (unless I explicitly said to implement in the same message).
