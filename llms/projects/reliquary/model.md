# Reliquary — The Federated Model

## No central registry

- The **repo is the registry.** Every reliquary carries its own two records: `relic.json` and `nexus.json`.
- Reliquaries are **federated by fork.** Fork a reliquary and you have your own registry, still linked to the one you forked. Others fork yours. One nexus leads to the next.
- `devneet-id/reliquary` is only the **first** reliquary — it maps its forks, it does not hold them.

```
devneet-id/reliquary
├── relic.json   devneet-id/*          (this owner's relics)
└── nexus.json   → fork/reliquary ─┬─ relic.json   fork/*
                                    └─ nexus.json   → … and onward
```

Principles:

- **No central registry.** The first reliquary maps its forks; it does not hold them.
- **Code from devneet, data from you.** A fork takes new code via *Sync fork*; its records belong to its owner.
- **Relics stay home.** A `.rune` rests in its own repo; a reliquary only records the link and the seal (sha256).
- **Your reliquary, your care.** `devneet-id/reliquary` does not review other reliquaries' relics.

## The Docker parallel (mental model)

| Docker | Reliquary |
|---|---|
| image | relic (`.rune`), a sealed snapshot of a runite |
| `docker build` | `php cast reliquary --runite-relic` |
| tag · digest | version · seal (sha256) |
| `docker push` | push the `.rune` to its repo, then `php relic register` |
| `docker pull` + run | `php cast reliquary --relic-runite=<vendor>/<repo>` |
| Docker Hub | `devneet-id/reliquary` and every fork, each a registry itself |

## The two records

| Record | Kept by | Holds |
|---|---|---|
| `relic.json` | the `relic` tool | the relics of this reliquary's owner |
| `nexus.json` | the `nexus` tool | the links to its forks — only the way to them |

See [records.md](records.md) for the exact JSON shapes.

## The page (how a reliquary is browsed)

Each reliquary publishes an `index.html` that **reads `relic.json` and `nexus.json` next to it at load time** — push your records and the page follows, no rebuild needed. It is served by **GitHub Pages**:

- *Settings → Pages → Deploy from a branch → `main` / root*
- Lives at `https://<you>.github.io/<repo>/`.

Because a browser cannot read `file://`, run `php cast start` (or `php cast serve`) locally instead of opening `index.html` directly.

## The Federation of Fides

*Fides* is trust; *foedus*, the pact at the root of *federation*, shares its root. Every vendor keeps its own reliquary, and the seals keep the trust between them.
