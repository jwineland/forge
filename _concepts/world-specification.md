---
id: world-specification
name: World Specification
status: formalized
citation: forge:chatgpt-ai-tool-broker-capability-engineering:world-model:exchange-10
created: 2026-04-19
depends-on: [capability-engineering-framework]
related-to: [intent-as-semantic-contract, capability-trials, bom-binding-locked-composition]
promoted-into: []
---

## Summary

A formal description of the environment in which a capability must operate. Systems fail not only because their logic is wrong, but because their assumptions about the world are wrong. The world specification makes those assumptions explicit, versioned, and challengeable — and is a first-class engineering artifact, not optional documentation.

## Detail

### Why world specification is underspecified by default

Most engineering methodologies assume the requirements are "the truth" and testing merely checks implementation fidelity. But there are three independently drifting things:

1. **Intended system behavior** — what we think we want
2. **Implemented system behavior** — what the system actually does
3. **Real-world environmental behavior** — what the world/users/operators/inputs/tools actually do

If you don't model the third explicitly, the AI/tooling stack will invent a world model for you. That is a bad trade.

### What a world specification contains

**Entities** — users, operators, services, devices, files, assets, workflows, approvals, external systems

**State** — what can exist, what states are valid, what transitions are allowed, what partial or degraded states are possible

**Environmental conditions** — latency, outages, stale data, conflicting inputs, missing permissions, race conditions, human error, partial completion, malicious or confused actors

**Semantics** — what things mean, what counts as success/failure, what ambiguity is allowed, what context changes interpretation

**Constraints** — business rules, safety rules, legal/compliance rules, operational boundaries, temporal rules, trust boundaries

### MVP scope

A world object does not need to be an elaborate simulation engine at MVP. It needs to let you say:
- Who exists
- What states exist
- What can go wrong
- What environmental conditions matter
- What assumptions are currently believed

Even a lightweight initial world model is better than none. The world model can be refined as trials reveal gaps.

### Relationship to the three drifts

The world specification closes the gap between intent and reality by making the environmental assumptions explicit. When a trial fails, you can now ask: was the failure due to:
- Incorrect implementation (implementation drift)?
- Incorrect specification of intended behavior (design drift)?
- Incorrect assumption about the world (world drift)?

Each of these has a different remediation path.

### Relationship to Forge stages

World definition is a cross-stage construct — it can appear during qualification, rationalization, formalization, and operationalization. It is not only a late-stage concern. During concept development, asking "what world does this concept assume?" is one of the most powerful ways to surface hidden constraints and test conceptual soundness.

### Named world types (preliminary)

From the manufacturing use case:
- "Manufacturing line world" — specific hardware, operators, assembly steps, QC gates
- "Customer-facing service request world" — users, SLAs, support tiers, escalation paths

World types can be reused across capabilities. A shared world spec reduces duplication and ensures consistent environmental assumptions.

## Open questions

- How world specifications are versioned and linked to the capabilities that depend on them
- How world drift is detected when the real environment evolves (new actor types, new failure modes)
- Whether world specifications should be formal enough for machine validation or remain human-readable design artifacts

## Promotion candidates

Core object in the capability engineering framework. Candidate for the manufacturing corpus template. Should be referenced in the Operationalization stage design.
