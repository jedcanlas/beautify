# beautify

Frontend design methodology for jedi — produces distinctive, production-grade UI.

Derived from the [frontend-design](https://github.com/anthropics/claude-code-plugins) Claude Code plugin, evolved locally for personal use. The "Concrete Design Rules" and "Anti-Patterns" sections distill principles from [pbakaus/impeccable](https://github.com/pbakaus/impeccable) (Apache-2.0) — see [NOTICE](NOTICE).

## What it provides

- `skills/using-beautify/SKILL.md` — design principles, component patterns, token philosophy, browsify visual verification workflow

## Installation

Vendored automatically by jedi:

```bash
jedi init      # installs beautify into .jedi/tools/beautify/
jedi update    # refreshes beautify from this repo
```

## Usage

Once vendored, the jedi Frontend Designer agent reads beautify methodology automatically. To replace the `frontend-design` Claude Code plugin with beautify in your Claude Code session, add beautify as a local skill:

```bash
# In Claude Code settings, add the skill path:
# E:/PROJECTS/beautify/skills/
```

## Development

This is a personal tool — edit `skills/using-beautify/SKILL.md` directly to evolve your design methodology.
