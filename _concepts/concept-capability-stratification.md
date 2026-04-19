---
id: concept-capability-stratification
name: Concept/Capability Stratification
status: formalized
citation: forge:chatgpt-ai-tool-broker-capability-engineering:two-stratum-model:exchange-15
created: 2026-04-19
depends-on: [forge-concept-lifecycle, capability-engineering-framework]
related-to: [stage-aware-guided-advancement, forge-guidance-engine]
promoted-into: []
---

## Summary

Forge operates across two interacting strata with different formality requirements and a deliberate promotion path between them. The Concept Engineering stratum is exploratory and loosely structured. The Capability Engineering stratum is formal, bounded, and challengeable. Neither replaces the other; both are needed.

## Detail

### Why two strata

Collapsing concept work and capability work creates two failure modes:

**Too early formalization** — forcing every idea into capability form before it is ready loses the creative and architectural discovery value of exploratory concept work.

**Too loose formalization** — keeping everything in the concept layer without ever promoting into capability form produces idea cemeteries, pattern catalogs nobody operationalizes, and architectural speculation without challenge.

The solution is explicit stratification with a defined promotion path.

### Stratum 1: Concept Engineering

For: ideas, patterns, terminology, questions, tensions, hypotheses, comparisons, architectural notes

Characteristics:
- Exploratory
- Partially ambiguous
- Multiple framings in play
- Not yet testable
- May remain as reusable pattern or vocabulary rather than operational artifact

Formality: structured enough to be tagged, linked, and retrieved — but not required to have bounded scope, invariants, or trial definitions

### Stratum 2: Capability Engineering

For: capabilities, world models, invariants, trials, evidence, refinements

Characteristics:
- Bounded and intentional
- Situated in a modeled world
- Testable and challengeable
- Governed by evidence
- Refinable through trial outcomes

Formality: requires explicit scope, world assumptions, invariants, and trial definitions before being treated as engineering-grade

### The promotion path

A concept is ready for promotion to the capability stratum when:
- It describes something the system should reliably do
- It depends on assumptions about the world
- Failure matters operationally
- Invariants can be stated
- Trials can be defined
- Evidence can be gathered

A concept should remain in the concept stratum when:
- It is still ambiguous
- Multiple framings are in play
- It is useful but not yet testable
- It informs design without describing intended system behavior
- It may remain a reusable pattern or term rather than an operational artifact

### Maturity flow

```
Note
  → Concept
    → Pattern
      → Candidate construct
        → Capability candidate
          → Formal capability
            → Trialed capability
              → Operational capability
```

Not every concept needs to complete this path. Some remain as vocabulary, design principles, reference patterns, failure archetypes, reusable world fragments, or governance heuristics.

### Bridge objects

The connection between strata requires explicit bridge objects:
- **Promotion record** — why this concept was promoted and to what
- **Derivation record** — which capability derived from which concept
- **Dependency link** — which capabilities depend on which concepts for their invariant or world definitions
- **Open assumption** — a concept-layer assumption that hasn't yet been formalized as a world specification

## Open questions

- Whether the Forge concept registry (`_concepts/`) and a future capability registry should be separate directories or unified with type fields
- How the promotion threshold is operationalized — who decides and on what basis?
- How bridge objects are represented in the current file-based system

## Promotion candidates

Core structural concept for Forge system design. Should be reflected in the Forge North Star and Canonical Concepts artifacts. Informs the Operationalization stage design.
