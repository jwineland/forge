---
id: intent-as-semantic-contract
name: Intent as Semantic Contract
status: formalized
citation: forge:2026-04-18-claude-general-docs:semantic-graph-intent:intent-abstraction
created: 2026-04-18
depends-on: [semantic-graph-foundation]
related-to: [bom-binding-locked-composition, boundarymark-fitness-attestation, output-materialization]
promoted-into: []
---

## Summary

Intent is a declarative specification of what something is for, at a level of abstraction above how it is implemented. Intent is stable when implementation changes. It separates into three distinct layers that change at different rates: semantic intent, content contract, and format resolution.

## Detail

The three layers:

**Semantic intent** — what this output is for and who it serves. "Executive presentation" carries meaning about audience, purpose, and content selection rules. Human-meaningful and stable for the life of a project type. Does not know or care about file formats.

**Content contract** — what a given intent includes and excludes. Defined once in the intent registry. Changes slowly as the corpus matures. Owned by the intent definition, not by individual projects.

**Format resolution** — how the intent materializes into an actual artifact. Marp, PPTX, reveal.js, PDF. Entirely a deployment concern driven by adapter configuration. Can change any time without affecting intent or content contract.

The CSS analogy: HTML declares semantic meaning; CSS resolves how it renders. The intent system is the same pattern applied to document systems.

Intent names come from a shared registry — they are not invented per-project. A project declares which intents it needs; the registry defines what those intents mean; the adapter layer resolves format.

Intent declarations also drive the challenge loop: if content intent declares the decision being supported and the primary audience, the review skill can select the appropriate adversarial persona automatically.

Intent also enables fitness attestation: a verification layer can check not just provenance but whether an artifact contains the elements required by its declared intent for its declared audience.

## Open questions

- The intent registry is a stub — full design needed before this concept is implementable
- Relationship to BoundaryMark fitness attestation needs formal specification
- How intent declarations interact with the JSON-LD graph needs vocabulary design

## Promotion candidates

Candidate for `_vocabulary/intent-registry.md` once that design session occurs. Candidate for `corpus-seed.yaml` schema in corpus template repos.
