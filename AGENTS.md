# AI Software Factory — demo target

This repository is a **disposable target** operated by an AI Software Factory. It is seeded from the control repo's `template/` and may be destroyed and recreated at any time.

## Contract with the factory

- The factory reads **labels** to decide what to do next. Do not rename labels; the vocabulary is a migration surface.
- Phases are read from labels and issue state. See `GLOSSARY.md`.
- The frontend deploys to GitHub Pages via `.github/workflows/deploy.yml` when `factory:deploy` is present on merged work.

## Label vocabulary

| Namespace | Purpose |
|---|---|
| triage roles (`ready-for-agent`, …) | current **state** |
| `factory:*` | **command** the factory should take |
| `wayfinder:*` | reserved for decision maps — not used here |

## Working here

Read `GLOSSARY.md` before naming anything. Skills used by the factory are installed under `.claude/skills/` and are loaded by `opencode`, which drives a model served by Ollama.

**`opencode.json` must exist in this repo.** It pins the provider to the local Ollama endpoint; without it, `opencode` inherits the operator's global config and may hang against an unreachable machine.
