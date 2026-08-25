---
name: design-tracker
description: >-
  Run the design-tracker feature workflow (status model, story folders, ADRs,
  verification). Use when the project has _designs/, or when the user mentions
  feature stories, catalog status, Built - Unverified, or design slash commands.
---

# Design tracker

## When to use

- Planning, implementing, or verifying a feature in a repo that uses `_designs/`
- Updating story status, catalog rows, or ADRs
- User invokes `/design-*` commands or asks about design-tracker workflow

## Status model

| Status | Meaning |
|--------|---------|
| **Proposed** | Idea captured, not approved for build |
| **Planned** | Approved direction, not implemented |
| **In Design** | UX / data / API details still being worked out |
| **In Build** | Implementation underway |
| **Built - Unverified** | Code appears to exist; behavior not yet checked against story |
| **Verified** | Acceptance criteria match routes, UI, permissions, and schema as applicable |
| **Deprecated** | Intentionally retired or replaced |

Never mark **Verified** from schema or file existence alone. Only `/design-verify-feature` (or e2e Phase 6 after **`verify now`**) may promote to **Verified**.

## Story file location

Stories live at `_designs/stories/<status-folder>/<feature-id>.md`:

| Status | Folder |
|--------|--------|
| Proposed | `proposed/` |
| Planned | `planned/` |
| In Design | `in-design/` |
| In Build | `in-build/` |
| Built - Unverified | `built-unverified/` |
| Verified | `verified/` |
| Deprecated | `deprecated/` |

On every status change: `git mv` into the matching folder and fix catalog + cross-links + relative links inside the story.

## Canonical locations

| What | Where |
|------|--------|
| Index | `_designs/feature-catalog.md` |
| Stories | `_designs/stories/<status>/` |
| Architecture | `_designs/architecture/` |
| Decisions | `_designs/decisions/` |
| Templates | `_designs/templates/` |
| Workflow | `_designs/WORKFLOW.md` |

## Command map

| Command | Phase |
|---------|-------|
| `/design-bootstrap` | Scaffold `_designs/` in a project |
| `/design-e2e-feature` | Orchestrate plan → Built - Unverified (optional verify) |
| `/design-finish-feature` | Resume existing story |
| `/design-plan-feature` | Explore; no code |
| `/design-new-story` | Create/extend story + catalog |
| `/design-new-adr` | Decision record |
| `/design-start-feature` | Pre-flight; no code until confirmed |
| `/design-implement-feature` | Code → Built - Unverified |
| `/design-sync-after-build` | Sync docs after code |
| `/design-verify-feature` | Checklist → Verified |
| `/design-review-unverified` | Hygiene report |
| `/design-audit-catalog` | Catalog vs code |

## Agent responsibilities

1. Read `_designs/README.md` and the relevant story before feature work.
2. Ask when the request conflicts with ADRs, weakens security, or adds avoidable complexity.
3. Update stories and catalog when implementation changes status or behavior.
4. Prefer updating existing docs; archive superseded docs under `_designs/archive/`.
5. If `_designs/` is missing, suggest `/design-bootstrap` before inventing a parallel doc tree.

## Progressive detail

- Full status governance: project `_designs/WORKFLOW.md`
- Bootstrap scaffold source: [../design-bootstrap/SKILL.md](../design-bootstrap/SKILL.md)
