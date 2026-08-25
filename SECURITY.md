# Security policy

## Supported versions

Security fixes are applied to the latest tagged release and to `main`.

| Version | Supported |
| --- | --- |
| `main` | Yes |
| Latest `v0.x` tag | Yes |
| Older tags | No |

## Reporting a vulnerability

Please **do not** open a public issue for security reports.

Prefer **GitHub private vulnerability reporting** on this repository
(Security → Report a vulnerability). If that is unavailable, email the
marketplace owner address in `.cursor-plugin/marketplace.json`.

Include:

- A description of the issue
- Steps to reproduce
- Impact (for example: leaked secrets in a generated file, unsafe hook, prompt injection in a command)

You should receive an acknowledgement within 7 days. We will tell you whether we accepted the report and when a fix is expected.

If the report is in scope, we will:

1. Confirm and reproduce privately
2. Prepare a fix on a private branch when needed
3. Tag a patched release
4. Credit you in the release notes if you want that
