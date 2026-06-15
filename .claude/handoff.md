# beautify — Session Handoff

_Last updated: 2026-06-15_

## What beautify is
A standalone Claude Code plugin packaging a frontend design methodology — a single prose skill that guides building distinctive, production-grade UI (anti "AI slop"). It is **knowledge/methodology**, not executable tooling.

- Skill: `skills/using-beautify/SKILL.md` (activates as `/beautify:using-beautify`)
- Manifests: `plugin.json` (root) + `.claude-plugin/marketplace.json`
- Attribution: `README.md` + `NOTICE`

## Provenance
- Core design-thinking/aesthetics prose: derived from Anthropic's `frontend-design` plugin (already byte-identical to upstream v1.0.0 — nothing new to pull there).
- Most other sections: distilled from **[pbakaus/impeccable](https://github.com/pbakaus/impeccable)** (Apache-2.0). Apache-2.0 attribution is satisfied via `NOTICE`.

## Work completed (this thread)
1. Verified `frontend-design` upstream is current (v1.0.0, 0 commits behind) — no update available.
2. Absorbed impeccable's transferable **design knowledge** into the skill across these sections (build-to-ship order):
   Design Thinking → Committing to a Direction → Frontend Aesthetics → Concrete Design Rules → Calibrating Intensity → Anti-Patterns → Production Craft Bar → Performance Floor → Critique Pass → Visual Verification (Browsify).
3. Converted beautify into a **standalone installable plugin** (added `.claude-plugin/marketplace.json`, matching memofy's structure).
4. Expanded `NOTICE` + `README` attribution.

Key commits on `main`: `5082cda` (concrete rules + anti-patterns), `788c19d` (standalone plugin + critique pass), `54d086b` (direction/calibration/craft/perf).

## Deliberately NOT absorbed
impeccable's **machinery** — its 23 slash-commands, the anti-pattern detector CLI, the live browser-edit server, hooks, and the `init`/AGENTS.md discovery flow. That is executable tooling (a *build*, not a *distill*) and conflicts with beautify's single-file philosophy. The knowledge those tools encode is already captured in the prose.

## Install / refresh
```bash
# Standalone plugin (preferred)
claude plugin marketplace add jedcanlas/beautify
claude plugin install beautify@beautify
claude plugin update beautify

# Or vendored by jedi
jedi update
```

## Future pickup options (not yet done)
- **Smoke-test the install.** I validated the JSON manifests but never ran `claude plugin marketplace add jedcanlas/beautify` end-to-end. Confirm it appears in `claude plugin list` and the skill activates.
- **Port the executable machinery** if wanted — biggest candidates, each its own project:
  - the **anti-pattern detector** (impeccable `scripts/detector/`) as a hook or CLI that flags side-tab borders, icon-tiles, flat hierarchy, low contrast on edit/save.
  - the **live browser-edit** loop, or lean on the existing `browser-harness`/`browsify` instead.
- **Re-sync impeccable periodically.** It's actively developed. To diff for new design knowledge:
  `git clone --depth 1 https://github.com/pbakaus/impeccable /tmp/imp &&` review `.agents/skills/impeccable/reference/*.md` against current SKILL sections.
- **Trim if it bloats.** The skill is ~200 lines; if it grows further, consider splitting into a prose SKILL + a `reference/` folder (the multi-file option previously declined in favor of single-file minimalism).
