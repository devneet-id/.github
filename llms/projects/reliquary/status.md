# Reliquary — Status

**Last updated:** 2026-11-15

## State: Active / early

The federated registry works end to end: sealing relics, registering them, mapping forks, and publishing the page.

## Confirmed in place

- `relic` tool: `initiate`, `register`, `upgrade`.
- `nexus` tool: `initiate`, `update`, `inspect`.
- website casts: `build`, `serve`, `watch`, `start`, plus `php exura fetch`.
- `relic.json` + `nexus.json` records; `index.html` reads them live; GitHub Pages deployment.
- A live fork chain: `devneet-id/reliquary` → `AnwarAchilles/reliquary`.
- Registered relics: `devneet-id/build-website`, `devneet-id/how-to-casting`.
- MIT licensed. Requires PHP 8.1+, Composer, Rune `^1.12` (restore needs 1.20+).

## Early-stage / to grow

- **Adoption**: few relics and forks so far — expand the catalog and the federation.
- **Trust tooling**: `nexus inspect` verifies seals; hardening and UX around broken-seal reporting is a natural next step.
- **Docs site**: each reliquary's `index.html` is generated from `src/`; keep it in sync as records grow.

## Files (local working copy)

```
reliquary/
├── relic.json      this owner's relics
├── nexus.json      links to forks
├── relic           the `relic` command (PHP)
├── nexus           the `nexus` command (PHP)
├── cast            the website/build runite
├── exura           helper to fetch Exura into src/
├── index.html      the published page (reads relic.json + nexus.json)
├── src/            page source bundled by `php cast build`
├── .echoes/        Rune metadata
└── vendor/         devneet/rune
```
