---
name: design-bootstrap
description: Scaffold _designs/ (README, WORKFLOW, catalog, templates) into the current project.
---

# Bootstrap design tracker

Project notes: $ARGUMENTS

## Goal

Create a project-local `_designs/` tree so the design-tracker slash commands and rules have a place to work. Do **not** invent product features — only scaffold structure and starter docs.

## Required reads

- This plugin's design-bootstrap skill and scaffold files under `skills/design-bootstrap/scaffold/` (when available)
- Existing `_designs/` if present (never overwrite without asking)
- Project `AGENTS.md` or README for stack hints to customize the verification checklist wording

## Steps

1. If `_designs/` already exists with `README.md` and `WORKFLOW.md`, **stop** and report what is present. Offer to fill only missing pieces (templates, empty catalog) after confirmation.
2. Otherwise create:
   - `_designs/README.md`
   - `_designs/WORKFLOW.md`
   - `_designs/feature-catalog.md` (empty index table)
   - `_designs/templates/feature-story.md`
   - `_designs/templates/decision-record.md`
   - `_designs/templates/architecture-note.md`
   - `_designs/architecture/.gitkeep` (or a short placeholder note)
   - `_designs/decisions/.gitkeep`
   - `_designs/archive/.gitkeep`
   - Do **not** pre-create empty `stories/<status>/` folders
3. Copy content from the design-bootstrap scaffold files when present; otherwise use the templates embedded in the design-bootstrap skill.
4. Adapt verification checklist language lightly to the project stack (e.g. routes file, auth mechanism) only when clearly known from `AGENTS.md` / README — keep the status model unchanged.
5. Optionally add a one-line pointer in the project root `README.md` or `AGENTS.md` to `_designs/` if the user wants (ask first).

## Outputs

Return:

- List of files created or skipped
- How to start: `/design-plan-feature` or `/design-e2e-feature`
- Reminder: stories and ADRs are project-owned; keep iterating the plugin separately

## Do not

- Do not invent product stories or mark anything **Verified**.
- Do not overwrite existing `_designs` content without explicit confirmation.
- Do not copy Ravenwood- or other product-specific ADRs into a new project.
