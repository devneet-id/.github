# The `.github` Repo (Org Home & Tooling)

**Repo:** `devneet-id/.github`

GitHub's special org repo. Beyond rendering the org profile, DEVNEET uses it as the home for org-wide assets, tooling, and this AI context base.

## Files in this project folder

- [profile.md](profile.md) — the org profile README (`profile/README.md`).
- [design-gallery.md](design-gallery.md) — the `design/` community gallery.
- [runite-app.md](runite-app.md) — the Rune app whose casts manage the gallery.

## Layout

```
.github/
├── profile/README.md     → renders at github.com/devneet-id (the org landing page)
├── design/               → community design gallery (official/ + per-contributor folders)
│   ├── official/         → canonical brand assets (team-maintained)
│   ├── <username>/       → a contributor's folder, with a generated README gallery
│   └── README.md         → gallery index (generated)
├── runite-app/           → a Rune runite; casts manage the design gallery
│   ├── cast              → the runite (design / design-scan / design-user casts)
│   └── vendor/devneet/rune
└── llms/                 → this AI context base
```

## Special GitHub paths used here

- `profile/README.md` — the public org landing page.
- (Available but confirm before assuming) community health files like `FUNDING.yml`, `CODE_OF_CONDUCT.md`, etc. would also live here and apply org-wide.

Everything else (`design/`, `runite-app/`, `llms/`) is ordinary storage/tooling with no special GitHub behaviour — accessed via raw URLs or cloned like any repo.

## Important operational note

The `.github` folder is **write-protected from the collaborating AI's file tools** (it is treated as a protected location name). Deliverables destined for `.github/` are produced in a scratch folder and **moved into place by a human**. This is why files sometimes land in a `Claude outputs/` download folder first.
