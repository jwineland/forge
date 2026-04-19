---
id: capability-trials
name: Capability Trials
status: formalized
citation: forge:chatgpt-ai-tool-broker-capability-engineering:trial-design:exchange-11
created: 2026-04-19
depends-on: [capability-engineering-framework, world-specification]
related-to: [evaluation-trust-plane, actionable-intent-verses, bom-binding-locked-composition]
promoted-into: []
---

## Summary

A capability trial is a formal challenge of a capability against a world specification. It is broader than a test case — it encompasses behavioral, adversarial, functional, and operational challenge types, each designed to surface different kinds of failure. Capability trials are first-class engineering artifacts, not afterthoughts.

## Detail

### Why "trial" not "test"

"Testing" is too small and too code-centric. A trial implies:
- The capability is being challenged against a real standard
- The outcome is meaningful, not just pass/fail on an implementation detail
- The process is formal and produces evidence
- The evidence can drive refinement of the capability, the world, or the invariants

### Trial Pack structure

Trials are organized into packs by challenge type:

**Normal Operation pack**
- Happy path execution
- Expected operator use
- Standard system inputs
- Nominal performance characteristics

**Adversarial Inputs pack**
- Malformed payloads
- Unexpected user actions
- Conflicting records
- Ambiguous state
- Security boundary probes

**Operational Degradation pack**
- Stale dependencies
- Unavailable services
- Partial completion
- Timeout/retry behavior
- Degraded infrastructure conditions

**Human Reality pack**
- Operator confusion
- Skipped steps
- Manual overrides
- Conflicting mental models
- Workflow interruptions

### Three evaluation classes within trials

**Deterministic gates** — run first, before any judgment-based evaluation
- Tests passed, schema valid, compile succeeded, lint clean
- These are hard gates, not scored

**Structured semantic validation** — constrained evaluators with explicit criteria
- Does implementation match design intent?
- Does behavior align with invariants?
- Are trust boundaries respected?

**Subjective/strategic judgment** — panel-style, never single-judge
- Is this elegant enough to maintain?
- Is this architecture likely to scale?
- Is this operator experience acceptable?

### Evidence objects

Each trial run produces an evidence object containing:
- Structured result records
- Logs and outputs
- Operator notes
- AI analysis
- Pass/fail per invariant
- Detected ambiguity
- Unexpected behavior observations
- Confidence and uncertainty estimates

### What a failed trial means

A failed trial does not necessarily mean "the code is wrong." It may mean:
- The world model was incomplete (world drift)
- The capability spec was underspecified (design drift)
- The expected behavior was naive (intent drift)
- The trial exposed a genuine new requirement

Each of these has a different Refinement path. The trial evidence should be specific enough to distinguish between them.

### Relationship to BOM-binding

For manufacturing use cases, trials are run at first article build and their results are part of the locked composition. The evidence objects from trials become part of the birth certificate. Future builds of the same BOM can be validated against the same trial pack to confirm consistent behavior.

## Open questions

- How trial packs are defined and versioned in the corpus
- How AI participates in trial design and execution vs. only in result analysis
- Automation path for deterministic gates vs. human involvement for judgment-based trials
- How trial results feed back into world specification refinement

## Promotion candidates

Core object in the capability engineering framework. Critical for the manufacturing corpus template. Should be part of the Operationalization stage design alongside world specification.
