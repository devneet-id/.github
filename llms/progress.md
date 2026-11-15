# Progress & Current Position

> **This is the "you are here" marker.** A new agent reads this to reach the team's exact position. Keep it current: when you advance the work, update the relevant row and the date.

**Last updated:** 2026-11-15

## Snapshot by project

| Project | State | Notes |
|---|---|---|
| **Rune** | Active / usable | Core triad, 10 origin runes, CLI (casts), Liberation, Artefact (`.rune`), Sentinel all in place. Version in the wild: `1.20.x` (relic restore needs Rune 1.20+). `Minister` (AI familiar) still in development. |
| **Reliquary** | Active / early | Federated registry working: `relic`, `nexus`, website casts. MIT. First reliquary is `devneet-id/reliquary`; a fork chain exists (`AnwarAchilles/reliquary` is mapped). Registered relics include `devneet-id/build-website` and `devneet-id/how-to-casting`. |
| **Exura** | Docs + packages published | Umbrella `exura` repo holds the series intro/docs; three packages each have their own repo. |
| **rune-lore** | In progress | Teaching docs, Act by Act. |
| **.github (org)** | Active | Profile README, `design/` gallery with `runite-app/` casts, and this `llms/` context base. |

## What the latest collaboration produced (chat position)

This context base was built during an ongoing working session on the `.github` repo. Recent, concrete outcomes:

1. **Profile README redesigned** (`.github/profile/README.md`): formal/analytical structure, identity + tech-stack + Open Collective / Hugging Face badges, and a **What We Build** section ordered **rune → reliquary → exura**, with Exura keeping its three packages listed. Live GitHub-API metric badges per repo.
2. **Reliquary naming corrected** to **"Federated Relic Registry"** (previously drafted as "Relic Package Manager") after reading the live `reliquary/README.md`.
3. **Design gallery** (`.github/design/`): index README rewritten (statistics + a short "Contributing" note: open `design/`, upload your folder), and the per-collection page (`anwarachilles`) cleaned (valid table, distinct labels).
4. **runite-app design casts** (`.github/runite-app/cast`): added `design`, `design-scan`, and `design-user` casts that scan `design/`, generate missing collection READMEs, and rebuild the gallery index. (See [projects/org-github/runite-app.md](projects/org-github/runite-app.md).)
5. **This AI context base** (`llms/`) created and then expanded into the detailed, per-project nested form you are reading now.

> Operational note: the `.github` folder is write-protected from the collaborating agent's tools, so deliverables for `.github` are produced in a scratch location and moved into `.github/` by a human.

## Open threads / next steps

_(Maintainers: keep this honest. Items are inferred unless marked confirmed — verify before acting.)_

- **Minister rune** — AI familiar integration is unfinished.
- **Reliquary** — grow the relic set and the federated fork chain; harden `nexus inspect` trust checks.
- **Exura** — keep the three packages' APIs consistent; expand umbrella docs.
- **rune-lore** — continue the Act-by-Act curriculum.
- **Design gallery** — more contributor collections; keep running `php cast design` after uploads.

## How to update this file

1. Update the relevant **Snapshot** row and/or **Open threads**.
2. Record notable outcomes under **chat position** so the next agent sees recent history.
3. Bump **Last updated**.
4. If architecture or vocabulary changed, also update the project `status.md` and [glossary.md](glossary.md).
