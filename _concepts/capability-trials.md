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

### Spec-first principle

Trials are authored *before* the execution agent is dispatched, not after. This is a named workflow invariant, not a guideline.

The failure mode of spec-after-the-fact is the **self-confirming loop**: an execution agent generates implementation and then generates tests from the same context. The tests confirm the agent's interpretation of requirements, not the human's intent. Tests can pass while the capability is wrong.

When a human-authored trial pack pre-exists, the agent's instruction becomes "make all trials in this pack pass" — the trial pack is the source of truth, not the implementation. A failed trial may mean the world model was incomplete or the capability spec was underspecified, not necessarily that the code is wrong. But a passing trial against a human-approved pack is meaningful evidence; a passing test against an AI-generated test suite is not.

This principle applies equally to human developers and execution drones. A trial pack must be human-authored or human-reviewed before dispatch. In a Forge drone workflow, a human-approved trial pack is a required gate before a handoff drone dispatches to an execution agent.

### Boundary vs. internal trials

**Boundary trials** exercise the capability at its external interfaces with realistic inputs and outputs. They do not mock internal collaborators. A boundary trial for an API endpoint provides a realistic HTTP payload and asserts on the realistic HTTP response — everything in between is the capability doing its job.

Boundary trials are the most valuable trial type because they:
- Catch integration failures that internal trials miss
- Remain valid even as internal implementation changes
- Are legible to non-implementers — human authorities can read and approve them without understanding internals

For drone capabilities specifically: a boundary trial for an index drone takes a realistic repo state as input and asserts on the resulting index artifact — not on internal parsing decisions. A boundary trial for a handoff drone takes a rationalized design decision as input and asserts on a valid, human-reviewable trial pack as output.

**Internal trials** verify isolated logic, edge cases in specific functions, or implementation constraints that do not surface at the boundary. Useful for implementation confidence, but should not be the primary validation surface for capability correctness.

General rule: prefer boundary trials for capability correctness; use internal trials for implementation confidence.

### Trial expression format

A trial pack needs a format that is simultaneously human-readable and machine-executable. This parallels the Narrative View / Intent View split in `actionable-intent-verses`.

Given/When/Then (Gherkin, as formalized in BDD) is a strong candidate expression format:

```gherkin
Feature: Index drone produces valid concept index

  Scenario: Fresh repo with three concept files
    Given a repo containing three formalized concept files
    When the index drone runs
    Then the output index contains exactly three entries
    And each entry has a stable concept ID and citation

  Scenario: Repo contains a concept with missing citation
    Given a repo containing one concept file with no citation field
    When the index drone runs
    Then the output index flags the entry as citation-incomplete
    And the drone does not fail or skip the entry
```

The `Given` clause maps to a world specification state instance. The `When` clause maps to a capability invocation. The `Then` clause maps to an invariant assertion.

This format produces trial packs that are reviewable by humans (including on mobile), executable by a test runner, and structured enough for drones to validate. The narrative layer (what the scenario is for) is the Narrative View; the step definitions that implement it are the Intent View — matching the `actionable-intent-verses` split exactly.

The trial expression format should be decided before the first trial pack schema is designed.

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
- **Trial expression format:** Should Gherkin (Given/When/Then) be adopted as the canonical trial pack expression syntax? This connects directly to `actionable-intent-verses` (Narrative/Intent split) and determines tooling choices. Should be resolved before the first trial pack schema is designed.
- **Spec-first enforcement:** How should the spec-first principle be enforced as a Forge workflow gate? Should a human-approved trial pack be a required artifact before a handoff drone can dispatch to an execution agent?
- **Boundary vs. internal trial ratio:** What is the recommended balance between boundary trials and internal trials for different capability types — drones, APIs, orchestration surfaces?

## Promotion candidates

Core object in the capability engineering framework. Critical for the manufacturing corpus template. Should be part of the Operationalization stage design alongside world specification.
