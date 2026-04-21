# Contributing

Thanks for considering a contribution. This project is part of the [SAAF Project](https://saafproject.com/) ecosystem — a shared framework for AI audit agents built by and for auditors.

## What contributions are welcome

| Type | Scope |
|---|---|
| **Control refinements** | Better wording, updated framework references, new cross-references. |
| **Framework mappings** | New regulatory frameworks (ISO 42001, NIST AI RMF, BIO 2.0, national equivalents of CBW/NIS2). |
| **AI Act triggers** | New rule-based triggers for obligation activation. |
| **Hook templates** | Runnable `settings.json` hook implementations for Claude Code or other AI-coding harnesses. |
| **Example configs** | Anonymised, representative configurations for common audit use-cases. |
| **Translations** | UI and documentation in EN / DE / FR / ES. |
| **Bug fixes** | Schema-validation gaps, export-rendering issues, accessibility. |

## What is out of scope

- Adding dependencies (the tool is deliberately single-file, no build step).
- Proprietary or paywalled framework data — only openly licensed sources.
- Organisation-specific configs (keep those in your own private fork).
- Anything that cannot be explained in a 2-sentence AI-Act-trigger description.

## How to submit

1. **Open an issue first** — especially for new controls, new frameworks, or mapping changes. These need community discussion before implementation.
2. Use the appropriate template in `.github/ISSUE_TEMPLATE/`.
3. For code contributions, fork → branch (`feat/…` or `fix/…`) → PR against `main`.
4. Keep PRs small and focused. One concept per PR.

## Design principles (non-negotiable)

1. **Single file** — the configurator is one HTML file. Don't introduce a build step.
2. **No backend** — everything runs in the browser. All state in `localStorage` + JSON files.
3. **No mandatory network calls** — Privacy mode must work fully offline (except fonts, which degrade gracefully).
4. **Data provenance** — every piece of framework data must have an attribution in `NOTICE.md`.
5. **Language** — Dutch for the UI (initial audience is NL auditors), English for code identifiers, variable names, commit messages, documentation.
6. **Controls are immutable codes** — never rename `G.01`, `D.04`, etc. Add new codes if needed, never repurpose existing ones.

## Adding a new control

1. Open issue with `new-control` template.
2. In `src/Compliance-Harnas-Configurator.html`:
   - Add entry to `harnas` object with `n`, `fw`, `d` fields.
   - Add entry to `HARNAS_LAYERS[letter].codes`.
   - Add entry to `harnasSteering` with `tier` + `claudeMd` / `hook` if applicable.
   - Add entry to `strideMap` (array of one or more STRIDE categories).
3. Update `cbwMap` / `digidMap` `maps` arrays if the new control is mitigated by a CBW or DigiD norm.
4. Update `schemas/harnas-config.schema.json` if the control ID pattern changes.
5. Document rationale in `docs/en/controls/{code}.md`.

## Adding a new framework

1. Open issue with `framework-mapping` template.
2. Discuss licensing and attribution first.
3. Add `{framework}Map` constant.
4. Add `{framework}Reverse` reverse-index.
5. Extend UI: chip filter + controls-tab rendering.
6. Add attribution to `NOTICE.md`.

## Commit message format

Conventional-commits-lite:

```
<type>: <summary>

<optional body>
```

Types: `feat`, `fix`, `docs`, `refactor`, `chore`, `test`, `style`.

## Code of conduct

See [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md). Short version: assume good faith, write like you'll meet the reader in person.

## License of contributions

By contributing you agree that your contributions are licensed under the MIT License (see [`LICENSE`](LICENSE)).
