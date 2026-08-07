---
name: design-new-story
description: Create or extend a feature story and catalog row from the feature-story template.
---

# New story (create or extend)

Feature description: $ARGUMENTS

## Required reads

- `_designs/templates/feature-story.md`
- `_designs/feature-catalog.md`
- `_designs/WORKFLOW.md`
- Design tracker rules (plugin or project)

## Steps

1. Check whether a story already exists in `_designs/stories/`. If yes, extend it; if no, create a new file.
2. Use structure from `_designs/templates/feature-story.md`:
   - Stable feature ID, title, module, status, last reviewed date
   - User story, business purpose, current/planned behavior, gaps
   - Gherkin acceptance criteria
   - Code evidence table (project paths)
   - Data model, UX notes, open questions, verification checklist
   - Links to architecture notes and ADRs
3. Assign filename: `_designs/stories/<status-folder>/<kebab-slug>.md`, where `<status-folder>` matches the initial status chosen in step 5 (see `_designs/WORKFLOW.md` "Story file location").
4. Add or update a row in `_designs/feature-catalog.md` with correct catalog ID and link.
5. Set initial status: **Proposed**, **Planned**, or **In Design** (not **Verified**).

## Stop / ask rules

Ask before creating the story if:

- The feature duplicates an existing catalog row
- Architecture is unset and an ADR should come first (schema, public API, identity, security-sensitive forks)
- Scope is unclear (roles, public vs protected)

## Outputs

Return:

- Path to created/updated story file
- Catalog row added/changed
- Recommended follow-up: `/design-new-adr` or `/design-plan-feature`

## Do not

- Do not implement application code unless I explicitly ask in the same message.
- Do not mark **Verified**.
