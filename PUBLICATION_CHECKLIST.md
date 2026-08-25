# Publication checklist

Human decision required: this work does **not** change GitHub visibility and does **not** submit to the Cursor Marketplace.

Reply **APPROVE PUBLICATION** when you want the repository made public (Settings → Change repository visibility). Marketplace submit is a later, separate approval.

## Done on this branch

- [x] Working-tree secret/PII grep: no tokens, private keys, or `.env` files found
- [x] History is three documentation/plugin commits; no rewrite planned
- [x] Snyk org id removed from tracked editor settings (`.vscode/` is gitignored)
- [x] Cursor template starters removed from the product surface
- [x] LICENSE (MIT), CONTRIBUTING, CODE_OF_CONDUCT, SECURITY, issue/PR templates
- [x] RELEASE.md documents tags on `main` (no published branch)
- [x] CI workflow added (`scripts/validate-template.mjs`)
- [x] README describes local install; Marketplace is explicitly “later”

## Before you click “public” on GitHub

- [ ] Read the PR diff yourself (especially README, SECURITY, and plugin manifests)
- [ ] Confirm MIT and the Oracreek / @jesgorsuch attribution are what you want
- [ ] Confirm `plugins@oracreek.com` is an inbox you monitor
- [ ] CI is green on this branch
- [ ] You are ready for the GitHub profile and clone URL to be world-visible

## After the repo is public (not this PR)

- [ ] Protect `main` (PR required, CI required)
- [ ] Tag `v0.1.0` and create a GitHub Release when you want a frozen snapshot
- [ ] Then, separately, submit to Cursor Marketplace from that tag

## History

No secrets were found in the current tree. Keep existing `main` history. Do not run `git filter-repo` or create an orphan branch unless a later scan finds a real secret.
