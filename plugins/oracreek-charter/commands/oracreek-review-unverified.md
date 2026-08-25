---
name: oracreek-review-unverified
description: Report on Built - Unverified, In Design, and stale Planned items. Report only by default.
---

# Review unverified & in-design items (report only)

Scope: $ARGUMENTS (optional — filter by module or feature; default: entire catalog)

## Required reads

- `_oracreek/feature-catalog.md`
- `_oracreek/WORKFLOW.md`
- All `_oracreek/stories/` with status **Built - Unverified**, **In Design**, or stale **Planned**
- Oracreek Charter rules (plugin or project)

## Steps

1. Scan `_oracreek/feature-catalog.md` for:
   - **Built - Unverified**
   - **In Design**
   - **Planned** (note last reviewed dates in linked stories if present)
2. For each item, briefly compare story claims to code — spot obvious mismatches.
3. Recommend per item:
   - Run `/oracreek-verify-feature` now
   - Update story (scope drift)
   - Downgrade or clarify status
   - Archive or consolidate docs
4. Prioritize a short ordered list for the next planning session.

## Stop / ask rules

This command is **report-only** unless I explicitly ask you to edit files in the same message.

## Outputs

Return a table or list:

- Feature ID | Story | Status | Issue | Recommended action

## Do not

- Do not edit files unless I explicitly request updates in this message.
- Do not mark **Verified** without running `/oracreek-verify-feature`.
