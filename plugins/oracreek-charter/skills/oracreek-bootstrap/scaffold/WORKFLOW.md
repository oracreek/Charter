# Oracreek Charter — Workflow & Governance

## Status definitions

### Proposed
Captured idea. No approval to build. May lack acceptance criteria.

### Planned
Approved direction. Acceptance criteria and architecture direction agreed at a high level. No implementation yet.

### In Design
Details still being refined: UX flows, schema shape, API contracts, permissions. Safe to prototype; not ready for **Verified**.

### In Build
Active implementation. Story should list affected files and any deviations from planned behavior.

### Built - Unverified
Implementation exists in the codebase (or substantial partial exists), but no one has completed the verification checklist against the story. Common after merges or when status was inferred from schema only.

### Verified
All of the following are true:

- Acceptance criteria match observed behavior (routes, UI, or documented manual test).
- Schema / data model matches the story (if applicable).
- Permission and public/private API boundaries match the story.
- Code evidence links in the story are current.

### Deprecated
Feature or doc intentionally retired. Link to replacement story or decision.

---

## Verification checklist

Use this in every story before marking **Verified**. Adapt path names to the project stack:

- [ ] **Schema / data model** — Tables, collections, or types exist and match documented model (or N/A).
- [ ] **Routes / API** — Endpoints behave as documented.
- [ ] **UI** — User-facing pages or surfaces render expected behavior.
- [ ] **Permissions / auth** — Access control enforced where required.
- [ ] **Public surface** — If public-facing, intentional exposure and scoping documented.
- [ ] **Tests / manual** — Automated test or explicit manual validation steps recorded.

---

## Story file location

Stories are grouped into subfolders by their **current** status:

| Status | Folder |
|--------|--------|
| Proposed | `_oracreek/stories/proposed/` |
| Planned | `_oracreek/stories/planned/` |
| In Design | `_oracreek/stories/in-design/` |
| In Build | `_oracreek/stories/in-build/` |
| Built - Unverified | `_oracreek/stories/built-unverified/` |
| Verified | `_oracreek/stories/verified/` |
| Deprecated | `_oracreek/stories/deprecated/` |

A story's canonical path is `_oracreek/stories/<status-folder>/<feature-id>.md`. Only folders with at least one story currently exist — do not pre-create empty ones.

**Whenever a story's Status field changes, move the file (`git mv`) into the matching folder in the same change**, and update every link that points to it:

- The story's own link in [feature-catalog.md](feature-catalog.md)
- Cross-links from other stories, [architecture/](architecture/) notes, and [decisions/](decisions/) records
- Relative links *within* the moved story to `../architecture/`, `../decisions/`, or other stories must be adjusted for the new folder depth

---

## Accuracy workflow

1. **New work** starts with a story update or new story from [templates/feature-story.md](templates/feature-story.md), saved directly into the status folder matching its initial status (see [Story file location](#story-file-location)).
2. **Architecture choices** get a [decision record](templates/decision-record.md) before implementation when they affect schema, security, or long-term maintenance.
3. **During build** — Status **In Build** → **Built - Unverified** when code lands; move the file and fix links per [Story file location](#story-file-location).
4. **After build** — Update code evidence; run verification checklist.
5. **Verified** only when checklist passes; move the file into `verified/` and fix links.
6. **Consolidation** — One canonical story per feature. Archive superseded docs; update [feature-catalog.md](feature-catalog.md) index.

---

## Review cadence

| When | Action |
| ------ | -------- |
| Before starting a feature | Read story + architecture + decisions; resolve open questions |
| Before merge / deploy | Update story evidence and status |
| Monthly or pre-planning | Review all **Built - Unverified**, **In Design**, stale **Planned** |
| After unplanned code change | Backfill story or decision so tracker matches repo |

---

## Consolidation policy

- **Canonical catalog:** [_oracreek/feature-catalog.md](feature-catalog.md)
- **Canonical stories:** `_oracreek/stories/<status-folder>/<feature-id>.md` — see [Story file location](#story-file-location)
- When merging provisional docs: correct statuses against code, link to stories, move old file to `archive/` with a header noting supersession date.
- Root `README.md` / `AGENTS.md` should not contradict verified features; add a pointer to `_oracreek/` when updating deployment docs.

---

## Agent responsibilities

Agents working in this repo must:

1. Read [_oracreek/README.md](README.md) and the relevant story before feature work.
2. Ask clarifying questions when the request is not ideal for future-state architecture, security, or maintainability.
3. Update stories and catalog when implementation changes status or behavior.
4. Never mark **Verified** without completing the verification checklist from code inspection.
5. Add decision records for significant forks (e.g. new tables, public endpoints, identity rules).
6. Avoid over-modeling when a simpler documented approach suffices.
