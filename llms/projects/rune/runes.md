# Rune — The Origin Runes

Ten runes live at the origin. Each holds one purpose; Aether flows through all of them. Law: **one rune, one purpose.**

Below, the runes verified at method level (read directly from source) show their real Manifest methods. Runes marked _(from README)_ are described at the documented level; confirm method names in source before relying on them.

---

## Aether — the flow beneath everything
Paths, stopwatch, memory, the arcane log, exit, version footer.
**Manifest:** `begin($flags=0)`, `end()`, `dd($data, $force=false)`, `exit($force=false)`.
Internally exposes many `aether_*` helpers (e.g. `aether_arcane()`, `aether_has_entity()`, `aether_exit()`, `aether_memoryusage()`, `aether_formatFileSize()`, `aether_zero_trust()`).

## Chanter — the CLI gate
Casts (commands), spells (`--options`), echoes (notes), zero trust.
**Manifest:**
- `cast(string $arg, ?callable $execute = null, string $echo = '')` — register a cast (or get it if `$execute` omitted); `$echo` is its note.
- `spell(string $key, mixed $value = null, mixed $fail = false)` — get a spell value, or set it.
- `echo(string $arg, string $note = '')` — get/set a cast's note.
- `begin()` — load built-in casts from `@bindrune/chanter/*`.
- `end()` — extract argv, resolve the cast, dispatch (honours `--zero-trust`).

Spell parsing: `--flag` → `true`; `--key=value` → `"value"` (URL-decoded); absent → `false`.

## Whisper — the voice to the user
Styled echo, input, clear, drain (buffer), flash (spinner).
**Manifest:**
- `echo(string $message, bool $asString = false)` — print with style tokens; returns self (chainable).
- `call(string $text)` — prompt for STDIN input.
- `drain(callable|bool $stateOrProcess, bool $asString = false)` — buffer output.
- `clear(bool $force = false)` — clear the terminal.
- `flash(callable $execute)` — run with a live spinner (`animation`, `stop`, `continue` helpers).

**Style tokens** (resolved by Whisper, applied per-message): `{{color-primary|secondary|success|warning|info|failed|danger|error|debug|end}}`, backgrounds `{{bg-*}}`, `{{icon-*}}` (e.g. `[√]`, `[x]`, `[!]`, `[i]`), `{{label-*}}`, and vars `{{nl}}`, `{{tab}}`, `{{bold}}`, `{{php}}`.

## Weaver — text and templates
Bind `{{var}}`, bond (key/value store), wrap, minify.
**Manifest:**
- `bind(string $template, $searchOrArray, string $data = '')` — replace `{{var}}`; pass an assoc array for multiple.
- `bond(string $key, mixed $value)` — set/get a template variable in the global bond.
- `item(string $source, string $alias = '')` — load a template file (optionally aliased).

Internally: `weaver_wrap_word/letter`, `weaver_min_*` (css/js/html/php minifiers).

## Forger — files and folders
Trace, scan, fix, move, clone, clean, observe.
**Manifest:**
- `trace(string $path, ?callable $cb = null)` — resolve each path part, tagging item/repo + existence.
- `scan(string $path, ?callable $cb = null)` — list entries (glob); each is a pathinfo object with `target`; optional callback transforms each.
- `info(string $path)` — object: `target`, `type` (`item`/`repo`), `base`, `name`, `ext`, `path`.
- `fix(array $paths)` — create missing dirs (`repo`) or files (`item`).
- `clean(string $path, bool $force = false)` — remove file/dir (recursive if forced).
- `move(array $paths)` / `clone(string $from, string $to)` — move/copy, creating structure.
- `repo(string $path, bool $recursion = false)` — ensure a dir exists (optionally scan).
- `item(string $path, mixed $content = false, int $flags = 0)` — read a file (no content) or write it (content given; dir must exist).
- `observer(string $path)` — latest mtime in a tree (for watch).

## Cipher — secrets _(from README)_
Unique id, hash, base64, and the runic cipher.

## Keeper — memory in `.echoes/` _(from README)_
Items, shards, arcane, glitch. Also powers "fancy error handling." Constants like `KEEPER_ECHOES`, `KEEPER_ECHOES_ARCANE` point into `.echoes/`.

## Crafter — the builder _(from README)_
Item → seed → shard → spark into one distributable file (part of the Artefact/Runite pipeline).

## Specter — beyond the main process _(from README)_
Cast in another window, soul, seer, observer, and a dev server. Multi-process & interaction. `specter_exit()` re-runs a cast in a separate process.

## Minister — the AI familiar _(from README, in development)_
Speaks with a familiar (AI spirit). **Not finished** — this is an active development area.

---

## Liberation runes (user-made)

Beyond the ten, you can create your own runes with **Liberation** (see [lifecycle.md](lifecycle.md)). They live in `@liberations/` and are shaped with Sentinel (`php cast sentinel --create-rune=<name>`, `--phantasm-fix`, `--invoke`). Law: **a liberation rune never replaces an origin rune** — need a variant, give it a new name (e.g. `MYWeaver`).
