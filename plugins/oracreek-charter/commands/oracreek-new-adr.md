---
name: oracreek-new-adr
description: Draft an architecture decision record before schema, API, or other durable forks.
---

# New ADR (decision record only)

Decision topic: $ARGUMENTS

## Required reads

- `_oracreek/templates/decision-record.md`
- Existing files in `_oracreek/decisions/` (use next sequential number)
- Related `_oracreek/stories/` and `_oracreek/architecture/` files
- OraCreek Charter rules (plugin or project)

## Steps

1. Determine the next ADR number (e.g. `004-`) from existing files in `_oracreek/decisions/`.
2. Draft using `_oracreek/templates/decision-record.md`:
   - Context, decision, alternatives considered, consequences, follow-up
   - Link affected stories and architecture notes
3. Save as `_oracreek/decisions/NNN-short-title.md` with status **Proposed** or **Accepted**.
4. Update linked stories to reference the new ADR (if stories exist).

## When an ADR is required

Create one when the decision affects:

- Schema or migrations
- Public vs authenticated API boundaries
- Identity / tenancy / customer modeling
- Security-sensitive behavior (auth, permissions, public exposure)
- AI or third-party integrations with lasting product impact
- Inventory, billing, or other domain rules that are easy to rediscover incorrectly

## Stop / ask rules

Ask if:

- The decision reverses an **Accepted** ADR without explicit user approval
- Alternatives were not considered or the simpler option matches documented future-state

## Outputs

Return:

- Path to new ADR file
- Summary of decision and consequences
- Stories/architecture files that should link to it

## Do not

- Do not implement application code in this command.
- Do not mark features **Verified**.
