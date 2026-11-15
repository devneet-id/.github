# Rune — Lifecycle: Awakening, Liberation, Artefact, Sentinel

## 1. Awakening — from the void

`Rune\Ethereal::awakening()` turns an empty `cast` into a runite. It loads the built-in starter from `@bindrune/awakening/cast.php`. This is "Act 0 — Awaken From The Void": the simplest possible entry.

```php
require_once __DIR__ . '/vendor/autoload.php';
Rune\Ethereal::awakening();
```

Progression taught in the lore: **Act 0** (the void) → **Act 1** (understanding the flow: invocation + incantation, as in [cli.md](cli.md)).

## 2. Liberation — make your own runes

`Rune\Ethereal::liberation()` opens the gate to create runes beside the origin ten.

```php
require_once __DIR__ . '/vendor/autoload.php';
Rune\Ethereal::liberation();
```

- Your runes live in `@liberations/` of the working folder.
- A PSR-4 loader for `Rune\\` is appended (registered after the origin loader), so **a liberation rune never replaces an origin rune**.
- In liberation mode the version footer's `sum` also counts your liberation runes.

Shape them with Sentinel:

```bash
php cast sentinel --create-rune=ledger   # scaffold Rune\Ledger
php cast sentinel --phantasm-fix=Ledger  # repair/raise its Phantasm
php cast sentinel --invoke=Ledger        # engrave it into the runite
```

## 3. Artefact / Runite — seal and share

An **Artefact** seals a runite (its code, its echoes, and its shards) into a single `.rune` file — like building a Docker image from a Dockerfile.

```bash
php cast artefact --invoke                 # cast → cast.rune (the snapshot)
php cast artefact --revoke=<file>.rune     # bring an artefact back to life elsewhere
```

A sealed runite can be restored in another place and runs as it was sealed. The `.rune` is the unit that **Reliquary** distributes (see [../reliquary/README.md](../reliquary/README.md)). Restoring a relic into a runite needs **Rune 1.20+**:

```bash
php cast reliquary --runite-relic                      # seal: cast → cast.rune
php cast reliquary --relic-runite=<vendor>/<repo>       # restore from a reliquary
```

The **Crafter** rune is the builder behind sealing (item → seed → shard → spark → one file); **Keeper** supplies the echoes/shards from `.echoes/`.

## 4. Sentinel — guard the runite

Sentinel engraves or removes runes in a runite, keeping it consistent:

```bash
php cast sentinel --invoke=Keeper    # engrave an origin/liberation rune into the runite
php cast sentinel --revoke=Keeper    # take it out
```

It also scaffolds and repairs liberation runes (`--create-rune`, `--phantasm-fix`). The `#sentinel-*` comment markers in a `cast` file (e.g. `#sentinel-manifest`, `#sentinel-awaken`, `#sentinel-codex`) are anchors Sentinel edits around — **keep them** if you use Sentinel.

## The journey (summary from the Rune README)

1. **Awakening** — an empty `cast` becomes a runite.
2. **Engraving** — write casts: `Chanter::cast('wind --art', fn() => …, 'note')`.
3. **Echoes & Arcane** — Keeper remembers in `.echoes/`; Aether records every step as arcane (`grimoire --arcane`).
4. **Artefact** — seal the runite + echoes + shards into a `.rune` to share.
5. **Revoke** — restore an artefact to life in another place.

## Laws of the Rune (invariants — do not break)

1. One rune, one purpose.
2. Entity holds the logic; entities call other entities.
3. Manifest only forwards to entities.
4. Phantasm is the contract (replaces Reflection).
5. Aether flows everywhere; runes awaken together in one flow.
6. Every change raises the Phantasm version of the rune that changed.
7. A liberation rune never replaces an origin rune.
