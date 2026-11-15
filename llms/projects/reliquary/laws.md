# Reliquary — The Laws (invariants)

These are design invariants. Tooling enforces them; do not design around them.

1. **A name is its repo.** A relic is named `<owner>/<repo>`, and a reliquary lists only its owner's own repos — nobody can take another's name.
2. **A version never changes.** The same version with another seal is refused; a change is a new version.
3. **The seal is sha256** of the `.rune` when it was listed. `nexus inspect` shows any seal that broke.
4. **A version from `main` is pinned to its commit.** When `main` moves on, older versions stay whole (the record keeps a `ref` like `main@<commit>`).
5. **A fork that has not initiated is silent.** It still holds its parent's records; until `php relic initiate` / `php nexus initiate`, those inherited names are ignored.

## Why these matter

- **Trust by seal.** Because relics live in their own repos (not centrally hosted), the sha256 seal is how a consumer knows a relic is the exact bytes that were listed. Broken seals surface via `nexus inspect`.
- **Immutability.** Law 2 + Law 4 mean a given version always restores to the same thing, even as development continues on `main`.
- **Ownership.** Law 1 + Law 5 keep the federation honest: a fork cannot impersonate another owner, and an un-initiated fork cannot accidentally republish its parent's catalog as its own.
