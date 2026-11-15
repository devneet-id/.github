# Glossary — DEVNEET / Rune vocabulary

The projects use a deliberate, lore-driven vocabulary. These names are load-bearing: they map to real constructs in the code. Learn them before editing.

## Rune core

- **Rune** — a modular unit of the framework; "something we don't know yet" until invoked.
- **Ethereal** — the bootstrap surface (`Rune\Ethereal`); "a place/thing we don't know."
- **Ether** — truth that does not change but always has meaning (constants / configuration).
- **Essence** — something that can change over time (state / flow).
- **Entity** — something that makes other things change (behaviour / logic).
- **Manifest** — a box connecting things so they work together; forwards calls to entities. A runite speaks through `Rune\X\Manifest`.
- **Phantasm** — a picture in the mind; the **living contract that replaces Reflection** (holds version, user, note, mark, link, node — read by the Grimoire).

## The triad lifecycle

Each rune is awakened in three steps, lazily: `Manifest::ether()::essence()::entity()`.
- **ether()** loads truth, **essence()** loads flow, **entity()** loads behaviour.

## Process & lifecycle

- **Awakening** — starting from anywhere (`Rune\Ethereal::awakening()`); turns an empty `cast` into a runite.
- **Liberation** — freedom to create your own runes beside the origin ones (`Rune\Ethereal::liberation()`, stored in `@liberations/`).
- **Echoes** — persisted memory in `.echoes/` (kept by the Keeper rune); "sounds from the past."
- **Arcane** — the phased process log recorded by Aether (revealed by `grimoire --arcane`).
- **Bindrune** — many runes joined; built-in casts live in `@bindrune/` (e.g. `rune`, `grimoire`, `artefact`, `sentinel`).
- **Grimoire** — "a book that feels alive"; system inspection (`php cast grimoire`).
- **Sentinel** — a guard that engraves/removes runes in a runite.

## CLI

- **cast** (noun) — the app file, and also a registered command.
- **runite** — a `cast` app (any project built on Rune).
- **spell** — a command option (`--name`, or `--name=value`).
- **echo** — a note attached to a cast; also Whisper's styled terminal output.
- **zero trust** — a guarded execution mode for breaking changes.

## Distribution (Reliquary)

- **Artefact** — "a thing we can see"; the act/result of sealing a runite.
- **Relic** — a `.rune` file: a sealed snapshot of a runite (code + echoes + shards). Analogous to a Docker image.
- **Shard** — a small piece of a relic / a project item packaged on its own.
- **Reliquary** — a federated registry recording where relics rest and their seals.
- **Seal** — the sha256 of a `.rune` at the time it was listed.
- **Nexus** — the map of a reliquary's forks (`nexus.json`); one nexus leads to the next.
- **Relic Package** — a registered relic entry in `relic.json` (name = `<owner>/<repo>`).
- **Fides / Foedus** — trust / pact; the root idea behind the federation of reliquaries ("The Federation of Fides").

## Quick analogies (for grounding)

- Rune ≈ a lazy, modular PHP foundation — runes instead of services, no bootstrap.
- Relic ≈ Docker image; Reliquary ≈ a federated Docker Hub with **no central server**.
- Phantasm ≈ Reflection, but declared and alive.
- Grimoire ≈ a live, self-describing `--help`/inspector.
