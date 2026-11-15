# Reliquary

**Repo:** `devneet-id/reliquary` · **Language:** PHP (built on Rune) · **License:** MIT

> Forged through Rune. Kept by its people. The **Federated Relic Registry** for Rune.

> A reliquary keeps no relic — it only remembers where each one rests, and the seal it bore when it was listed.

## Files in this project folder

- [model.md](model.md) — the federated design, `relic.json` / `nexus.json`, the Docker analogy.
- [commands.md](commands.md) — every `relic`, `nexus`, and website command.
- [laws.md](laws.md) — the five Laws of the Reliquary (invariants).
- [records.md](records.md) — the on-disk record formats, with examples.
- [status.md](status.md) — current state and open threads.

## The idea in one paragraph

A **relic** (`.rune`) is a sealed snapshot of a runite — its code, echoes, and shards in a single file — much like a Docker image: take it anywhere and it comes back to life as it was sealed. A **reliquary** records *where* each relic rests and the **seal (sha256)** of each version. Unlike Docker Hub, there is **no central registry**: the repo *is* the registry (its own `relic.json` and `nexus.json`), and reliquaries are **federated by fork** — fork one and you have a registry of your own, still linked to its parent; others fork yours, and one nexus leads to the next.

## Requirements

- PHP 8.1+ with `curl` (or `allow_url_fopen`)
- Composer
- A GitHub account
- `GITHUB_TOKEN` (optional) raises the GitHub API limit from 60 to 5,000 req/hr — used by `nexus update` and `main`-based versions.

## Begin your own reliquary (quickstart)

```bash
# 1. Fork devneet-id/reliquary and clone your fork
composer install
# 2. Make the inherited records yours
php relic initiate
php nexus initiate
# 3. Register relics, then push
php relic register
git add relic.json nexus.json && git commit -m "feat: my reliquary" && git push
```

Your reliquary is now a registry of its own, linked to its parent; the parent's next `php nexus update` maps it.

## Depends on

- **Rune** (`devneet/rune ^1.12`); relic restore needs Rune **1.20+**.
- The `reliquary` cast inside a runite performs sealing/restoring (`--runite-relic`, `--relic-runite=<vendor>/<repo>`).

## Local working copies

- `reliquary/` — the registry app (contains `relic`, `nexus`, `cast`, `relic.json`, `nexus.json`, `src/`, `index.html`).
- `reliquary-dev/` — holds `notes/`.
