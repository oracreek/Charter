---
name: oracreek-charter
description: >-
  Run the OraCreek Charter workflow (architecture, design docs, status, and
  verification). Use when the project has _oracreek/, or when the user mentions
  feature stories, catalog status, Built - Unverified, or /oracreek-* commands.
---

# OraCreek Charter

## When to use

- Planning, implementing, or verifying a feature in a repo that uses `_oracreek/`
- Updating story status, catalog rows, or ADRs
- User invokes `/oracreek-*` commands or asks about oracreek-charter workflow

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

Never mark **Verified** from schema or file existence alone. Only `/oracreek-verify-feature` (or e2e Phase 6 after **`verify now`**) may promote to **Verified**.

## Story file location

Stories live at `_oracreek/stories/<status-folder>/<feature-id>.md`:

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
| Index | `_oracreek/feature-catalog.md` |
| Stories | `_oracreek/stories/<status>/` |
| Architecture | `_oracreek/architecture/` |
| Decisions | `_oracreek/decisions/` |
| Templates | `_oracreek/templates/` |
| Workflow | `_oracreek/WORKFLOW.md` |

## Command map

| Command | Phase |
|---------|-------|
| `/oracreek-bootstrap` | Scaffold `_oracreek/` in a project |
| `/oracreek-e2e-feature` | Orchestrate plan → Built - Unverified (optional verify) |
| `/oracreek-finish-feature` | Resume existing story |
| `/oracreek-plan-feature` | Explore; no code |
| `/oracreek-new-story` | Create/extend story + catalog |
| `/oracreek-new-adr` | Decision record |
| `/oracreek-start-feature` | Pre-flight; no code until confirmed |
| `/oracreek-implement-feature` | Code → Built - Unverified |
| `/oracreek-sync-after-build` | Sync docs after code |
| `/oracreek-verify-feature` | Checklist → Verified |
| `/oracreek-review-unverified` | Hygiene report |
| `/oracreek-audit-catalog` | Catalog vs code |

## Agent responsibilities

1. Read `_oracreek/README.md` and the relevant story before feature work.
2. Ask when the request conflicts with ADRs, weakens security, or adds avoidable complexity.
3. Update stories and catalog when implementation changes status or behavior.
4. Prefer updating existing docs; archive superseded docs under `_oracreek/archive/`.
5. If `_oracreek/` is missing, suggest `/oracreek-bootstrap` before inventing a parallel doc tree.

## Progressive detail

- Full status governance: project `_oracreek/WORKFLOW.md`
- Bootstrap scaffold source: [../oracreek-bootstrap/SKILL.md](../oracreek-bootstrap/SKILL.md)
