# `.github` — runite-app (gallery tooling)

**Path:** `runite-app/`

A **Rune runite** (an app built on Rune) whose casts manage the `design/` gallery. This is DEVNEET dogfooding its own foundation: Rune maintaining the org's own content.

## Layout

```
runite-app/
├── cast                    the runite (entry file)
├── composer.json           requires devneet/rune ^1.12
└── vendor/devneet/rune     the Rune framework
```

## What the `cast` file does

- **Invocation:** awakens Aether, Whisper, Weaver, Chanter, **and Forger** (Forger was added specifically for file/folder work).
- **Helpers** (plain functions over Forger): list collections, collect+dedupe image assets (prefer SVG), group by topic, titleize names (`v2-logo-1` → "V2 Logo 1"), and engrave Markdown for both a contributor README and the gallery index.
- **Registered casts:**

| Command | Purpose |
|---|---|
| `php cast design` | Scan every collection under `design/`, **generate `README.md` for any contributor that lacks one**, then **rebuild `design/README.md`** (the index). |
| `php cast design --check` | Dry run — report what would be created/updated/rebuilt; write nothing. |
| `php cast design --force` | Also regenerate contributor READMEs that already exist. |
| `php cast design-scan` | Read-only: list each collection, its asset count, and whether it has a README. |
| `php cast design-user --name=<username>` | (Re)generate a single contributor's README. |

## Behaviour details

- A "collection" is any folder under `design/` except `official` (configurable via `$RESERVED`).
- Contributor README = a gallery grouped by topic folder, 3 images per table row, captions titleized.
- The index keeps the curated intro + live last-updated badge + Contributing note, with an auto-generated Collections table (concept counts).
- `php cast design` only **creates missing** contributor READMEs (unless `--force`), but **always rebuilds** the index. This is the intended "map everything to `design/README.md`" flow.

## Design decisions captured

- The casts follow Rune idioms: `Chanter::cast(arg, execute, echo)`, `Chanter::spell()` for options, `Whisper::echo()` with style tokens, `Forger::scan()/item()` for files.
- The app was syntax-checked (`php -l`) clean.
- Delivery note: because `.github` is write-protected from the collaborating AI, this `cast` file is produced in scratch and moved into `.github/runite-app/` by a human.

## For an AI extending this

- To add a new gallery operation, register another `Chanter::cast(...)` in the incantation section and reuse the existing helper functions.
- Keep `$RESERVED` in sync with any non-collection folders added under `design/`.
- If a contributor adds loose images directly in their folder (not in a topic subfolder), they are grouped under an "Assets" heading.
