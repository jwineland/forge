# Design Note: Federated Graphs and Project-Local Forge Layers

**Status:** Design concern requiring review  
**Date:** 2026-04-26  
**Related session:** `2026-04-26-chatgpt-forge-drone-orchestration`  
**Purpose:** Capture the architectural question of how Forge's primary concept registry relates to project-local graphs, manifests, atlases, plans, and implementation evidence.

---

## 1. Problem Statement

Forge is not only a repository for its own concepts. It is intended to elevate concepts, designs, and implementation plans across many projects.

Some projects will be introduced directly by the user. Others may emerge from Forge concept clusters, parked concepts, or repeated design themes. Concepts may be reused across projects, and project-specific learnings may later be generalized back into the primary Forge registry.

This raises a core architectural question:

> When a project is elevated with Forge, where do its graph, manifest, atlas, design decisions, implementation plans, handoffs, and evidence live, and how do they relate to the primary Forge concept registry?

---

## 2. Provisional Answer

Forge likely needs a **federated graph / manifest model**.

The primary Forge registry should not own every detail of every project. Each elevated project should be able to maintain a project-local Forge layer, while preserving explicit lineage to reusable concepts in the primary registry.

Proposed framing:

```text
Primary Forge Registry
↔ Project-local Forge Layer
↔ Implementation Repository Artifacts
```

This avoids both extremes:

```text
Bad: one giant global Forge graph owns everything
Bad: every project is isolated and concept lineage is lost
```

---

## 3. Primary Forge Registry

The primary Forge registry remains the canonical home for general, reusable semantic abstractions.

Examples:

```text
forge:concept:design-atlas
forge:concept:bounded-context-packet
forge:concept:human-as-message-bus
forge:concept:challenge-loop-methodology
forge:concept:semantic-graph-foundation
```

The primary registry answers:

- What is this concept?
- Where did it emerge?
- How has it evolved?
- What other concepts is it related to?
- Where has it been promoted, reused, specialized, or challenged?
- What generalized learning has returned from project use?

The primary registry should preserve reusable meaning and cross-project lineage. It should not become the storage location for every local implementation detail from every project.

---

## 4. Project-Local Forge Layer

When a project is elevated, it may need its own project-local Forge layer, likely resident in that project repository or associated project state store.

Possible file layout:

```text
.forge/
  MANIFEST.md
  atlas.md
  graph.jsonld
  concepts/
  decisions/
  plans/
  packets/
  handoffs/
  jobs/
  reviews/
  reports/
```

This project-local layer represents situated design state.

It answers:

- How does this imported concept apply here?
- What local decisions have been made?
- Which project files embody the design?
- What implementation plans exist?
- What prompt/handoff artifacts exist?
- What reviews and challenges have been performed?
- What is currently coherent, incoherent, unresolved, or drifted?
- What is ready for implementation dispatch?

---

## 5. Situated Concept Realizations

A global Forge concept may be promoted into a project as a project-specific realization.

Example:

```text
Global concept:
forge:concept:design-atlas

Project-local realization:
project:example-app:concept:design-atlas-application
```

The project-local realization should preserve lineage and local adaptation metadata.

Candidate relationships:

```text
project concept
  derivedFrom → forge concept
  appliesTo → project/repo/module
  constrainedBy → project-specific decisions
  implementedBy → files/PRs/commits
  divergesFrom → forge concept, if intentionally modified
  promotedBackTo → forge concept, if generalized insight emerges
```

Key distinction:

```text
Global Forge concepts are portable abstractions.
Project-local concepts are situated applications.
```

---

## 6. Multiple Manifests

Forge should expect multiple manifests at different authority levels.

### 6.1 Global Forge `MANIFEST.md`

Governs the primary Forge registry:

- repo purpose
- lifecycle invariants
- concept storage
- session excavation structure
- vocabulary expectations
- append-only session policy
- promotion and parking rules

### 6.2 Project `.forge/MANIFEST.md`

Governs the project-local Forge layer:

- project scope
- local design state
- imported concepts
- local decisions
- authority chain
- location of Atlas / graph / plans / handoffs
- implementation evidence policy

### 6.3 Scoped Sub-Manifests

Large projects may need scoped sub-manifests:

```text
.forge/areas/auth/MANIFEST.md
.forge/areas/billing/MANIFEST.md
.forge/areas/agent-orchestration/MANIFEST.md
```

These should not become independent conflicting authorities. They are scoped projections under the project manifest.

---

## 7. Multiple Graphs

Forge should also expect multiple graphs.

Possible graph layers:

| Graph | Scope | Owner |
|---|---|---|
| Primary Forge graph | reusable concepts, sessions, vocabulary, cross-project lineage | Forge registry |
| Project graph | imported concepts, local decisions, design areas, implementation plans | Project-local Forge layer |
| Area graph | scoped subdomain within large project | Project-local subarea |
| Implementation evidence graph | files, commits, PRs, tests, handoffs | Project repo / tooling |

These graphs should be federated through explicit identities and lineage edges.

---

## 8. Authority Boundaries

Canonical authority should depend on artifact type.

| Artifact type | Canonical home |
|---|---|
| General reusable concept | Primary Forge registry |
| Global vocabulary | Primary Forge registry |
| Cross-project lineage | Primary Forge registry, with project back-references |
| Project-specific concept realization | Project-local Forge layer |
| Project design decision / ADR | Project repo |
| Project Design Atlas | Project repo |
| Implementation plan | Project repo |
| Prompt / handoff artifact | Project repo |
| Implementation evidence | Project repo / PR / commit |
| Generalized learning from project | Promoted back to primary Forge registry |

Default rule:

> Forge owns reusable semantic abstractions. Projects own situated design state, implementation plans, handoffs, and evidence.

---

## 9. Federation Links

The model needs explicit link types for concept and design movement.

Candidate links:

| Link | Meaning |
|---|---|
| `derivedFrom` | Project-local item derives from primary Forge concept |
| `promotedInto` | Primary Forge concept has been applied to a project |
| `appliesTo` | Concept/design applies to a project, module, file, or domain |
| `constrainedBy` | Project realization is narrowed by local decisions or constraints |
| `implementedBy` | Concept/design/plan is embodied by files, commits, PRs, tests |
| `evidencedBy` | Claim or decision has supporting session, review, PR, or test evidence |
| `divergesFrom` | Project-local realization intentionally differs from source concept |
| `promotedBackTo` | Project-specific learning has been generalized into primary registry |
| `supersedes` | Later concept/design/decision replaces earlier one |
| `conflictsWith` | Concepts or project realizations are in unresolved tension |

Review question: which of these already exist in `_vocabulary/forge-context.jsonld`, which should be added, and which should remain informal until implementation?

---

## 10. Design Atlas Placement

Each elevated project may need its own Design Atlas.

Possible locations:

```text
project/.forge/atlas.md
project/.forge/atlas.jsonld
```

The project Atlas is the global-coherence view for that project. It should include:

- imported Forge concepts
- local concept realizations
- project design areas
- decisions / ADRs
- assumptions
- known tensions
- implementation plans
- prompt/handoff artifacts
- drift reports
- links to files / PRs / commits

The primary Forge registry may also have a registry-level Atlas for Forge itself.

Therefore, Atlas is probably project-scoped by default, but Forge itself can be one project with its own Atlas.

---

## 11. Promotion and Back-Promotion

Concepts should move in both directions.

### Promotion into a project

A global concept is applied locally:

```text
forge:concept:bounded-context-packet
  promotedInto → project:example-app:concept:bounded-context-packet
```

The project records:

- source concept
- local interpretation
- local constraints
- local decisions
- implementation links

### Back-promotion into Forge

A project-specific insight becomes reusable:

```text
project:example-app:concept:atlas-drift-signal
  promotedBackTo → forge:concept:atlas-drift-signal
```

This creates or updates a generalized concept in the primary registry.

### Divergence

A project may intentionally adapt a concept:

```text
project:example-app:concept:design-atlas
  divergesFrom → forge:concept:design-atlas
```

Divergence should not overwrite the global concept. It should record project-specific variation.

---

## 12. Identity and Namespace Requirements

Federation requires explicit identity boundaries.

Candidate ID examples:

```text
forge:concept:design-atlas
forge:session:2026-04-26-chatgpt-forge-drone-orchestration

project:example-app:concept:design-atlas
project:example-app:decision:ADR-004-auth-boundary
project:example-app:packet:2026-04-26-auth-review
project:example-app:plan:auth-refactor-plan
project:example-app:handoff:codex-auth-refactor
```

Requirement:

> The same concept may have multiple project-local realizations, but each realization must preserve lineage to the source concept.

---

## 13. Synchronization Model

Forge may eventually need a registry of known elevated projects.

Example:

```yaml
projects:
  - id: project:forge
    repo: jwineland/forge
    forge_root: /
    atlas: MANIFEST.md or _atlas/...
  - id: project:example-app
    repo: jwineland/example-app
    forge_root: .forge/
    atlas: .forge/atlas.md
```

Each project may also need an imports file:

```yaml
imports:
  - source: forge:concept:design-atlas
    local_id: project:example-app:concept:design-atlas
    version: 2026-04-26
  - source: forge:concept:bounded-context-packet
    local_id: project:example-app:concept:bounded-context-packet
    version: 2026-04-26
```

This enables traceability without forcing every project artifact into the primary Forge repo.

---

## 14. Drift Risks

Federation introduces new risks:

```text
Forge says one thing.
Project manifest says another.
Project Atlas says another.
Implementation says another.
```

Forge therefore needs drift checks across authority layers:

```text
primary registry concept
→ imported project concept
→ project MANIFEST
→ project Atlas
→ local decisions / ADRs
→ implementation plans
→ code / PRs / commits
```

This links the federated graph idea directly to the Design Atlas and Global Coherence Map concern.

---

## 15. Relationship to Drones / Workers

Drones may help maintain federation state:

| Drone | Federation role |
|---|---|
| Index drone | Tracks project-local Forge files and imported concepts |
| Classifier drone | Maps local artifacts to primary concepts and project design areas |
| Packet drone | Builds review packets from local Atlas and imported concept lineage |
| Drift drone | Detects mismatch between registry, project Atlas, plans, and implementation |
| Handoff drone | Generates prompts grounded in project-local plans and source concept lineage |
| Cost governor | Chooses local/API/subscription route for federation-maintenance work |

However, drones are not a prerequisite for the design model. Federation can begin as file-based lineage and manifest discipline.

---

## 16. Relationship to Existing Forge Concepts

This design note relates strongly to:

| Existing concept | Relationship |
|---|---|
| `semantic-graph-foundation` | Federation extends graph identity and traversal across project boundaries |
| `manifest-as-coherence-anchor` | Multiple manifests need an authority chain rather than conflict |
| `concept-progression-record` | Project-local realizations may need local progression records linked to global CPRs |
| `concept-capability-stratification` | Project-local concepts may move toward capability realization |
| `corpus-lifecycle-system` | Each project-local Forge layer is a corpus with lifecycle modes |
| `forge-guidance-engine` | Guidance may need to operate across registry and project graphs |
| `evaluation-trust-plane` | Federation drift and Atlas review require trust/evaluation rubrics |
| `object-oriented-documentation` | Project-local subgraphs may inherit or specialize global concept structures |

---

## 17. Open Review Questions

1. Should every elevated project have a `.forge/` directory, or should some project Forge layers live outside project repos?
2. What is the minimal project-local Forge layer?
3. What is the minimum import record needed when a Forge concept is used in a project?
4. Should project-local concepts be copied, referenced, projected, or instantiated?
5. How should Forge represent concept divergence across projects?
6. How should generalized project learnings be promoted back to the primary registry?
7. Should a project-local Atlas be mandatory before implementation planning?
8. What is the authority order among primary registry, project manifest, project Atlas, ADRs, plans, and implementation evidence?
9. How should Graph/Manifest/Atlas drift be detected and resolved?
10. What vocabulary additions are required for federation?
11. How does this model avoid making Forge a monorepo for all project knowledge?
12. How does this model avoid losing global reusable learning inside project-local details?

---

## 18. Provisional Recommendation

Adopt a federated model as the working design assumption:

```text
Primary Forge Registry
  reusable concepts
  global vocabulary
  cross-project lineage
  generalized learning

Project-Local Forge Layer
  project manifest
  project design atlas
  local concept realizations
  decisions / ADRs
  plans / packets / handoffs
  implementation evidence

Federation / Synchronization
  import links
  promotion links
  divergence links
  back-promotion links
  drift reports
```

Do not implement the full federation mechanism yet. First, rationalize the artifact model, namespace scheme, and authority chain with human and multi-model review.

---

## 19. Non-Implementation Constraint

This note captures a design model and open questions. It does not implement `.forge/`, project registries, synchronization, graph federation, schema changes, or import/export tooling.
