---
name: design-audit-catalog
description: Compare feature-catalog status to routes, UI, and schema. Report discrepancies.
---

# Audit catalog vs codebase

Scope: $ARGUMENTS (optional module or feature filter; default: full catalog)

## Required reads

- `_designs/feature-catalog.md`
- `_designs/stories/` (linked from catalog)
- Project entrypoints for routes/API, schema, and UI (discover from repo layout / `AGENTS.md`)
- `_designs/WORKFLOW.md`
- Design tracker rules (plugin or project)

## Steps

1. For each catalog row (or filtered subset), compare **documented status** to **observed implementation**:
   - Routes/APIs exist and match public vs protected expectations
   - Schema/data model supports claimed behavior (if applicable)
   - UI exists where story claims user-facing surfaces
2. Flag discrepancies (e.g. **Verified** without evidence, **Planned** with substantial code, missing routes claimed as built).
3. Note stale code evidence links in stories.
4. Recommend: status correction, story update, or `/design-verify-feature` / `/design-sync-after-build`.

## Stop / ask rules

Report-only unless I ask for doc edits in the same message.

Ask when UX intent is unclear and affects status judgment.

## Outputs

Return:

- Discrepancy list (catalog ID, claimed status, actual finding, suggested fix)
- Summary count by severity
- Suggested command for each fix (`/design-sync-after-build`, `/design-verify-feature`, `/design-new-story`)

## Do not

- Do not mark **Verified** in an audit report without full checklist pass.
