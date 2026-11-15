# Rune — CLI (casts, spells, echoes)

The CLI is Rune's primary interface. An app is a file named `cast` (a "runite"). You register **casts** (commands); users pass **spells** (options) and read **echoes** (notes).

## Anatomy

```php
<?php
require_once __DIR__ . '/vendor/autoload.php';

use Rune\Aether\Manifest  as Aether;
use Rune\Whisper\Manifest as Whisper;
use Rune\Weaver\Manifest  as Weaver;
use Rune\Chanter\Manifest as Chanter;
use Rune\Forger\Manifest  as Forger;

// INVOCATION — awaken the runes you need
Aether::ether()::essence()::entity();
Whisper::ether()::essence()::entity();
Weaver::ether()::essence()::entity();
Chanter::ether()::essence()::entity();
Forger::ether()::essence()::entity();

// INCANTATION
Aether::begin();
Chanter::begin();

// ... register casts here ...

Chanter::end();   // parse argv, dispatch
Aether::end();    // version footer + exit
```

## Registering a cast

```php
Chanter::cast(
  arg: 'greet --loud --name',     // cast name is "greet"; --loud/--name document its spells
  echo: 'Greet someone, optionally loudly.',
  execute: function () {
    $loud = (bool) Chanter::spell('loud');        // --loud  → true/false
    $name = Chanter::spell('name') ?: 'world';     // --name= → value, else false
    $text = $loud ? strtoupper("hello $name") : "hello $name";
    Whisper::echo("{{color-success}}{{icon-success}} {$text}{{color-end}}{{nl}}");
  }
);
```

Run it:

```bash
php cast greet
php cast greet --loud --name=Anwar
```

- **Cast name** = the non-`--` words in `arg` (here, `greet`).
- **Spells**: `--flag` → `true`; `--key=value` → `"value"`; absent → `false`. Read with `Chanter::spell('key')`.
- **Echo**: the `echo:` note shows in the base `php cast` listing.

## Output styling (Whisper)

`Whisper::echo()` understands style tokens, applied to that message only:

```php
Whisper::echo("{{color-info}}{{icon-info}} building…{{color-end}}{{nl}}");
Whisper::echo("{{color-warning}}{{icon-warning}} careful{{color-end}}{{nl}}");
```

Colors: `primary secondary success warning info failed danger error debug end`.
Vars: `{{nl}}` (newline), `{{tab}}`, `{{bold}}`, `{{php}}` (the php binary name).
Icons: `{{icon-success}}` → `[√]`, `{{icon-failed}}` → `[x]`, `{{icon-info}}` → `[i]`, `{{icon-warning}}` → `[!]`.

Input: `$answer = Whisper::call("Your name? ");`

## Files (Forger)

```php
foreach (Forger::scan($dir) as $e) {
  if (is_dir($e['target'])) continue;           // $e is pathinfo + 'target'
  // $e['basename'], $e['filename'], $e['extension']
}
Forger::item($path, $contents);   // write (dir must exist); omit $contents to read
Forger::repo($dir);               // ensure a directory exists
```

## Built-in casts (from `@bindrune/chanter`)

- `php cast` — base entrance: stats, registered casts, version footer.
- `php cast grimoire [--rune=<Name> | --rune-all | --arcane]` — live system inspection.
- `php cast artefact --invoke` — seal the runite into a `.rune`; `--revoke=<file>.rune` restores it.
- `php cast sentinel --invoke=<Rune> | --revoke=<Rune> | --create-rune=<name> | --phantasm-fix=<Rune>` — manage runes in the runite.

## A real, non-trivial example in this org

`.github/runite-app/cast` registers `design`, `design-scan`, `design-user` — casts that scan the `design/` gallery, generate missing collection READMEs (via Forger + string templates), and rebuild the index. It awakens Aether, Whisper, Weaver, Chanter, **and Forger**. See [../org-github/runite-app.md](../org-github/runite-app.md) for the full breakdown.
