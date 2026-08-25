# Architecture Note Template

Copy to `architecture/<area>.md` and fill in all sections.

---

```markdown
# Architecture: <Area Name>

| Field | Value |
|-------|-------|
| **Last updated** | YYYY-MM-DD |
| **Status** | Draft / Active / Superseded |
| **Related stories** | links |

## Problem

What system problem this area solves.

## Current implementation

Summary of what exists in code/schema today, with file references.

## Proposed model

Entities and relationships (keep minimal — prefer simplicity).

## Data flow

Describe request/response or user flow. Use a diagram if helpful.

```mermaid
flowchart LR
  Client --> API
  API --> Store
```

## Affected files

- `...`

## Security & access

Public vs authenticated routes, roles, permission model.

## Migration / backfill

Migrations, seed data, rollout notes.

## Operational concerns

Caching, concurrency, audit, ops workflows.

## Open questions

- ...
```
