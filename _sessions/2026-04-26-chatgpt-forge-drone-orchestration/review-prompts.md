# Consolidated Review Prompts: Drone Orchestration, Atlas, Federation, and Cost Governance

**Document type:** Review orchestration index for multi-model and human challenge loops  
**Date:** 2026-04-26  
**Related session:** `2026-04-26-chatgpt-forge-drone-orchestration`  
**Purpose:** Consolidate review prompts scattered across the session capture so reviewers can evaluate the design as a coherent review packet.

---

## 1. How to Use This File

This file is a review orchestration index. It does not replace the underlying design notes. Reviewers should read the relevant source files, then answer one or more prompt groups below.

Primary source files:

- `excavation.md`
- `engineer-orientation.md`
- `global-coherence-map-note.md`
- `design-atlas-related-work-survey.md`
- `federated-graphs-and-project-local-forge.md`
- `cost-accounting-and-classification-retention.md`

Foundational concepts on main that inform this review:

- `_concepts/capability-engineering-framework.md`
- `_concepts/world-specification.md`
- `_concepts/capability-trials.md`
- `_concepts/actionable-intent-verses.md`

---

## Prompt A — Forge Identity and Architectural Fit

> Review the proposed Forge drone/worker orchestration layer. Does it fit Forge's stated identity as a semantic knowledge lifecycle system, or does it overextend Forge into general agent orchestration? Identify which parts belong in Forge Core, which parts belong in a downstream Forge Operations package, which parts belong in project-local `.forge/` layers, and which parts should remain parked.

Specific questions:

1. Is drone orchestration a natural extension of concept/design lifecycle management?
2. Should Forge Core only preserve/elevate meaning while Forge Operations performs dispatch?
3. What boundary prevents Forge from becoming a generic agent framework?
4. Which proposed drones are substrate maintenance vs. design judgment vs. execution agents?

---

## Prompt B — Concept Rationalization

> Compare the candidate concepts from this session against existing Forge concepts such as `human-ai-role-separation`, `challenge-loop-methodology`, `multi-model-deliberation-roles`, `forge-guidance-engine`, `evaluation-trust-plane`, `manifest-as-coherence-anchor`, and `semantic-graph-foundation`. Which concepts are genuinely new, which are refinements, and which are duplicate framings?

Specific rationalization tasks:

1. Resolve the boundary between `forge-housekeeping-workers` and `forge-drone-coordination-layer`. **Note:** both concepts carry explicit `rationalizationNote` flags in `index.jsonld` blocking promotion to Qualification until this boundary is resolved. This is a named pre-promotion gate, not merely an open question.
2. Confirm whether `human-as-message-bus` is a design pressure, anti-pattern, or concept.
3. Confirm whether `subscription-cognition-api-logistics` is the architectural response to `human-as-message-bus`. (An explicit `motivatedBy` link is recorded in `index.jsonld`.)
4. Determine whether `github-as-shared-state-substrate` is the correct concept name, given that the prior name `github-as-drone-message-bus` was semantically inverted. (Name rationale is recorded in `index.jsonld`.)
5. Determine whether `bounded-context-packet` and `design-packet-freeze` are distinct concepts or should be merged.

---

## Prompt C — Economic and Cost-Class Model

> Evaluate the proposed cost accounting and cost-class governance model. Does it preserve the original motivation of the session: understanding subscription-vs-API economics while designing a hybrid workflow that avoids uncontrolled frontier-model API spend?

Specific questions:

1. Are the four cost classes — Green, Yellow, Red, Black — sufficient?
2. Should subscription-surface work, API work, and local work have separate cost ledgers?
3. Should cost classes apply to drone jobs, design cycles, prompt dispatches, or all of them?
4. What approval gates are needed for Red and Black work?
5. What information must be logged to compare subscription usage to API-equivalent value?
6. Does the design retain the original session-based cost accounting model?
7. Should cost governance become a first-class Forge concept or remain an operational concern?

---

## Prompt D — Design Atlas / Global Coherence

> Review the Design Atlas proposal as a response to the loss of whole-authority-document global review after modularization. Is Atlas a distinct first-class artifact, a graph projection, a MANIFEST extension, a project-scoped guidance object, or a hybrid?

Specific questions:

1. What is the smallest useful Design Atlas?
2. What must be included to restore whole-design coherence checking?
3. What should be excluded from the minimum viable Atlas?
4. What is the relationship between Atlas and `manifest-as-coherence-anchor`?
5. What is the relationship between Atlas and `semantic-graph-foundation`?
6. Should Atlas be required before implementation planning?
7. How often should Atlas receive frontier-model challenge review?
8. How should Atlas represent uncertainty, disagreement, and unresolved tensions?

Note: completeness/coverage reporting is explicitly blocked on parked `completeness-scoring-methodology` and should not be treated as MVP-ready.

---

## Prompt E — Federation and Project-Local Forge Layers

> Review the proposed federated graph / project-local Forge model. How should the primary Forge registry relate to project-local graphs, manifests, atlases, implementation plans, prompt handoffs, and implementation evidence?

Specific questions:

1. Should every elevated project have a `.forge/` layer?
2. What is the minimal project-local Forge layer?
3. What is the authority chain among primary registry, project manifest, project Atlas, ADRs, plans, handoffs, and code?
4. Should project-local concepts be copied, referenced, projected, or instantiated?
5. How should divergence from a global concept be represented?
6. How should project learnings be promoted back into the primary registry?
7. Should project registry/import records be JSON-LD, YAML, or both with explicit authority rules?
8. Which project-local artifacts should be immutable, mutable, derived, or regeneratable?

---

## Prompt F — Prompt Generation and Dispatch

> Review prompt generation and dispatch as first-class Forge concerns. Does the design adequately address the user's role as human message bus across ChatGPT, Codex, Claude Code, GitHub, local files, and future tooling?

Specific questions:

1. What prompt/handoff artifacts should Forge preserve?
2. Should prompts be treated as `OutputArtifact`, `IntentDeclaration`, `Handoff`, or another type?
3. How should prompts preserve source concept/design lineage?
4. What dispatch mechanisms should be supported first: human copy/paste, GitHub issue/PR, committed handoff file, MCP, API job, or local runner?
5. How should Forge capture outputs from subscription UI surfaces that cannot be automated directly?
6. What dispatch metadata is required to verify that implementation matched intent?

---

## Prompt G — Local-First Drones and Escalation

> Assess the proposal to use local compute, including laptop CPU and future GB10-class resources, for housekeeping drones before escalating to API or subscription frontier models.

Specific questions:

1. Which drone tasks are safe for local models?
2. Which tasks require API utility models?
3. Which tasks require frontier reasoning?
4. What confidence and validation mechanisms are required?
5. How should local drone results be marked when low confidence?
6. What should trigger escalation from local → cheap API → standard API → subscription frontier → approved frontier API?

---

## Prompt H — MVP Scope

> Evaluate the proposed five-drone MVP: Index, Packet, Handoff, Verification, and Cost Governor. Is this the right minimal set to remove the user as human message bus for one design-to-implementation handoff workflow?

Specific questions:

1. Should Design Atlas maintenance be part of MVP, or deferred?
2. Should federation/import records be part of MVP, or deferred?
3. Is Cost Governor required from day one?
4. Can the MVP operate entirely through GitHub/file artifacts before runtime drones exist?
5. What is the first workflow that proves value without overbuilding?
6. What should be explicitly out of scope?

---

## Prompt I — Drift, Trust, and Evaluation

> Propose a rubric for reviewing Atlas/project-local Forge state for global design coherence and implementation drift.

Specific questions:

1. What kinds of drift matter most?
2. What evidence should be required before declaring a design coherent?
3. What drift should block implementation planning?
4. What drift should merely create a warning?
5. Should multi-model disagreement be treated as evidence of risk?
6. Which evaluation rubrics belong in `evaluation-trust-plane` vs. Atlas-specific review?

---

## Prompt J — Merge and Follow-Up Strategy

> Assess whether this PR should merge as design-capture baseline, remain draft pending additional model review, or be split into follow-up PRs.

Specific questions:

1. Is the material sufficiently preserved for merge as design input?
2. Which topics require separate rationalization PRs?
3. Which candidate concepts should be promoted to Qualification first? (Note: `forge-housekeeping-workers` and `forge-drone-coordination-layer` are explicitly gated — their boundary must be resolved before either can advance.)
4. Which parked concepts block near-term design work?
5. What issue(s) should be opened after this PR merges?

---

## Prompt K — Capability Engineering Layer Integration

> Review the proposed drone handoff and verification design in relation to the existing formalized Forge concepts: `capability-engineering-framework`, `world-specification`, and `capability-trials`. These concepts are formalized on main. The drone design should connect to this layer rather than design a parallel verification mechanism.

Background: the capability engineering framework defines six objects — Capability, World, Invariant, Trial, Evidence, Refinement — that already constitute the theoretical foundation for implementation handoff and verification. The world specification defines the three-drift diagnostic (implementation/design/world drift). The capability-trials concept defines the spec-first principle and identifies the self-confirming loop as a named failure mode.

Specific questions:

1. Should handoff artifacts be **Capability Trial Packs** rather than prose prompts? The execution drone's instruction would then be "make all trials in this pack pass" rather than "build me a thing."
2. Should the verification drone's mechanism be **Capability Trial execution against a World Specification**, not generic test running?
3. Does the **spec-first principle** (trials authored and human-approved before execution agent is dispatched) need to be encoded as a named Forge workflow gate? What enforces it?
4. Should **Gherkin** (Given/When/Then) be adopted as the canonical expression format for Capability Trial Packs? This connects `actionable-intent-verses` (Narrative/Intent split) with the trial pack structure and would be the trial expression format open question in `capability-trials`.
5. How does the **three-drift diagnostic framework** (implementation drift, design drift, world drift) govern the verification drone's failure analysis and Refinement routing?
6. What is the minimum **World Specification** required before a handoff drone can be dispatched? Can a trial pack exist without a backing World Specification, or is a world spec a prerequisite?
7. Should `capability-trials` be updated to formally adopt Gherkin as the trial expression format before the first drone trial pack schema is designed? (A candidate update is already present as an open question in `capability-trials` on main.)

---

## 2. Current Recommended Review Order

1. `engineer-orientation.md` — project context, canonical stage vocabulary, and section 20 (capability engineering layer connection).
2. `excavation.md` — session summary, candidate concepts, rationalization notes, and capability engineering layer relationships.
3. `cost-accounting-and-classification-retention.md` — original session motivation and three-ledger cost model.
4. `global-coherence-map-note.md` — core modularization coherence risk.
5. `design-atlas-related-work-survey.md` — prior concept synthesis and Atlas component analysis.
6. `federated-graphs-and-project-local-forge.md` — cross-repo architecture and federation model.
7. `index.jsonld` — machine-readable session record with concept metadata, rationalization flags, and citation quality.
8. Foundational concepts on main: `capability-engineering-framework`, `world-specification`, `capability-trials`, `actionable-intent-verses`.
9. This file — multi-model challenge loop prompts A–K.
