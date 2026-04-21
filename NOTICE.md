# Third-party notices

The Compliance-Harnas Configurator includes data, fonts, and concepts from third parties. Attributions below.

## Control framework data

### CBW (NIS2) Control Framework — 26 beheersmaatregelen
- **Source:** ADR & NOREA, *Cbw (NIS2) Control Framework* (2025)
- **License:** Creative Commons Attribution 4.0 International (CC-BY 4.0)
- **License text:** https://creativecommons.org/licenses/by/4.0/
- **What is used:** The 26 official BM identifiers (1.1 – 17.1), titles, themes, and Cbw/Cbb article references. Embedded in `src/Compliance-Harnas-Configurator.html` under the constant `cbwMap`.
- **What is NOT from this source:** the mapping of each BM onto the 35 harnas-controls — those are our own interpretation (best-effort; verify per audit).

### DigiD NOREA 3.0 normenkader — partial mapping
- **Source:** Norm based on NOREA DigiD Assessment Template 2025.
- **What is used:** Selected norm identifiers (B-01, B-03, etc.) and titles, where they intersect with AI-runtime concerns. Embedded as `digidMap`.
- **What is NOT from this source:** the mapping onto harnas-controls — our interpretation.

## Fonts (optional, loaded from Google Fonts CDN by default; replaceable via Privacy mode)

| Font | License |
|---|---|
| [Fraunces](https://fonts.google.com/specimen/Fraunces) | SIL Open Font License 1.1 |
| [Inter Tight](https://fonts.google.com/specimen/Inter+Tight) | SIL Open Font License 1.1 |
| [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) | SIL Open Font License 1.1 |

If you self-host the fonts (recommended for AVG-compliant operation — Google Fonts CDN leaks IP address), include copies of each font's LICENSE file alongside the font files.

The configurator's Privacy mode disables Google Fonts and falls back to platform-native fonts (Georgia / Segoe UI / Consolas).

## Compliance frameworks referenced

The configurator cites but does not reproduce the following; users must consult the original source material for interpretation:
- EU General Data Protection Regulation (AVG / GDPR) — Regulation (EU) 2016/679
- EU Digital Operational Resilience Act (DORA) — Regulation (EU) 2022/2554
- EU AI Act — Regulation (EU) 2024/1689
- NL Cyberbeveiligingswet (Cbw) & Cyberbeveiligingsbesluit (Cbb) — implementing NIS2 (Directive (EU) 2022/2555)

## STRIDE threat model

STRIDE is a threat modeling methodology originally developed at Microsoft (Kohnfelder & Garg, 1999; popularised by Howard & LeBlanc). The six categories (Spoofing / Tampering / Repudiation / Information disclosure / Denial of service / Elevation of privilege) are in the public domain.

## Disclaimer

All framework mappings in this tool are best-effort interpretations by the authors. They are not legal advice. For formal audits or compliance attestation, consult the original normative documents and qualified legal/compliance counsel.
