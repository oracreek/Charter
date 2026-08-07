# Feature Story Template

Copy to `stories/<status-folder>/<feature-id>.md` and fill in all sections, where `<status-folder>` matches the **Status** value below (see [../WORKFLOW.md](../WORKFLOW.md#story-file-location)).

---

```markdown
# <Feature ID>: <Title>

| Field | Value |
|-------|-------|
| **Module** | (e.g. Public / Admin / Platform / System) |
| **Status** | Proposed / Planned / In Design / In Build / Built - Unverified / Verified / Deprecated |
| **Last reviewed** | YYYY-MM-DD |
| **Catalog ref** | e.g. 1.1 |

## User story

As a \<role\>, I want \<capability\>, so that \<benefit\>.

## Business purpose

One short paragraph on why this matters.

## Current behavior

What the codebase does today. Link evidence.

## Planned behavior

Target future state. Align with architecture notes and decisions.

## Known gaps

Bulleted list of missing pieces.

## Acceptance criteria

```gherkin
Scenario: ...
  Given ...
  When ...
  Then ...
```

## Code evidence

| Area | Path / symbol |
|------|----------------|
| Routes / API | `...` |
| Handlers / services | `...` |
| UI | `...` |
| Schema / data | `...` |

## Data model

- Existing: ...
- Planned: ...

## UX notes

Screens, flows, copy, edge cases.

## Open questions

- ...

## Verification checklist

- [ ] Schema / data model
- [ ] Routes / API
- [ ] UI
- [ ] Permissions / auth
- [ ] Public surface (if applicable)
- [ ] Tests / manual validation

## Related docs

- Architecture: [../../architecture/...](../../architecture/...)
- Decisions: [../../decisions/...](../../decisions/...)
```
