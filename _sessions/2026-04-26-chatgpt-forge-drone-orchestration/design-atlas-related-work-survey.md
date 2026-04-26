# Related Work Survey: Design Atlas / Global Coherence Map

**Status:** Design survey for review and rationalization  
**Date:** 2026-04-26  
**Related session:** `2026-04-26-chatgpt-forge-drone-orchestration`  
**Purpose:** Survey existing Forge concepts that align with the emerging Design Atlas / Global Coherence Map idea.

---

## 1. Survey Conclusion

The Design Atlas concept is **not wholly new**. It appears to synthesize several existing Forge concepts that already point toward global coherence, semantic graphing, design drift prevention, guided advancement, evaluation, and modular corpus governance.

What appears new is the explicit framing of a **project-level global design survey artifact** that replaces the lost whole-authority-document review function after modularization.

Provisional conclusion:

> Design Atlas should likely be treated as a synthesis / projection layer built from existing Forge primitives, not as an unrelated new subsystem.

---

## 2. Design Pressure Being Addressed

The historical full-authority-document workflow allowed frontier reasoning models to survey the entire design and catch cross-boundary gaps, contradictions, and conceptual incoherence.

Modularization reduces repeated large-context processing but creates a drift risk:

> Local packets can be coherent while the whole design becomes incoherent.

The Design Atlas is a candidate answer to this risk: a maintained, compressed, navigable, cross-linked map of the current design state that supports periodic global review without requiring full corpus reloads on every turn.

---

## 3. Strongly Related Existing Concepts

### 3.1 `manifest-as-coherence-anchor`

**Alignment:** Very strong.

This concept already names the need for a coherence anchor across multi-file corpora. It defines the MANIFEST as the place that records scope, authority chain, invariants, file registry, and design decisions.

Relevant elements:

- authority chain
- invariants table
- file registry
- design decisions with rationale
- scoped sub-manifests for larger corpora
- drift resolution when manifest and authority documents conflict

**Atlas implication:**

Design Atlas may generalize or extend the MANIFEST-as-anchor idea from corpus governance into design-state navigation. The Atlas may either be:

1. a richer manifest projection,
2. a design-specific companion to the manifest, or
3. a rendered view generated from the semantic graph.

Open question: Should the Atlas replace, extend, or sit beside a MANIFEST?

---

### 3.2 `semantic-graph-foundation`

**Alignment:** Foundational.

This concept already argues that the MANIFEST is a flat projection of an underlying directed graph, and that making the graph explicit enables transitive drift detection, stable identity, graph traversal, and rendered human-readable views.

Relevant elements:

- stable node identity
- `Concept`, `ContentModule`, `Session`, `Thread`, `Exchange`, `Emergence`, `LockedComposition`, `IntentDeclaration`, `OutputArtifact`
- edges such as `dependsOn`, `composesInto`, `locksTo`, `supersedes`, `cites`, `promotedInto`
- MANIFEST as derived view rather than sole authority
- transitive drift detection

**Atlas implication:**

Design Atlas is likely a human-facing projection of the semantic graph, augmented with design-specific summaries, conflicts, assumptions, decisions, and open questions.

Open question: Does Atlas require new node/edge types such as `Design`, `DesignArea`, `Assumption`, `Tension`, `Decision`, `Plan`, `Handoff`, or can it be represented using existing node types?

---

### 3.3 `object-oriented-documentation`

**Alignment:** Strong application-layer analogue.

OOD treats documentation modules as typed objects with properties, methods, inheritance, and dependency relationships. It explicitly discusses propagation of changes through dependencies to prevent silent drift.

Relevant elements:

- namespace / class / object / method / property mapping
- inheritance relationships
- graph traversal to detect affected dependent artifacts
- distinction between structural dependency and procedural inheritance
- namespace conflict detection

**Atlas implication:**

Design Atlas may need an OOD-like hierarchy for design areas:

```text
Project / World
  Design Area
    Concept Cluster
      Decision
      Assumption
      Plan
      Handoff
```

OOD gives a mental model for modular design without losing inheritance/dependency visibility.

Open question: Should Atlas define a class hierarchy for design artifacts, or should it only render graph relationships already encoded elsewhere?

---

### 3.4 `concept-progression-record`

**Alignment:** Strong for continuity and anti-regression.

The CPR is the ratcheting primitive that prevents concept state from dissolving across turns, sessions, and platforms. It aggregates into a Concept Ledger, which is already described as a continuity spine.

Relevant elements:

- stable concept identifiers
- current best definition
- carry-forward points
- open questions
- related concepts
- promotion targets
- supporting artifacts
- regression risks
- concept ledger as continuity spine
- carry-forward set for session-level continuity

**Atlas implication:**

The Design Atlas likely consumes CPR entries and concept ledger state. It may be the project-level counterpart to the concept ledger: not one concept's state, but the navigable state of a design composed from many concepts.

Open question: Is Atlas a ledger, a projection of the ledger, or a higher-order artifact built from multiple ledgers plus design/project metadata?

---

### 3.5 `forge-guidance-engine`

**Alignment:** Strong operational relationship.

The Guidance Engine monitors concept progression, identifies missing prerequisites, recommends next actions, routes stage skills, and back-prompts the human.

Relevant elements:

- Central Progression Controller
- stage-specialized skills / subagents
- rationalization and formalization skills
- evaluation-aware progression
- regression detection
- targeted back-prompting
- packaging state for later work

**Atlas implication:**

The Atlas may be a critical input to the Guidance Engine. Without a global map, the Guidance Engine can only make local recommendations. With an Atlas, it can detect cross-concept coherence issues and recommend rationalization, merging, promotion, or design review.

Open question: Does Guidance Engine own the Atlas, or merely read/write it?

---

### 3.6 `stage-aware-guided-advancement`

**Alignment:** Strong behavioral requirement.

This concept says Forge must monitor maturity, readiness, missing prerequisites, regression risks, and cross-concept coherence issues, then proactively recommend the next bounded move.

Relevant elements:

- current stage and confidence
- readiness signals
- missing prerequisites
- regression risks
- cross-concept coherence issues
- bounded back-prompts
- mobile-safe orchestration

**Atlas implication:**

The Atlas is likely the artifact that makes cross-concept coherence visible enough for stage-aware advancement to operate at design scale.

Open question: Should Atlas maintenance be a prerequisite for advancing a design from rationalization to implementation planning?

---

### 3.7 `evaluation-trust-plane`

**Alignment:** Strong for coherence review and challenge loops.

The Evaluation and Trust Plane defines structured evaluation, multi-judge disagreement, evidence requirements, versioned rubrics, and escalation classes.

Relevant elements:

- architectural coherence as an evaluation criterion
- evidence-bearing judge outputs
- structured semantic validation
- subjective/strategic panel judging
- multi-judge disagreement as signal
- versioned rubrics
- escalation on contradiction, low confidence, or high disagreement

**Atlas implication:**

Atlas review should not be a vague "does this look coherent?" pass. It should be governed by explicit rubrics such as:

- boundary clarity
- dependency direction
- assumption freshness
- decision consistency
- unresolved conflict visibility
- implementation-plan alignment
- design area coverage

Open question: Should Atlas include its own review rubric, or should evaluation rubrics live in the Evaluation and Trust Plane and be referenced by Atlas review jobs?

---

### 3.8 `corpus-lifecycle-system`

**Alignment:** Strong lifecycle context.

This concept defines Birth, Growth, and Maintenance modes for governed corpora. Growth and Maintenance are where Atlas becomes important.

Relevant elements:

- content accumulates and structure emerges
- sub-elements break into scoped sub-manifests
- system detects what is present, missing, and drifted
- maintenance uses drift checks, challenge loop reviews, and PR-gated changes

**Atlas implication:**

Atlas may be especially important in Growth and Maintenance modes. It may not be necessary for a small birth-phase project, but becomes essential once modularization creates cross-boundary coherence risk.

Open question: At what project size/complexity should an Atlas be required?

---

### 3.9 `concept-capability-stratification`

**Alignment:** Moderate to strong.

This concept distinguishes exploratory concept engineering from bounded capability engineering, and names bridge objects such as promotion records, derivation records, dependency links, and open assumptions.

Relevant elements:

- concept stratum vs. capability stratum
- promotion path
- bridge objects
- open assumptions
- dependency links
- capability candidates and formal capabilities

**Atlas implication:**

Atlas may need to show where design elements sit across strata: exploratory concept, candidate construct, design decision, implementation plan, capability candidate, operational capability.

Open question: Should Atlas be stage/stratum aware?

---

### 3.10 Parked `completeness-scoring-methodology`

**Alignment:** Moderate but important.

Completeness scoring is parked, but it is relevant because Atlas should not merely exist; it should be assessed for whether it is sufficient to support global design review.

Relevant elements:

- readiness to advance
- completeness of concept/design metadata
- detecting what is missing
- providing a basis for advancement gates

**Atlas implication:**

A Design Atlas may need a completeness score or coverage report, especially before using it as the basis for frontier review or implementation planning.

Open question: What counts as an adequately complete Atlas for a given project stage?

---

## 4. Related But More Indirect Concepts

### `multi-model-deliberation-roles`

Useful for defining different model review roles over the Atlas: critic, architect, risk reviewer, implementation reviewer, and dissenting judge.

### `challenge-loop-methodology`

Useful for defining Atlas review cycles and structured challenge loops over the compressed global map.

### `human-ai-role-separation`

Relevant because Atlas should reduce human burden without removing human authority over canonical design decisions.

### `intent-as-semantic-contract`

Relevant if Atlas review packets and implementation handoffs are treated as intent declarations with content contracts.

### `actionable-intent-verses`

Relevant if Atlas-derived handoffs need to become executable or dispatchable prompt artifacts.

### `conversational-concept-regression`

Relevant because Atlas is partly an anti-regression mechanism for project/design state rather than only individual concepts.

---

## 5. What Appears Genuinely New

The following seem to be new or newly explicit in the Atlas framing:

1. **Project-level global design survey artifact**  
   Existing concepts address concepts, manifests, semantic graphs, and corpus lifecycle. Atlas specifically names the need for a periodic whole-design review surface after modularization.

2. **Replacement for full-authority-document cycling**  
   Atlas preserves the cross-boundary review function of large authority documents without requiring every turn to process the full document.

3. **Layered review artifact**  
   Atlas may combine human-readable map, machine-readable graph, coherence ledger, assumption ledger, drift report, and frontier review digest.

4. **Boundary between local packet work and global coherence work**  
   Atlas creates an explicit control point: local design packets are only safe if anchored to the global map.

5. **Design-scale anti-regression primitive**  
   CPR prevents individual concepts from regressing. Atlas may prevent whole designs from regressing or fragmenting.

---

## 6. Candidate Atlas Definition

A **Design Atlas** is a durable, project-scoped, human-readable and machine-addressable projection of current design state that preserves global coherence across modular concepts, decisions, assumptions, plans, and implementation artifacts.

It exists to let humans, drones/workers, and frontier models review the shape of a design without reloading every underlying source artifact.

---

## 7. Candidate Atlas Components

| Component | Purpose | Related prior concept | Notes |
|---|---|---|---|
| Design area map | Names major design regions and ownership/scope | MANIFEST as coherence anchor, OOD | |
| Concept cluster map | Shows grouped concepts and relationships | Semantic graph, CPR | |
| Decision map | Links ADRs/design decisions to concepts and files | MANIFEST, semantic graph | |
| Assumption ledger | Tracks assumptions, freshness, and unresolved world claims | Concept-capability stratification | |
| Coherence ledger | Lists tensions, conflicts, contradictions, and unresolved rationalization items | Stage-aware advancement, guidance engine | |
| Drift report | Shows design/implementation mismatch and stale artifacts | Semantic graph, evaluation/trust plane | |
| Frontier review digest | Compressed global packet for high-reasoning review | Challenge loops, multi-model deliberation | |
| Completeness/coverage report | Indicates whether the Atlas is sufficient for review or planning | Completeness scoring, evaluation/trust plane | ⚠ **BLOCKED**: depends on parked `completeness-scoring-methodology`. This component cannot be designed or implemented until that concept is unparked and resolved. See Open Rationalization Question 13. |

---

## 8. Candidate Relationship Model

```text
Semantic Graph = authoritative machine structure
MANIFEST = governance and authority projection
Concept Ledger / CPR = ratcheting concept state
Design Atlas = project-level global coherence projection
Guidance Engine = controller that reads Atlas/Ledger and recommends next moves
Evaluation & Trust Plane = rubrics and judge processes for Atlas review
Drones/Workers = maintain indexes, summaries, drift reports, packets, and review digests
```

This suggests Atlas is neither a replacement for the graph nor merely a document. It is a projection and review surface over the graph/ledger/manifest state.

---

## 9. Open Rationalization Questions

1. Is Design Atlas a first-class artifact type in Forge vocabulary?
2. Is Atlas project-scoped only, or can Forge itself have a registry-level Atlas?
3. Is Atlas generated from the semantic graph, manually maintained, or hybrid?
4. How does Atlas relate to MANIFEST — extension, derived view, sibling, or replacement?
5. What node/edge types are missing to support Atlas?
6. What is the minimum viable Atlas for a small project?
7. What threshold triggers Atlas requirement for larger projects?
8. How often should Atlas receive frontier-model review?
9. What constitutes Atlas drift?
10. Should implementation planning be blocked if Atlas coverage is insufficient?
11. How should Atlas capture uncertainty and disagreements among models?
12. What drones are responsible for maintaining Atlas components?
13. **What is the dependency order between Atlas completeness/coverage reporting and the unparked `completeness-scoring-methodology`? This concept is currently parked and blocks the completeness/coverage report component (section 7). Unparking and resolving `completeness-scoring-methodology` should be treated as a prerequisite before the completeness component of Atlas is designed.**

---

## 10. Proposed Review Prompts

### Prompt A — Synthesis Fit

> Review the Design Atlas proposal against Forge concepts: MANIFEST as Coherence Anchor, Semantic Graph Foundation, Object-Oriented Documentation, Concept Progression Record, Forge Guidance Engine, Stage-Aware Guided Advancement, Evaluation and Trust Plane, and Corpus Lifecycle System. Is Atlas a distinct first-class artifact or a projection generated from these existing primitives?

### Prompt B — Minimal Viable Atlas

> Define the smallest useful Design Atlas that restores whole-design coherence checking after authority-document modularization. What must it include, what can wait, and what should explicitly not be included? Note that the completeness/coverage report component is blocked on the parked `completeness-scoring-methodology` and should be excluded from the minimal viable Atlas scope.

### Prompt C — Drift and Coherence Rubric

> Propose a rubric for reviewing an Atlas for global design coherence. Include criteria, required evidence, escalation thresholds, and examples of failures that should block implementation planning.

### Prompt D — Vocabulary Impact

> Identify required vocabulary additions or schema extensions for representing Design Atlas concepts in JSON-LD. Which existing node/edge types are sufficient, and which new ones are needed?

---

## 11. Provisional Recommendation

Treat Design Atlas as a **candidate first-class Forge artifact** pending model and human review.

Do not immediately implement an Atlas generator. First, rationalize whether Atlas is:

1. a new artifact type,
2. a rendered graph projection,
3. a MANIFEST extension,
4. a project-scoped guidance object, or
5. some combination of the above.

The near-term action should be a design review, not implementation.
