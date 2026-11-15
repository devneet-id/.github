# DEVNEET — The Organization

## What DEVNEET is

DEVNEET is an open developer community based in **Indonesia**, building fast, simple, and accessible software systems. It designs and maintains **public** projects that lower the barrier to modern software development — favouring clarity over complexity, and practical adoption over novelty for its own sake.

Guiding principle: **openness compounds.** Shared knowledge, open source code, and transparent collaboration are seen as the most reliable path to technology that is both sophisticated and broadly beneficial.

## Mission in practice

- Build tools that are **minimal by design** — every dependency, abstraction, and line of config is treated as a cost.
- Keep everything **semantic-first** — names and structure carry meaning; code reads like intent.
- Stay **open and federated** — public by default, and distribution avoids central chokepoints.
- Grow through **community** — contributions, discussion, and shared ownership shape direction.

## The portfolio (what we actually work on)

| Project | One-line | Language | Role in the whole |
|---|---|---|---|
| **Rune** | A lore-driven, modular concept beneath PHP. | PHP | The foundation everything else builds on. |
| **rune-lore** | Docs and lore for Rune, taught Act by Act. | Docs | Teaching/onboarding for Rune. |
| **Reliquary** | The Federated Relic Registry for Rune. | PHP (on Rune) | How Rune apps are packaged & shared. |
| **Exura** | A minimalist framework series. | HTML/docs umbrella | Independent web-stack frameworks. |
| **exuraphp** | Backend micro-framework. | PHP | Exura — backend layer. |
| **exurajs** | Frontend micro-framework. | JavaScript | Exura — frontend layer. |
| **exuracss** | Semantic-first CSS framework. | CSS | Exura — styling layer. |
| **.github** | Org profile, design gallery, tooling, AI context. | Mixed | Org-wide home & meta. |

## How we work

- **Everything in the open** on the `devneet-id` GitHub organization.
- **Design assets** live in `.github/design/` as a gallery; contributors drop their own folder in and open a PR (or push directly if they have access). See [projects/org-github/](projects/org-github/README.md).
- **Tooling is dogfooded.** The design gallery is managed by a Rune app (`.github/runite-app`) whose casts generate the gallery READMEs — Rune building Rune's own org.
- **Distribution is federated.** Rune apps ship as relics through Reliquary; there is no central registry to gatekeep.

## Infrastructure & presence

- Code & docs: **GitHub** (`github.com/devneet-id`).
- Funding: **Open Collective** (`opencollective.com/devneet`).
- Models/datasets: **Hugging Face** (`huggingface.co/devneet`).
- Packages: **Packagist** (`devneet/rune`, and the Exura packages).

## Who maintains it

The community is led by its maintainers (primary GitHub handle seen across repos: **AnwarAchilles**). Contributors are welcomed at all levels — developers, designers, writers.

## The aesthetic (important for understanding the code)

DEVNEET's flagship, Rune, uses a deliberate **lore vocabulary** — Ether, Essence, Entity, Grimoire, Relic, Reliquary, Phantasm, and so on. This is not decoration: each word maps to a real construct. A new agent should read [glossary.md](glossary.md) before reading code, or the naming will be confusing.
