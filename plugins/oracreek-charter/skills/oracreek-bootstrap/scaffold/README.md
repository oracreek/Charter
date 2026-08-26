# OraCreek Charter

This directory is the **source of truth** for architecture, design docs, status, and validation evidence. Application code lives elsewhere in the repo; Charter records what is planned, built, verified, and why.

## Where to start

| Document | Purpose |
| -------- | --------- |
| [feature-catalog.md](feature-catalog.md) | Index of all features with status and links to stories |
| [stories/](stories/) | One file per durable feature area, grouped in subfolders by status (`stories/<status>/<feature-id>.md`) — see [WORKFLOW.md](WORKFLOW.md#story-file-location) |
| [architecture/](architecture/) | System design by area (data flow, tables, security) |
| [decisions/](decisions/) | ADR-style records for choices that should not be rediscovered |
| [templates/](templates/) | Copy these when adding new stories, architecture notes, or decisions |
| [WORKFLOW.md](WORKFLOW.md) | Status model, verification rules, review cadence, consolidation policy |

## Status model (summary)

| Status | Meaning |
| -------- | --------- |
| **Proposed** | Idea captured, not approved for build |
| **Planned** | Approved direction, not implemented |
| **In Design** | UX / data / API details still being worked out |
| **In Build** | Implementation underway |
| **Built - Unverified** | Code appears to exist; behavior not yet checked against story |
| **Verified** | Documented acceptance criteria match schema, routes, UI, and security as applicable |
| **Deprecated** | Intentionally retired or replaced |

Do **not** mark **Verified** from schema evidence alone. See [WORKFLOW.md](WORKFLOW.md).

## Agent operating guidance

Before implementing or changing a feature:

1. Read this README, the relevant [story](stories/), [architecture note](architecture/), and [decision records](decisions/).
2. Compare the request to documented future-state architecture. If it conflicts, adds avoidable complexity, weakens security, or diverges from best practices, **stop and ask for clarification** before building.
3. During work, set story status to **In Build** or **Built - Unverified** — not **Verified**.
4. After implementation, update code evidence links and the verification checklist in the story.
5. Record major architecture choices as [decisions](decisions/) before implementation (schema, public APIs, identity, security-sensitive forks).
6. Prefer updating existing docs over creating competing ones. Superseded docs go in [archive/](archive/).

## Slash commands (Agent chat)

Type `/oracreek-` in Cursor Agent chat (requires the **oracreek-charter** plugin or equivalent project commands).

| Command | Phase | When to use |
| --------- | ------- | ------------- |
| `/oracreek-bootstrap` | Setup | Scaffold `_oracreek/` into a project |
| `/oracreek-e2e-feature` | Orchestration | **One step:** plan → document → build → sync; stops at **Built - Unverified** unless you say **`verify now`** |
| `/oracreek-finish-feature` | Orchestration | **Resume** an existing story from pre-flight, implement, sync, or verify |
| `/oracreek-plan-feature` | Planning | Explore an idea; clarify UX; propose status — **no code** |
| `/oracreek-new-story` | Planning | Create or extend a story + catalog row from template |
| `/oracreek-new-adr` | Planning | Draft a decision record before schema/API forks |
| `/oracreek-start-feature` | Coding | Pre-flight: read story/ADRs, plan scope, ask on conflicts — **no code until confirmed** |
| `/oracreek-implement-feature` | Coding | Implement to story acceptance criteria; end at **Built - Unverified** |
| `/oracreek-sync-after-build` | Documentation | Update story, catalog, architecture after code lands |
| `/oracreek-verify-feature` | Documentation | Run WORKFLOW checklist; only path to mark **Verified** |
| `/oracreek-review-unverified` | Hygiene | Report on Built - Unverified / In Design / stale Planned |
| `/oracreek-audit-catalog` | Hygiene | Compare catalog status to routes, UI, and schema |

**Recommended one-step flow:** New feature → `/oracreek-e2e-feature` (reply at each gate) → **`verify now`** when ready. Existing story → `/oracreek-finish-feature`.

Granular flow: `/oracreek-plan-feature` → `/oracreek-start-feature` → `/oracreek-implement-feature` → `/oracreek-sync-after-build` → `/oracreek-verify-feature`.

## Human workflow (short)

1. **Start feature** — Confirm story status and open questions.
2. **Build** — Update story as behavior changes; add decision records when needed.
3. **Verify** — Check routes, UI, schema, permissions; then mark **Verified**.
4. **Review** — Periodically audit **Built - Unverified**, stale **Planned**, and **In Design** items.
5. **Backfill** — If code changed without a story, add or update a story so the tracker stays accurate.

## Archive

[archive/](archive/) holds superseded documents. They are history only — not source of truth.
