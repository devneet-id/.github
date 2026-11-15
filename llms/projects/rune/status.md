# Rune — Status

**Last updated:** 2026-11-15

## State: Active / usable

Rune is the most mature project in the ecosystem and is in real use (Reliquary and the org's `runite-app` are built on it).

## Confirmed in place

- Core triad (Ether / Essence / Entity), Manifest, Phantasm.
- Ten origin runes present: Aether, Chanter, Whisper, Weaver, Forger, Cipher, Keeper, Crafter, Specter, Minister.
- CLI: casts, spells, echoes; built-in `rune`, `grimoire`, `artefact`, `sentinel` casts (via `@bindrune`).
- Liberation (custom runes in `@liberations/`), Sentinel scaffolding.
- Artefact/Runite sealing to `.rune`; restore needs Rune **1.20+**.
- Automatic `major.sum` versioning (seen: `1.20.x`, e.g. `1.20.114`).

## In development / known gaps

- **Minister** (AI "familiar") — explicitly still in development.
- Some runes (Cipher, Keeper, Crafter, Specter) are documented here from the README's descriptions; their exact method signatures should be read from source before being relied upon. Aether, Chanter, Whisper, Weaver, Forger are verified at method level.

## Dependencies & packaging

- Distributed via Composer/Packagist as `devneet/rune` (apps require e.g. `^1.12`; relic restore needs `1.20+`).
- MIT licensed.

## Related work to watch

- `devneet-id/rune-lore` — the Act-by-Act teaching material; the natural place to send new developers.
- Reliquary depends on Rune and defines the `reliquary` cast used for sealing/restoring relics.
