# Rune — Architecture

## The triad: Ether, Essence, Entity

Every rune expresses itself through three parts, awakened only when needed:

| Part | Meaning | Holds |
|---|---|---|
| **Ether** | truth that never changes but always has meaning | constants, configuration, definitions |
| **Essence** | what changes over time | state, flow, in-memory data |
| **Entity** | what makes other things change | behaviour / logic (procedural functions) |

An entity may call the entities of **other** runes — that is how runes cooperate. (Law: "Entity holds the logic.")

## Manifest — the engraving surface

`Rune\Manifest` is the base class each rune's `Manifest` extends. It exposes `ether()`, `essence()`, `entity()` which `require_once` the matching file and register the rune globally. A runite never calls entity functions directly; it speaks through the Manifest:

```php
use Rune\Aether\Manifest as Aether;
Aether::ether()::essence()::entity();   // awaken Aether fully
```

Laws: "Manifest is for engraving — it only forwards to entities."

### How a Manifest looks (simplified, from `Rune\Manifest`)

```php
class Manifest {
  protected static $origin = __DIR__;
  public static function entity()  { require_once static::$origin."/Entity.php";  /* register */ return static::class; }
  public static function essence() { require_once static::$origin."/Essence.php"; /* register */ return static::class; }
  public static function ether()   { require_once static::$origin."/Ether.php";   /* register */ return static::class; }
}
```

Each origin rune's `Manifest` extends this and adds domain methods (e.g. `Chanter::cast()`, `Whisper::echo()`, `Forger::scan()`), plus lifecycle hooks: `begin()`, `end()`, `_arise()`, `_aether_end()`.

## Phantasm — the living contract (replaces Reflection)

Instead of PHP Reflection, each rune carries a **Phantasm** describing itself: `version`, `user`, `note`, `mark`, `link`, `node`. The Grimoire reads Phantasms to document the system live. Law: "Every change raises the Phantasm version of the rune that changed."

## Aether — the flow beneath everything

`Aether` is special: it flows through all runes. It provides paths, a stopwatch, memory usage, the **arcane** log, exit handling, and the version footer. Nearly every entity function ends by calling `aether_arcane("...")` to record a step in the process log.

- `Aether::begin()` — cleans memory, resets arcane; opens the flow.
- `Aether::end()` / `Aether::exit()` — closes the flow and prints the version footer, then exits.
- `Aether::dd($data)` — dump and stop.

Law: "Aether flows everywhere; runes are not standalone packages — they awaken together inside one flow."

## The flow of a run (the `cast` file)

```
require vendor/autoload.php
│
├─ INVOCATION   use ...\Manifest; Manifest::ether()::essence()::entity();  (awaken runes)
│
├─ INCANTATION  Aether::begin(); Chanter::begin();
│                 ... register casts / main logic ...
│               Chanter::end();   (parses argv, dispatches the matching cast)
│               Aether::end();    (version footer + exit)
```

- `Chanter::begin()` loads built-in casts from `@bindrune/chanter/*` (the `rune`, `grimoire`, `artefact`, `sentinel` commands).
- `Chanter::end()` extracts argv into a cast name + spells, finds the registered cast, and runs it. With `--zero-trust` it runs guarded (arcane disabled).

## Global state

Rune uses PHP globals deliberately (e.g. `$AETHER_RUNE_ENTITY`, `$CHANTER_CAST`, `$WHISPER_DRAIN_STATE`). This is part of the process-based, no-container design — the "flow" is shared global state coordinated by Aether. When extending Rune, follow the same pattern rather than introducing a DI container.

## Versioning

The footer shows `Version=major.sum`:
- `major` = the core's major version.
- `sum` = the sum of every Phantasm version (origin runes, plus liberation runes in liberation mode).

So the number grows as the runes grow (e.g. `1.20.114`). This is automatic minor/patch versioning.
