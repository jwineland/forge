---
id: capability-engineering-framework
name: Capability Engineering Framework
status: formalized
citation: forge:chatgpt-ai-tool-broker-capability-engineering:framework-definition:exchange-8
created: 2026-04-19
depends-on: [semantic-graph-foundation, concept-capability-stratification]
related-to: [world-specification, capability-trials, actionable-intent-verses, bom-binding-locked-composition]
promoted-into: []
---

## Summary

Capability Engineering is the discipline of designing and governing systems by proving behavioral reliability in modeled worlds, rather than by reviewing implementation code. As AI increasingly generates and operates implementation, the engineering center shifts from code authorship to capability definition, world modeling, invariant specification, and trial-based validation.

## Detail

### The core proposition

Historically, software engineering treated implementation review as the primary truth surface. As AI-generated and AI-operated systems become more common, this breaks down:

- You cannot realistically say "I understand the system because I reviewed the implementation" when implementation is AI-generated
- The primary questions become: what can this system do? Under what conditions? How does it fail? What invariants must hold?
- Testing is no longer the tail end — it becomes the primary truth surface

### The six primary objects

**1. Capability**
The thing the system is intended to reliably do. A Capability answers: what is the outcome? Who/what uses it? What actions does it allow? What are its boundaries? What are its trust assumptions? What are its success/failure conditions?

**2. World**
The modeled environment the capability operates in. Defines: actors, entities, system states, constraints, trust boundaries, failure conditions, domain semantics. (See `world-specification` concept for full detail.)

**3. Invariant**
What must remain true no matter what. Examples: "A user must never see another tenant's asset." "An operator override must always be attributable." These are the spine of capability engineering — human oversight of what must remain true, not of every line of how it is achieved.

**4. Trial**
A formal challenge against a capability in a world. Not just a test case — a Capability Trial can include happy-path scenarios, adversarial probes, policy boundary tests, operator misuse, degraded infrastructure conditions, concurrency failures, chaos/resilience exercises.

**5. Evidence**
What happened when the trial was run. Logs, structured result records, operator notes, AI observations, pass/fail against invariants, detected ambiguity, unexpected behavior.

**6. Refinement**
A structured change prompted by observed divergence. Can target the capability spec, world model, invariants, implementation, or evaluation logic. A failed trial does not always mean "the code is wrong" — it may mean the world model was incomplete or the authority spec was underspecified.

### The engineering lifecycle

1. Define intended capabilities
2. Define the world in which they must operate
3. Define invariants and unacceptable behaviors
4. Generate or implement candidate solutions
5. Run capability trials
6. Observe divergence between intended and actual behavior
7. Refine the world model, authority spec, or implementation
8. Repeat

This replaces: "write code → write tests → ship → regret."

### Relationship to Forge

The ChatGPT Forge design session explicitly identified that Forge has the bones of an MVP capability engineering platform. The stage progression (Excavation → Qualification → Rationalization → Promotion → Formalization → Operationalization) maps onto the capability engineering lifecycle. Operationalization is where concepts become capabilities with worlds, invariants, and trials.

Forge's concept engineering layer feeds the capability engineering layer. The two-stratum model (see `concept-capability-stratification`) defines the boundary and promotion path between them.

### Three evaluation classes

**Deterministic validation** — use tools, not judges. Tests passed, schema valid, code compiles, formatting correct. Hard gates.

**Structured semantic validation** — constrained evaluators. Does implementation match design? Does ADR contradict prior ADRs?

**Subjective/strategic judgment** — panel-style judging and escalation. Never single-judge/single-score for these.

## Open questions

- How capability maturity levels (Draft → Defined → Trialed → Adversarially challenged → Operator validated → Production credible) are tracked
- Integration path between Forge concept registry and a capability registry
- Whether capability engineering tooling is a separate system or an extension of Forge

## Promotion candidates

High-value candidate for a capability engineering specification document. Core to the Forge Compose / manufacturing template work. Should inform the Operationalization stage design.
