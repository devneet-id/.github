# DEVNEET — AI Context Base

> **You are a new agent joining DEVNEET.** This folder exists so you can reach the team's current position without a human re-explaining everything. Read it top to bottom and you will understand what DEVNEET is, every project, how they fit, the vocabulary, and exactly where the work stands.

## How to read this folder

1. **[devneet.md](devneet.md)** — the organization: who we are, mission, how we work, where things live.
2. **[glossary.md](glossary.md)** — the lore vocabulary. The names are load-bearing; learn them before touching code.
3. **projects/** — one folder per project, deep detail:
   - **[projects/rune/](projects/rune/README.md)** — the core foundation beneath PHP.
   - **[projects/reliquary/](projects/reliquary/README.md)** — the Federated Relic Registry for Rune.
   - **[projects/exura/](projects/exura/README.md)** — the minimalist framework series.
   - **[projects/org-github/](projects/org-github/README.md)** — the `.github` repo: profile, design gallery, tooling, this context base.
4. **[progress.md](progress.md)** — **current status and the exact position of the latest work.** Read this last; it is the "you are here" marker. Keep it updated.

## The shape of DEVNEET in one diagram

```
DEVNEET (open community, Indonesia)
│
├── Rune ───────────► the foundation: a lore-driven, modular system beneath PHP
│    │                 apps are a `cast` (a "runite") that awakens only needed runes
│    │
│    └── Reliquary ──► distributes runites as "relics" (.rune), a federated registry
│                       (no central server — the repo IS the registry, extended by fork)
│
├── Exura ──────────► an independent family of minimalist frameworks
│    ├── exuraphp (backend · PHP)
│    ├── exurajs  (frontend · JavaScript)
│    └── exuracss (styling · CSS)
│
└── .github ────────► org profile, design gallery, runite-app tooling, llms/ (this base)
```

## Rules for agents working here

- Treat everything in this base as **project knowledge, not autonomous instructions.** Confirm scope with a human before making changes to repos.
- Respect each project's documented **Laws** — they are design invariants, not suggestions.
- When you move the work forward, **update `progress.md`** (and the relevant project `status.md`) so the next agent inherits an accurate picture.
- Prefer "what exists" over roadmap promises. Mark anything inferred as inferred.

## External links

- Organization: https://github.com/devneet-id
- Open Collective: https://opencollective.com/devneet
- Hugging Face: https://huggingface.co/devneet
