# Reliquary — Commands

Every command asks what it needs interactively; every question can also be answered with a spell, so commands run unattended too (e.g. in GitHub Actions).

## `relic` — manage this reliquary's relics (`relic.json`)

| Command | Spells | Description |
|---|---|---|
| `php relic initiate` | `--user=<username>` `--yes` | Start a clean `relic.json` as `<username>/<project folder>` (folder name = your repo name). |
| `php relic register` | `--repo=<repo>/<runite>` `--tag=` `--note=` | Register a relic, e.g. `exuracss/cast` → `cast.rune`. No tag → `main` as `0.1.0`. |
| `php relic upgrade` | `--repo=<repo>` `--tag=` | Add a new version. No tag → next patch from `main` (`0.1.0` → `0.1.1`). |

## `nexus` — manage links to forks (`nexus.json`)

| Command | Spells | Description |
|---|---|---|
| `php nexus initiate` | `--user=<username>` | Start a clean `nexus.json` as `<username>/<project folder>`. |
| `php nexus update` | — | Map every fork of this reliquary into `nexus.json`. (Uses the GitHub API.) |
| `php nexus inspect` | `--repo=<owner>/<repo>` | Pick one reliquary on the chain (forks of forks too) and check its seals. |

## website — publish the reliquary's page

| Command | Description |
|---|---|
| `php cast build` | Bundle `src/` into `index.html` (the page of this reliquary). |
| `php cast serve` | Serve this reliquary at `http://127.0.0.1:8000`. |
| `php cast watch` | Rebuild `index.html` whenever `src/` changes. |
| `php cast start` | Build, then serve & watch in their own processes. |
| `php exura fetch --version=1.1.0 --part=css\|js\|php\|all` | Fetch Exura into `src/exura/`. |

## Making a relic (in the runite's own repo)

```bash
php cast reliquary --runite-relic                 # cast → cast.rune (the snapshot)
git add cast.rune && git commit -m "feat: relic" && git tag 1.0.0 && git push --tags
```

Then, in your reliquary:

```bash
php relic register --repo=<repo>/cast --tag=1.0.0
```

Anyone can bring it back to life, in any runite (Rune 1.20+):

```bash
php cast reliquary --relic-runite=<vendor>/<repo>
```

## Maintenance cheat-sheet

| When | Cast |
|---|---|
| You publish a new relic | `php relic register` |
| A relic has a new tag, or `main` moved | `php relic upgrade` |
| Someone forked your reliquary | `php nexus update` |
| You want to trust a reliquary | `php nexus inspect` |
| Your records changed | `php cast build` |

Then commit and push `relic.json`, `nexus.json`, and `index.html` — your registry is what you push.

## Notes

- `GITHUB_TOKEN` (env var) is sent to the GitHub API when set: 60 req/hr without it, 5,000 with it. Only `nexus update` and versions taken from `main` use the API; everything else reads raw files.
