# Security policy

## Reporting a vulnerability

The Compliance-Harnas Configurator is used in audit and compliance contexts, often with references to real client data. Please report security issues **privately** before public disclosure.

**Do not** open a public issue for security-relevant bugs. Instead:

1. Open a **private GitHub Security Advisory** against this repository, or
2. Email the maintainer at the contact address listed on the project's GitHub organisation page.

Include:
- A clear description of the issue.
- Steps to reproduce (minimal example).
- Your assessment of the impact (confidentiality / integrity / availability).
- Any proposed mitigation.

## What qualifies

| In scope | Out of scope |
|---|---|
| XSS via unsanitised user input | Social engineering of the maintainer |
| Integrity-hash bypass | Self-XSS via browser devtools |
| PII-detection bypass with practical exploit | Denial of service via oversized manually-constructed JSON (size-cap already in place) |
| JSON-schema bypass leading to invalid state | Theoretical timing attacks on SHA-256 |
| Prompt-injection patterns that break harnas output | Claims that MIT-license terms are insecure |

## Response timeline

- **Acknowledgement:** within 5 business days.
- **Initial assessment:** within 10 business days.
- **Fix or disclosure-plan:** within 30 business days for rated Medium or higher.

## Known trust boundaries

These are documented limitations, not vulnerabilities:

- `localStorage` is not tamper-resistant. Any JS loaded from the same origin can read/modify it.
- `ACTIVE.json` on disk is read by the `/harnas-check` skill; integrity-hash verification is optional (the skill currently flags tampered files but does not refuse).
- The configurator sends **no data to any server** except the Google Fonts CDN when Privacy mode is off. Self-host the HTML + fonts for full air-gapped operation.
- SHA-256 integrity protects against accidental corruption and naive tampering, not against an attacker who can re-compute and replace the hash.

## Supply chain

This project has **zero runtime dependencies**. There is no `package.json`, `requirements.txt`, or build pipeline that could be compromised. The only external resources are:

- Google Fonts CDN (optional, disableable via Privacy mode).

If you fork and add dependencies, this guarantee no longer holds.
