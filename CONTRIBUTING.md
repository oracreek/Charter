# Contributing

Thanks for helping improve Design Tracker. This is a **public product repository**: `main` should always be presentable.

## Workflow

We use [GitHub Flow](https://docs.github.com/en/get-started/using-github/github-flow):

1. Branch from `main` with a short name (`feat/…`, `fix/…`, `docs/…`, `chore/…`).
2. Open a pull request. Keep it focused.
3. Wait for CI (`node scripts/validate-template.mjs`) to pass.
4. Merge only when you would be comfortable tagging that commit as the next release candidate.

Do not maintain a long-lived `published` branch. Released versions are **git tags** (`v0.1.0`) that match the plugin manifest. See [RELEASE.md](RELEASE.md).

## What belongs in this repo

- The Design Tracker plugin under `plugins/design-tracker/`
- Marketplace manifest listing **only** that plugin
- Docs, license, and CI for a public GitHub project

Do not add:

- Secrets, `.env` files, API keys, or personal machine paths
- Screenshots or examples that show private data
- Unmodified Cursor template starter plugins
- Unpublished experiments that are not ready for `main`

## Commit messages

Prefer [Conventional Commits](https://www.conventionalcommits.org/):

- `feat:` new capability
- `fix:` bug fix
- `docs:` documentation only
- `chore:` tooling, CI, hygiene
- `ci:` workflow changes

## Checks before you open a PR

- [ ] `node scripts/validate-template.mjs` passes
- [ ] No secrets, tokens, or personal data in the diff
- [ ] Plugin `version` is unchanged unless this PR is intentionally a release
- [ ] Docs match the behavior you changed

## Code of Conduct

Participation is covered by [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
