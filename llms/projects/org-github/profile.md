# `.github` — Org Profile README

**Path:** `profile/README.md` → renders the public org landing page at `github.com/devneet-id`.

## Current structure (as redesigned)

1. **Tagline** — "An open community building fast, simple, and accessible software systems."
2. **Identity badges** — based-in Indonesia, focus open-source, Open Collective supporters (live), Hugging Face.
3. **Intro** — two short paragraphs (the "openness compounds" principle).
4. **Tech Stack** — PHP, JavaScript, CSS, Git badges.
5. **What We Build** — the project list, ordered **rune → reliquary → exura**:
   - **rune** · PHP · Concept — lore-driven modular concept beneath PHP.
   - **reliquary** · PHP · Registry — the Federated Relic Registry for Rune (no central registry; repo is the registry, federated by fork; relic = sealed `.rune` snapshot).
   - **exura** · Minimalist Framework Series — umbrella, with its **three packages listed** (exuraphp / exurajs / exuracss).
   - Each entry carries **live GitHub-API badges** (last commit, language, code size, open issues).
6. **Our Approach** — minimal by design, open & accessible, built to last, community-driven.
7. **Get Involved** — repos, Open Collective, Hugging Face.

## Design intent

- Formal, professional, analytical tone.
- Metrics are **live** (shields.io against the GitHub API) — no manual maintenance.
- Order reflects the dependency/importance story: the foundation (rune), then how it's distributed (reliquary), then the independent framework family (exura).

## History / decisions captured

- Exura was consolidated from three separate entries into **one umbrella entry that keeps its three packages listed** (same philosophy, three layers).
- Reliquary's label was corrected from "Relic Package Manager" to **"Federated Relic Registry"** after reading the live repo.
- The banner image is currently **not** present at the top of the on-disk file (it was in an earlier draft). Re-adding it is an open cosmetic choice.

## For an AI editing this

- Keep it in **English**, formal and analytical.
- Preserve the rune → reliquary → exura order unless the maintainer changes priorities.
- Prefer live badges over hand-maintained numbers.
