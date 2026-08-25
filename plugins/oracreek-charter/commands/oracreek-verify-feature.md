---
name: design-verify-feature
description: Run WORKFLOW verification checklist; only path that may mark a feature Verified.
---

# Verify feature (checklist → Verified)

Feature: $ARGUMENTS

## Required reads

- `_designs/WORKFLOW.md` (verification checklist, including "Story file location")
- Matching story under `_designs/stories/` (resolve via the catalog link — stories are grouped in subfolders by status)
- `_designs/feature-catalog.md`
- Design tracker rules (plugin or project)
- Relevant application routes, handlers, UI, schema, and permission checks for this project

## Steps

1. Resolve story from $ARGUMENTS.
2. For each acceptance criterion in the story, verify behavior in **code and routes** — not schema alone.
3. Complete the checklist from `_designs/WORKFLOW.md` (adapt N/A items to the project stack):
   - [ ] Schema / data model (or N/A)
   - [ ] Routes / API
   - [ ] UI
   - [ ] Permissions / auth
   - [ ] Public surface (if public-facing)
   - [ ] Tests / manual validation (document what was checked)
4. If any item fails, keep status **Built - Unverified**, document gaps, and do not mark **Verified**.
5. If all pass:
   - Update story: checkboxes, **Verified** status, **last reviewed** date, current behavior
   - Move the story file (`git mv`) into `_designs/stories/verified/`, and fix its internal relative links plus every cross-link to it
   - Update `_designs/feature-catalog.md` to **Verified** and its link path to the new `verified/` location

## Stop / ask rules

Ask if:

- Acceptance criteria are ambiguous or untestable without user confirmation
- Verification would require production-only config (note manual steps instead)

## Outputs

Return:

- Checklist results (pass/fail per item)
- Final status (**Verified** or **Built - Unverified** with reasons)
- Any catalog/story file edits made

## Do not

- Do not mark **Verified** from schema evidence alone.
- This command is the **only** designated path to promote a feature to **Verified** in the tracker.
