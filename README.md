# beautify

Frontend design methodology for jedi — produces distinctive, production-grade UI.

Derived from the [frontend-design](https://github.com/anthropics/claude-code-plugins) Claude Code plugin, evolved locally for personal use. The "Concrete Design Rules" and "Anti-Patterns" sections distill principles from [pbakaus/impeccable](https://github.com/pbakaus/impeccable) (Apache-2.0) — see [NOTICE](NOTICE).

## What it provides

- `skills/using-beautify/SKILL.md` — design principles, component patterns, token philosophy, browsify visual verification workflow

## Installation

### As a standalone Claude Code plugin (recommended)

beautify is a self-contained plugin (`plugin.json` + `skills/` + `.claude-plugin/marketplace.json`), installable the same way as any other:

```bash
claude plugin marketplace add jedcanlas/beautify
claude plugin install beautify@beautify
```

The skill then activates as `/beautify:using-beautify` (and auto-loads when you build any UI). Run `claude plugin update beautify` to refresh.

### Vendored by jedi

```bash
jedi init      # installs beautify into .jedi/tools/beautify/
jedi update    # refreshes beautify from this repo
```

Once vendored, the jedi Frontend Designer agent reads beautify methodology automatically.

## Development

This is a personal tool — edit `skills/using-beautify/SKILL.md` directly to evolve your design methodology.
