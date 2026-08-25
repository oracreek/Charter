---
name: oracreek-bootstrap
description: Scaffold _oracreek/ (README, WORKFLOW, catalog, templates) into the current project.
---

# Bootstrap Oracreek Charter

Project notes: $ARGUMENTS

## Goal

Create a project-local `_oracreek/` tree so the oracreek-charter slash commands and rules have a place to work. Do **not** invent product features — only scaffold structure and starter docs.

## Required reads

- This plugin's oracreek-bootstrap skill and scaffold files under `skills/oracreek-bootstrap/scaffold/` (when available)
- Existing `_oracreek/` if present (never overwrite without asking)
- Project `AGENTS.md` or README for stack hints to customize the verification checklist wording

## Steps

1. If `_oracreek/` already exists with `README.md` and `WORKFLOW.md`, **stop** and report what is present. Offer to fill only missing pieces (templates, empty catalog) after confirmation.
2. Otherwise create:
   - `_oracreek/README.md`
   - `_oracreek/WORKFLOW.md`
   - `_oracreek/feature-catalog.md` (empty index table)
   - `_oracreek/templates/feature-story.md`
   - `_oracreek/templates/decision-record.md`
   - `_oracreek/templates/architecture-note.md`
   - `_oracreek/architecture/.gitkeep` (or a short placeholder note)
   - `_oracreek/decisions/.gitkeep`
   - `_oracreek/archive/.gitkeep`
   - Do **not** pre-create empty `stories/<status>/` folders
3. Copy content from the oracreek-bootstrap scaffold files when present; otherwise use the templates embedded in the oracreek-bootstrap skill.
4. Adapt verification checklist language lightly to the project stack (e.g. routes file, auth mechanism) only when clearly known from `AGENTS.md` / README — keep the status model unchanged.
5. Optionally add a one-line pointer in the project root `README.md` or `AGENTS.md` to `_oracreek/` if the user wants (ask first).

## Outputs

Return:

- List of files created or skipped
- How to start: `/oracreek-plan-feature` or `/oracreek-e2e-feature`
- Reminder: stories and ADRs are project-owned; keep iterating the plugin separately

## Do not

- Do not invent product stories or mark anything **Verified**.
- Do not overwrite existing `_oracreek` content without explicit confirmation.
- Do not copy Ravenwood- or other product-specific ADRs into a new project.
