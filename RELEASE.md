# Releases

This project uses [semantic versioning](https://semver.org/) and [GitHub Flow](https://docs.github.com/en/get-started/using-github/github-flow).

`main` is the product. There is no long-lived published branch. A **release** is a git tag plus a GitHub Release.

## Version source of truth

Keep these in sync for a release:

- `plugins/design-tracker/.cursor-plugin/plugin.json` → `version`
- `.cursor-plugin/marketplace.json` → `metadata.version`
- Git tag `vX.Y.Z` (leading `v`)
- [CHANGELOG.md](CHANGELOG.md)

## Who can publish

Only maintainers listed in [MAINTAINERS.md](MAINTAINERS.md) create tags and GitHub Releases.

## How to cut a release

1. Ensure `main` is green (CI passes) and the changelog **Unreleased** section describes the work.
2. Bump the two version fields above.
3. Move **Unreleased** notes into a new `## X.Y.Z` section dated today.
4. Open a PR titled `chore: release vX.Y.Z`.
5. After merge, tag the merge commit:

   ```bash
   git checkout main
   git pull
   git tag -a vX.Y.Z -m "vX.Y.Z"
   git push origin vX.Y.Z
   ```

6. Create a **GitHub Release** from that tag (can be a draft first). Paste the changelog section.

Do not force-push tags. Do not rewrite history to “fix” a release; cut a patch instead.

## Cursor Marketplace

Listing this plugin on the Cursor Marketplace is a **separate step** after the GitHub repository is public. Do not submit until a maintainer explicitly asks. When that happens, the tagged commit is what we submit, not an untagged `main` experiment.

## Pre-releases

Optional tags such as `v0.2.0-beta.1` are allowed for testers. They are not Marketplace candidates.
