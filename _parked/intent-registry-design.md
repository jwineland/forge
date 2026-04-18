---
id: intent-registry-design
name: Intent Registry Design
status: parked
citation: forge:2026-04-18-claude-general-docs:semantic-graph-intent:intent-abstraction
created: 2026-04-18
park-trigger: When Forge schema design session begins — this is a blocking dependency for corpus-template-doc and corpus-template-eng
park-reason: Intent as semantic contract is formalized but the registry of named intent types requires a dedicated design session before it can be specified
decay-policy: review-at-90-days
depends-on: [intent-as-semantic-contract]
related-to: [corpus-lifecycle-system, semantic-graph-foundation]
---

## Summary

The intent registry defines the canonical named intent types — executive-presentation, functional-review, working-session, technical-brief, regulatory-record — with their content contracts, audience definitions, and style parameters. Format resolution is handled by adapters and is not part of the registry definition.

## What needs to be designed

- Formal specification of each named intent type
- Content contract per intent: what is included, what is excluded
- Audience definition per intent
- Style parameters per intent (density, structure, interactivity)
- How intent declarations are expressed in corpus-seed.yaml
- How the intent registry is stored and versioned in `_vocabulary/`
- How intent names map to format adapters

## Prior context

Preliminary intent type list from design session:
- `executive-presentation` — decision-oriented, minimal detail, slide-forward, governance suppressed
- `functional-review` — operational detail, explicit feedback prompts, phase-by-phase
- `working-session` — synchronous discussion, short notes, interaction-driven
- `technical-brief` — dense, methodology-forward, validation details included
- `regulatory-record` — complete, append-only, nothing suppressed

See `_vocabulary/intent-registry.md` for the stub.
