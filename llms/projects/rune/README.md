# Rune

**Repo:** `devneet-id/rune` · **Package:** `devneet/rune` (Composer / Packagist) · **Language:** PHP · **License:** MIT

> A lore-driven, modular concept beneath PHP that responds to development rather than dictating it.

Rune is the foundation of the DEVNEET ecosystem. It is **lightweight, lazy-loaded, and process-based** — closer to a toolkit of composable "runes" than a conventional framework. There is **no bootstrapping**; each rune awakens only when invoked. Documentation is **live** (Phantasm) instead of relying on Reflection.

## Files in this project folder

- [architecture.md](architecture.md) — the triad (Ether/Essence/Entity), Manifest, Phantasm, the Aether flow.
- [runes.md](runes.md) — all ten origin runes with their real methods.
- [cli.md](cli.md) — casts, spells, echoes; how to write commands; worked examples.
- [lifecycle.md](lifecycle.md) — awakening, liberation, artefact/relic, sentinel, versioning.
- [status.md](status.md) — current state and open threads.

## Why it exists

Conventional frameworks dictate structure up front (bootstrap, container, config, convention). Rune inverts that: you **awaken only what you invoke**, compose small purposeful units, and let the system stay minimal. It "responds to development rather than dictating it" — you sculpt structure from intent.

Essentials (from the project README):

- Modular core structure; functional, process-based.
- Lazy loading without bootstrapping.
- Live documentation replacing Reflection (**Phantasm**).
- Automatic minor & patch versioning.
- PSR-4 Composer autoloading; static class service handlers.
- A full, "fancy" CLI (100% CLI support): styled output, input, progress.
- Save/load a project as a package (**Runite / Artefact**), items as packages (**Shard**).
- Metadata storage (`.echoes/`, via **Keeper**), zero trust for breaking execution.
- Event-driven & encapsulation (**Chanter**), multi-process (**Specter**), liberation (custom runes).

## Install & first run

```bash
composer require devneet/rune
echo "#rune" > cast        # placeholder entry file
```

Minimal `cast` (the app file / "runite"):

```php
<?php
require_once __DIR__ . '/vendor/autoload.php';
Rune\Ethereal::awakening();   // awaken from the void
```

```bash
php cast            # run the app
php cast grimoire   # inspect the system (live docs)
```

## The paradigm (how to think about it)

> At first, humans did not know anything. By looking, writing, and growing, we finally understand.

- **Rune / Ethereal** = the unknown thing / place.
- **Ether / Essence / Entity** = unchanging truth / changeable flow / the mover.
- **Manifest / Phantasm** = the connector / the mental picture (contract).
- **Awakening / Liberation / Echoes / Runite / Shard / Bindrune / Grimoire / Sentinel / Artefact** = see [glossary](../../glossary.md).

## Related repos

- `devneet-id/rune-lore` — the lore and docs, taught Act by Act.
- Local working copies on the maintainer's machine: `rune/` (source), `rune-dev/`.
- `rune-art` — logo/artwork used by Rune's README.
