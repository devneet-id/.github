# Exura

**Umbrella repo:** `devneet-id/exura` — the Exura series: introduction and docs for the three packages. Each package also has its own repo and can be used **independently**.

> One philosophy — minimalist, semantic-first, modern — delivered across three layers of the stack.

## Files in this project folder

- [exuraphp.md](exuraphp.md) — the PHP backend micro-framework.
- [exurajs.md](exurajs.md) — the JavaScript frontend micro-framework.
- [exuracss.md](exuracss.md) — the semantic-first CSS framework.
- [status.md](status.md) — current state.

## The series

| Package | Repo | Language | Role |
|---|---|---|---|
| **exuraphp** | `devneet-id/exuraphp` | PHP | Minimalist micro-framework for modern **backend** development. |
| **exurajs** | `devneet-id/exurajs` | JavaScript | Minimalist micro-framework for modern **frontend** development. |
| **exuracss** | `devneet-id/exuracss` | CSS | Modern, **semantic-first** CSS framework. |

Topics the series emphasises: lightweight, reactive, REST API, semantic CSS.

## Relationship to the rest of DEVNEET

- **Independent of Rune.** Exura is a general-purpose framework family for the web stack, not a Rune dependency. The two share DEVNEET's design philosophy (minimal, semantic, composable) but are separate codebases.
- **Reachable from Reliquary.** `php exura fetch --part=css|js|php|all` pulls Exura into a project's `src/exura/` (used by the reliquary website, for instance).

## The umbrella repo (`exura`)

- Primarily **documentation**: the series intro plus cross-package docs (Markdown), an `index.html` docs page, and a PHP `cast` build tool.
- Treat it as the canonical place for the series narrative; go to the individual package repos for implementation.

## For an AI working on Exura

- Keep the three packages consistent **in spirit** — same minimalist, semantic philosophy, different target environment.
- Implementation changes belong in the package repo; narrative/cross-cutting docs belong in `exura`.
- The three can be adopted standalone — don't introduce hard coupling between them.
