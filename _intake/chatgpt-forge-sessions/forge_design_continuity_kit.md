# Forge Design Continuity Kit

## Purpose
This document is the initial control surface for AI Forge. It exists to reduce conversational concept regression, preserve core design intent, and provide a ratcheting structure for advancing meaningful work from conversation.

This is not the full Forge architecture. It is the minimum continuity package required to keep Forge development coherent while the broader design evolves.

---

# 1. Forge North Star

## Identity
AI Forge is a structured method for advancing meaningful work from conversation into reusable, formalized, and optionally operationalized artifacts.

## Core Problem
Long, high-velocity design conversations tend to lose, flatten, or replace previously surfaced concepts as discussion advances. This conversational concept regression causes architectural drift and weakens design coherence.

## Core Function
Forge exists to surface, preserve, mature, capture, formalize, and where appropriate operationalize valuable concepts without allowing them to silently dissolve or be replaced by smoother but less faithful restatements.

## Forge is not
- merely a generic chat workflow
- merely a document generator
- merely a passive memory layer
- dependent on the user to manually direct every stage
- a giant single authority document
- a loose pile of modular documents with no continuity spine

## Core Progression Spine
1. Excavation
2. Qualification
3. Rationalization
4. Promotion
5. Formalization
6. Operationalization (provisional later-stage extension)

---

# 2. Canonical Concepts

## Canonical

### Forge
A structured method for advancing meaningful work from conversation.

### Conversational Concept Regression
The tendency for long-form AI-assisted design conversations to gradually lose, flatten, distort, or replace previously surfaced concepts, distinctions, and process structures as newer synthesis layers accumulate.

### Progressive Concept Preservation
A Forge principle stating that valuable conceptual distinctions, structures, and design insights surfaced in conversation must be preserved, matured, and progressively operationalized rather than being allowed to dissolve as discussion evolves.

### Excavation
The surfacing stage. Forge reveals latent structure from conversational material, including assumptions, tensions, distinctions, concept fragments, and unresolved questions. Excavation is discovery, not drafting or design review.

### Qualification
The refinement stage. Forge determines which surfaced concepts are meaningful enough to retain, how they should be bounded, whether they overlap existing concepts, and which fragments should be carried forward, merged, or discarded.

### Rationalization
The design review and improvement stage. Forge challenges and improves qualified concepts against architectural coherence, fit, redundancy, tradeoffs, and design quality.

### Promotion
The capture stage. Forge moves concepts from conversational output into retained project structure. Promotion includes classification and routing, not mere saving.

### Formalization
The deliverables stage. Forge packages promoted concepts into durable outputs such as concept definitions, registries, design docs, ADR candidates, grouped concept sets, schemas, or work-ready structures.

### Carry-Forward Set
A compact, explicit list of concepts, distinctions, or decisions that must not be dropped in subsequent work.

### Concept Ledger
The ratcheting continuity structure that tracks active concepts, their status, stage, carry-forward points, promotion targets, and related artifacts.

## Likely Canonical

### Operationalization
A later-stage Forge extension where formalized artifacts become trialable, testable, measurable, challengeable, or executable forms such as capabilities, world definitions, invariants, trials, and evidence structures.

### World Definition
A structured articulation of the environment in which a concept or capability exists, including actors, entities, constraints, states, boundaries, assumptions, and failure conditions.

### Formalization Loops
Iterative packaging loops used to group, shape, and harden concepts or concept hierarchies into durable artifacts while soliciting only the missing human input needed for sound formalization.

### Promotion Pathways
The mapping of promoted concepts into downstream destinations such as glossary entries, concept registry records, architecture notes, ADR candidates, capability candidates, work items, plans, or formal documents.

### Artifact Lineage
The mapping between concepts and the conversational, documentary, and delivery artifacts that surfaced, supported, refined, formalized, or implemented them.

### Guidance Engine
A stage-aware proactive mechanism that recommends the next best move, asks for only the needed human input, and invokes stage-specific skills when work is ready to advance.

## Provisional / Needs Ratification

### Forge as the backbone for a formal capability engineering framework
### Planning mode / plan derivation as a first-class Forge mode
### Registry families beyond concepts and artifacts
### Specific scoring strategies bound to stages and artifact classes

---

# 3. Forge Stage Model

## 3.1 Excavation
**Purpose**: Surface latent structure from conversation.

**Typical outputs**:
- surfaced concept fragments
- assumptions
- tensions
- candidate distinctions
- unresolved questions
- nearby related concepts

**Must not do**:
- prematurely collapse into polished drafting
- perform architecture review as the dominant behavior
- silently decide canon without later qualification

**Advance when**:
- enough latent material has been surfaced to meaningfully compare, bound, or retain

**Regression risk if skipped**:
- vague ideas get prematurely hardened
- hidden structure is lost

## 3.2 Qualification
**Purpose**: Decide which surfaced material is meaningful enough to retain and refine.

**Typical outputs**:
- qualified concepts
- bounded definitions
- merged or rejected fragments
- provisional or likely canonical status
- carry-forward candidates

**Must not do**:
- assume every surfaced idea deserves persistence
- blur distinct concepts to reduce complexity too early

**Advance when**:
- a concept is coherent enough to review and improve against the wider architecture

**Regression risk if skipped**:
- noise and signal remain mixed
- concepts are carried forward without proper boundaries

## 3.3 Rationalization
**Purpose**: Challenge and improve concepts through design review.

**Typical outputs**:
- refined concept statements
- architectural implications
- overlap/conflict analysis
- tradeoff framing
- comparative alternatives

**Must not do**:
- replace the original meaning of a concept without explicit note
- treat smoother wording as necessarily better design

**Advance when**:
- concepts are mature enough to capture in retained project structure

**Regression risk if skipped**:
- concepts are promoted before being sufficiently challenged

## 3.4 Promotion
**Purpose**: Capture concepts into retained project structure.

**Typical outputs**:
- concept records
- status changes
- registry candidates
- promotion destinations
- work item or artifact candidates

**Must not do**:
- merely save text without classification
- allow important concepts to remain only in conversational residue

**Advance when**:
- promoted concepts are ready to be packaged into formal outputs

**Regression risk if skipped**:
- conversational insights evaporate

## 3.5 Formalization
**Purpose**: Package promoted material into durable outputs.

**Typical outputs**:
- concept packages
- formal definitions
- grouped hierarchies
- design docs
- ADR candidates
- structured prompts
- schemas
- registry entries

**Must not do**:
- require exhaustive human prompting for every missing detail
- force one packaging style on all concept types

**Advance when**:
- concepts have been packaged sufficiently to be used downstream

**Regression risk if skipped**:
- retained concepts remain too vague to reuse consistently

## 3.6 Operationalization (Provisional)
**Purpose**: Convert formalized artifacts into challengeable, measurable, or executable forms.

**Typical outputs**:
- world definitions
- invariants
- trials
- evaluation structures
- evidence models
- capability candidates

**Must not do**:
- imply that every concept must become executable
- erase the distinction between design maturity and operational readiness

**Advance when**:
- the concept should support trial, validation, execution, or capability engineering

**Regression risk if skipped**:
- later-stage applicability may remain underspecified

---

# 4. Progression Rules

## Non-negotiable rules
1. Forge must not depend on the user to manually direct every stage.
2. Forge must proactively recommend sensible next-stage actions when readiness is high.
3. Every meaningful Forge session should produce a carry-forward set.
4. Important concepts must not remain solely in conversational residue.
5. Promotion must classify and route concepts, not merely save them.
6. Modular docs must be anchored by a central continuity mechanism.
7. Rich workspace artifacts are not the sole source of truth.
8. Mobile-safe interaction must support the minimum ratchet.
9. Formalization should use tailored back-prompts for missing information rather than generic clarifying prompts.
10. Different stages and artifact classes may use different evaluation and scoring strategies.
11. Provisional concepts must be marked as provisional rather than silently treated as canonical.
12. Later extensions must not silently rewrite the core Forge spine.

---

# 5. Interaction Modes

## 5.1 Conversational / Mobile Mode
**Must support**:
- capture discoveries
- review carry-forward state
- mark concepts as provisional/canonical candidates
- mark promotion intent
- review current stage/status
- emit session ratchet summary
- queue deeper follow-up work

**May defer**:
- large hierarchy editing
- deep artifact inspection
- complex formalization drafting

## 5.2 Structured Workspace Mode
**Must support**:
- deeper formalization
- grouped hierarchy editing
- concept comparison
- registry review
- artifact mapping
- document drafting

## 5.3 Durable Artifact / Repo Mode
**Must support**:
- versioned persistence
- traceable linkage to concepts and artifacts
- formal document maintenance
- patch and delta tracking

---

# 6. Required Capabilities

## 6.1 Continuity
- maintain a central concept ledger
- produce carry-forward sets
- record ledger deltas
- track canonical/likely canonical/provisional status
- identify regression risks

## 6.2 Progression
- identify current stage per concept or concept cluster
- detect readiness to advance
- recommend next-stage action
- distinguish exploration from design changes

## 6.3 Capture and Promotion
- capture concepts into retained structure
- classify downstream destination
- maintain promotion pathways
- preserve rationale and open questions

## 6.4 Formalization
- package grouped concepts
- solicit missing rationale/invariants/examples as needed
- support formalization loops
- produce durable concept and design artifacts

## 6.5 Guidance
- proactively back-prompt the user with the next best move
- invoke stage-specific skills or workflows
- reduce human orchestration burden while preserving approval authority

## 6.6 Interaction Modes
- support mobile-safe use
- support richer workspace follow-up
- maintain reliable handoff between modes

## 6.7 Registry and Lineage
- support concept registries
- support artifact mapping and lineage
- support cross-project reuse
- support semantic relationships between concepts

## 6.8 Evaluation
- use stage-appropriate evaluation methods
- support multiple scoring strategies where appropriate
- distinguish deterministic validation from subjective judgment

## 6.9 Extensions
- support world definition
- support capability engineering evolution
- support plan derivation from matured concepts where appropriate

---

# 7. Concept Ledger (Initial Entries)

| ID | Concept | Stage | Status | Carry Forward | Notes |
|---|---|---:|---|---|---|
| forge.identity | Forge as structured advancement of meaningful work from conversation | Rationalization | Canonical | Preserve as primary identity | North star concept |
| forge.problem.regression | Conversational concept regression | Rationalization | Canonical | Keep explicit as core problem | Anti-regression anchor |
| forge.principle.preservation | Progressive concept preservation | Rationalization | Canonical | Must remain explicit | Governing principle |
| forge.stage.excavation | Excavation | Promotion | Canonical | Preserve meaning as surfacing, not review | Core stage |
| forge.stage.qualification | Qualification | Promotion | Canonical | Preserve as refinement and retention decision | Core stage |
| forge.stage.rationalization | Rationalization | Promotion | Canonical | Preserve as design review/improvement | Core stage |
| forge.stage.promotion | Promotion | Promotion | Canonical | Preserve as capture plus routing | Core stage |
| forge.stage.formalization | Formalization | Promotion | Canonical | Preserve as packaging into durable outputs | Core stage |
| forge.stage.operationalization | Operationalization | Qualification | Provisional | Keep visible, do not silently canonize or drop | Later-stage extension |
| forge.primitive.carry_forward | Carry-forward set | Promotion | Canonical | Must exist after meaningful sessions | Ratchet primitive |
| forge.primitive.ledger | Concept ledger | Qualification | Likely Canonical | Central continuity mechanism | Ratchet primitive |
| forge.mode.mobile | Mobile-safe Forge mode | Rationalization | Likely Canonical | Must not be treated as second-class | Interaction requirement |
| forge.guidance | Guidance engine / proactive back-prompting | Qualification | Likely Canonical | Must reduce orchestration burden | Controller-like behavior |
| forge.world | World definition | Qualification | Likely Canonical | Cross-stage construct | Important extension |
| forge.registry | Concept registries and semantic relationships | Excavation | Provisional | Preserve as major design area | Needs formalization |
| forge.lineage | Artifact retrieval/mapping/recording | Excavation | Provisional | Preserve as anti-regression support | Needs formalization |
| forge.planning | Plan derivation / planning mode | Excavation | Provisional | Preserve without forcing into core spine yet | Needs qualification |

---

# 8. Carry-Forward Set (Current)

The following points must not be dropped in future Forge work:

1. Forge is a structured method for advancing meaningful work from conversation.
2. Conversational concept regression is a core problem Forge exists to solve.
3. The canonical progression spine is excavation, qualification, rationalization, promotion, and formalization.
4. Operationalization is a meaningful later-stage extension and should remain visible, but is not yet fully ratified.
5. Forge must not depend on the user to manually direct every stage.
6. Forge should proactively recommend next-stage actions and use stage-specific skills or workflows.
7. A central concept ledger and carry-forward mechanism are required to prevent loss across modular work.
8. Mobile-safe interaction is a first-class requirement.
9. Formalization includes packaging, grouping, hierarchy shaping, and tailored prompts for missing information.
10. World definition, registry modeling, artifact lineage, capability engineering support, and planning support are important evolved concepts that must remain visible during future design work.

---

# 9. Formalization Queue

## Immediate
1. Formalize the Forge concept ledger schema.
2. Formalize the per-session operating pattern for chat.
3. Formalize the guidance engine minimal design.
4. Qualify operationalization as canonical, likely canonical, or extension-only.
5. Qualify whether planning is a first-class Forge mode or a downstream derivative.

## Near-term
6. Formalize registry families and semantic relationship model.
7. Formalize artifact lineage model.
8. Formalize promotion pathways.
9. Formalize world definition as a cross-stage construct.
10. Formalize stage-specific scoring/evaluation strategies.

---

# 10. Chat Operating Pattern

For meaningful Forge turns, the assistant should actively use this control surface.

## Per meaningful turn
- identify the active concept(s)
- identify or infer the current stage
- determine whether the turn is exploratory or changes design state
- classify the idea as core spine, support system, extension, or future item
- recommend the next best move

## After meaningful work blocks
Emit:
1. **Carry Forward** — must-not-drop points
2. **Ledger Delta** — what changed in concept state
3. **Queue Update** — what should be qualified, promoted, or formalized next
4. **Suggested Next Move** — proactive back-prompt

## Default back-prompt behavior
Instead of asking “what do you want to do next?”, Forge should prefer:
- here is the best next move and why
- here is the minimum input I need from you
- here is what I can do now vs what may need richer follow-up

---

# 11. Immediate Suggested Next Move

The next best move is to formalize two things before expanding the architecture further:

1. **Forge Concept Ledger Schema**
   - so concept state becomes explicit and ratcheting
2. **Forge Guidance Engine Minimum Design**
   - so Forge can proactively advance work and reduce orchestration burden

These two items will make the continuity mechanism operational rather than merely aspirational.

