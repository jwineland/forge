# Intent Registry

**Status: STUB — requires dedicated design session**

This file will define the canonical named intent types used across all Forge-governed corpora. Each intent type specifies the semantic contract (audience, purpose, content selection rules, style parameters) independently of format resolution.

Format resolution — which output format a given intent materializes into — is handled by the adapter layer and is not defined here.

## Design session required

The intent registry is a parked concept (see `_parked/intent-registry-design.md`). It should be designed before the `corpus-template-doc` and `corpus-template-eng` repos are created, as both depend on the intent vocabulary.

## Known intent types (preliminary, unformalized)

The following have been identified in design discussions but not yet formally specified:

- `executive-presentation` — decision-oriented, minimal detail, slide-forward, suppresses governance content
- `functional-review` — operational detail, explicit feedback prompts, phase-by-phase
- `working-session` — synchronous discussion, short notes, interaction-driven
- `technical-brief` — dense, methodology-forward, includes validation details
- `regulatory-record` — complete, append-only presentation, nothing suppressed

## Citation

`forge:2026-04-18-claude-general-docs:semantic-graph-intent:intent-abstraction`
