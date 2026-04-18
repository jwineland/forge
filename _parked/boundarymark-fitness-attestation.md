---
id: boundarymark-fitness-attestation
name: BoundaryMark Fitness Attestation
status: parked
citation: forge:2026-04-18-claude-general-docs:semantic-graph-intent:attestation-discussion
created: 2026-04-18
park-trigger: When BoundaryMark design work resumes — this concept extends the rack birth certificate architecture into the content domain
park-reason: Depends on stable semantic graph vocabulary and intent registry; BoundaryMark work is currently in a separate design track
decay-policy: manual-only
depends-on: [intent-as-semantic-contract, semantic-graph-foundation, bom-binding-locked-composition]
related-to: []
---

## Summary

Fitness attestation extends BoundaryMark provenance attestation into a new category: not just "I can prove this document came from this source" but "I can prove this document is what it claims to be for its declared audience and intent." A verification layer checks whether an artifact contains the required elements for its declared intent and suppresses what should be excluded.

## What needs to be designed

- Formal definition of fitness attestation vs. provenance attestation
- How intent declarations in JSON-LD map to SCITT receipt structure
- How content hash of a locked composition becomes a VC credential subject
- Integration point with existing W3C VC/DID work in BoundaryMark
- Attestation schema for fitness claims

## Prior context

The key insight from the design session: attesting a locked composition is attesting a specific subgraph snapshot, which is a well-defined cryptographic operation. The content hash that locks a module version to a BOM is the same primitive as a VC credential subject. JSON-LD alignment between Forge and BoundaryMark enables direct embedding of content graph references in VCs.
