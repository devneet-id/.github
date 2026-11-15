# `.github` — Design Gallery

**Path:** `design/`

A community gallery of DEVNEET's visual work: official brand assets plus a folder per contributor.

## Layout

```
design/
├── official/            canonical brand assets (team-maintained, e.g. logo.svg)
├── <username>/          one folder per contributor
│   ├── <topic>/         e.g. main/, rune/ — groups of asset files (svg/png/…)
│   └── README.md        a generated gallery of that contributor's assets
└── README.md            the gallery index (generated)
```

Observed contributors: `anwarachilles` (topic `main`: logos, wordmarks, compact wordmarks) and `mreazenith` (topic `rune`: banners, cards, logos/titles in png+svg).

## Conventions

- A "collection" = any folder under `design/` **except `official`** (reserved).
- Asset path shape: `<username>/<topic>/<file>` (e.g. `anwarachilles/main/v2-logo-1.svg`).
- Image files: `svg png jpg jpeg gif webp`; **SVG preferred** when a name exists as both svg and png (the generator dedupes to the svg).

## The index README (`design/README.md`)

Current form (curated): a title + short intro, a live **last-updated** badge (scoped to `design/`), a **Collections** table (each collection → its README, with a concept count), and a short **Contributing** note:

> Open the `design/` folder, then upload your own folder — that's it.

## Contributing model

- Contributors without write access: use GitHub's web "Upload files" on `design/` → GitHub **auto-forks** and opens a PR (no manual fork needed).
- Trusted/core contributors with write access to `.github`: can commit directly (but note branch protection, if enabled, forces PRs).
- Because permissions are per-repo, giving someone direct-upload rights to `design/` means write access to all of `.github` — a reason the team considered (and kept) separation of concerns.

## Generation

The index and each contributor README are **generated** by the `runite-app` casts — see [runite-app.md](runite-app.md). After someone uploads assets, running `php cast design` regenerates the missing READMEs and rebuilds the index.
