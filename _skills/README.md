# Skills

This directory will be synchronized from `jwineland/corpus-skills` when that repository is created.

Currently empty. Do not add skills directly here — they should be authored in `corpus-skills` and synced via GitHub Action.

## Planned sync mechanism

A GitHub Action in this repo will run on push to `corpus-skills:main` and open a PR here with updated skill files. The PR follows the standard review process before merge.

## Skills expected here

- `corpus-init-skill.md` — initialize a governed document corpus
- `challenge-loop-skill.md` — cross-platform structured review cycle
- `drift-check-skill.md` — manifest-based drift detection
- `publish-review-bundle-skill.md` — audience-specific review bundle creation
- `forge-excavation-skill.md` — concept excavation from a conversation (to be designed)
