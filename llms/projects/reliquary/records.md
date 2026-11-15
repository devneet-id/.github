# Reliquary — Record Formats

A reliquary carries two JSON records. Both have `main` (this reliquary's identity, `<owner>/<repo>`) and a `list`.

## `relic.json` — this owner's relics

```json
{
  "main": "devneet-id/reliquary",
  "list": {
    "devneet-id/exuracss": {
      "repo": "https://github.com/devneet-id/exuracss",
      "runite": "cast",
      "note": "…",
      "tags": {
        "1.1.0": {
          "url": "https://raw.githubusercontent.com/devneet-id/exuracss/1.1.0/cast.rune",
          "sha256": "…",
          "rune": "1.20.110"
        },
        "1.1.1": {
          "url": "https://raw.githubusercontent.com/devneet-id/exuracss/<commit>/cast.rune",
          "sha256": "…",
          "rune": "1.20.110",
          "ref": "main@1a2b3c4"
        }
      }
    }
  }
}
```

Field notes:
- **key** (`devneet-id/exuracss`) — the relic name, always `<owner>/<repo>`.
- **repo** — the GitHub repo the `.rune` lives in.
- **runite** — the runite file name inside that repo (usually `cast`), so the relic is `cast.rune`.
- **note** — human description.
- **tags** — one entry per version: `url` (raw link to the `.rune`), `sha256` (the **seal**), `rune` (the Rune version it was sealed with), and optional `ref` (`main@<commit>`) when the version was taken from `main` and pinned to a commit.

### Observed live data (devneet-id/reliquary)

The real `relic.json` currently lists, for example:
- `devneet-id/build-website` — "Build a website with HTML, CSS, JS & PHP, bundled into one dist/index.php." (tag `0.1.0`).
- `devneet-id/how-to-casting` — "Learn how to cast: casts, spells, and cast in cast." (tags `0.1.0`, `0.1.1`).

## `nexus.json` — links to forks

```json
{
  "main": "devneet-id/reliquary",
  "list": {
    "demo/reliquary": {
      "owner": "demo",
      "branch": "main",
      "relic": "https://raw.githubusercontent.com/demo/reliquary/main/relic.json",
      "nexus": "https://raw.githubusercontent.com/demo/reliquary/main/nexus.json"
    }
  }
}
```

Field notes:
- **key** — the fork reliquary (`<owner>/reliquary`).
- **owner / branch** — where to read it.
- **relic / nexus** — raw URLs to that fork's two records, so the chain can be walked (forks of forks).

### Observed live data

`devneet-id/reliquary`'s `nexus.json` maps `AnwarAchilles/reliquary` (owner `AnwarAchilles`, branch `main`).

## Walking the federation

Starting at any reliquary: read its `relic.json` (its catalog) and its `nexus.json` (its forks), then follow each fork's `nexus` URL recursively. `php nexus inspect --repo=<owner>/<repo>` does this to one target and verifies seals.
