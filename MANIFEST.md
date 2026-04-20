# Forge Manifest

## Purpose of This File

This manifest is the authoritative orientation document for the Forge repository. Forge is a semantic knowledge lifecycle system — it governs how concepts are excavated from conversations, classified, versioned, parked, promoted, and composed into corpus content across any project.

This repo is the **default general concept registry**. It is the landing place for all `forge this conversation` operations unless a specific project repo is named.

**Read this file first** at the start of any working session involving concept excavation, classification, or promotion.

---

## Corpus Identity

**What this is:** A concept registry and knowledge lifecycle management system. It captures meaningful concepts emerging from human-AI collaborative work, records their provenance, tracks their development state, and routes them for use in specific project corpora.

**What it is not:** A project-specific corpus. Project corpora (general_docs, ironfish, etc.) are governed by their own MANIFESTs and contain their own authority documents. Forge governs the lifecycle of the concepts that feed those corpora.

**The problem it solves:** Collaborative AI sessions generate more structured knowledge than can be tracked manually. Concepts arise, relate to each other, become partially formalized, get set aside, and are lost when sessions end. Forge is the persistence and organization layer that prevents that loss.

---

## Session Bootstrap

1. Read this file
2. Read `_vocabulary/forge-context.jsonld` if the session involves schema or graph work
3. Check `_parked/` for concepts with triggers relevant to current work
4. Check `_concepts/` for prior work on the topic at hand
5. For a new excavation: follow the procedure in `_sessions/README.md`

---

## Authority Model

| Layer | Location | Owns |
|---|---|---|
| Vocabulary authority | `_vocabulary/forge-context.jsonld` | Node types, edge types, status vocabulary, reference types |
| Concept registry | `_concepts/` | Individual concept definitions, dependencies, promotion status |
| Session index | `_sessions/` | Excavation records, citation addresses, session metadata |
| Parked concepts | `_parked/` | Deferred concepts with trigger conditions |
| Manifest coherence | `MANIFEST.md` | This file — authority chain, invariants, maintenance protocol |
| Editing behavior | `CLAUDE.md`, `AGENTS.md`, `.claude/` | How humans and AI tools work on this repo |

---

## Key Invariants

### Concept status vocabulary

Concepts progress through these primary stages:

- `excavated` — extracted from conversation, not yet classified
- `classified` — type assigned, dependencies noted
- `formalized` — fully described with metadata complete
- `operationalized` — trialable or executable form achieved
- `archived` — no longer actively tracked

Concepts may also undergo these working transitions at any stage:

- `parked` — intentionally deferred with a trigger condition; can be unparked and returned to any prior stage
- `promoted` — routed into a specific project corpus or downstream context; promotion is a routing decision, not a maturity stage. A concept may be promoted before or after full formalization.
- `forked` — branched for specialized use in a specific project while the original remains in the registry

**Important:** Promotion is not the same as formalization. Promotion is the decision to route a concept into active use in a specific context. Formalization is the act of expressing the concept in a rigorous, canonical, and durable form. These can happen independently and in either order.

### Reference types for content modules
- `floating` — always resolve to most current validated version
- `locked` — resolve to specific content hash, immutable
- `constrained` — resolve to version satisfying declared constraints

### Canonical stage progression

The canonical Forge stage progression for concept maturation is:

**Excavation → Qualification → Rationalization → Formalization → Operationalization**

Promotion, parking, and forking are working transitions that can occur at any point in this progression. They are orthogonal to maturity stage.

### Citation address format

```
forge:SESSION_ID:THREAD_ID:EXCHANGE_N[:EMERGENCE_N][.BRANCH]
```

Example (linear): `forge:2026-04-18-claude-general-docs:forge-design:exchange-47:emergence-2`

Example (branched): `forge:2026-04-19-gemini-citation-modality:urn-design:exchange-7.b`

Components:
- **SESSION_ID** — date + platform + context identifier
- **THREAD_ID** — named topic area within the session
- **EXCHANGE_N** — turn pair number within the thread
- **EMERGENCE_N** — optional: specific emergence point within an exchange
- **BRANCH** — optional: `.b`, `.c` etc. for regenerated or edited responses within the same exchange. Omit for the first/canonical response.

Sub-verse branching rationale: when a response is regenerated or a prompt is edited within a session, the linear exchange number is ambiguous. The branch suffix preserves the canonical exchange address while uniquely identifying the variant. The undecorated address always refers to the first/canonical response.

### Routing rules
- `forge this conversation` — deposits to this repo, no project scope
- `forge this in [repo]` — deposits directly to named project repo
- `forge this for [repo]` — deposits here, tagged as candidate for named project

---

## File Registry

| File | Role | Status |
|---|---|---|
| `MANIFEST.md` | Corpus orientation and governance | Current |
| `CLAUDE.md` | Claude Code entrypoint | Current |
| `AGENTS.md` | Agent framework entrypoint | Current |
| `.claude/edit-protocol.md` | Edit procedure | Current |
| `.claude/drift-check.md` | Alignment audit | Current |
| `_vocabulary/forge-context.jsonld` | JSON-LD vocabulary and @context | v0.1 — active design |
| `_vocabulary/intent-registry.md` | Named intent type definitions | Stub — needs design session |
| `_concepts/README.md` | Concept file format and usage | Current |
| `_concepts/three-layer-skill-architecture.md` | Formalized concept — Claude session | Current |
| `_concepts/manifest-as-coherence-anchor.md` | Formalized concept — Claude session | Current |
| `_concepts/intent-as-semantic-contract.md` | Formalized concept — Claude session | Current |
| `_concepts/forge-concept-lifecycle.md` | Formalized concept — Claude session | Current |
| `_concepts/session-citation-system.md` | Formalized concept — Claude session | Current |
| `_concepts/bom-binding-locked-composition.md` | Formalized concept — Claude/Gemini sessions | Current |
| `_concepts/semantic-graph-foundation.md` | Formalized concept — Claude session | Current |
| `_concepts/corpus-lifecycle-system.md` | Formalized concept — Claude session | Current |
| `_concepts/human-ai-role-separation.md` | Formalized concept — Claude session | Current |
| `_concepts/challenge-loop-methodology.md` | Formalized concept — Claude session | Current |
| `_concepts/statutory-urn-hybrid.md` | Formalized concept — Gemini session | Current |
| `_concepts/object-oriented-documentation.md` | Formalized concept — Gemini session | Current |
| `_concepts/actionable-intent-verses.md` | Formalized concept — Gemini/ChatGPT sessions | Current |
| `_concepts/conversational-concept-regression.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/concept-progression-record.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/stage-aware-guided-advancement.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/forge-guidance-engine.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/multi-model-deliberation-roles.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/capability-engineering-framework.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/world-specification.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/capability-trials.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/concept-capability-stratification.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/ai-arb-realization-system.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/forge-mobile-safe-core.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/evaluation-trust-plane.md` | Formalized concept — ChatGPT session | Current |
| `_concepts/promotion-as-transition.md` | Formalized concept — ChatGPT/skills-architecture session | Current |
| `_concepts/layered-skill-loading-architecture.md` | Formalized concept — ChatGPT/skills-architecture session | Current |
| `_concepts/skills-context-memory-separation.md` | Formalized concept — ChatGPT/skills-architecture session | Current |
| `_sessions/README.md` | Session excavation format and citation system | Current |
| `_sessions/2026-04-18-claude-general-docs/excavation.md` | Claude session excavation | Current |
| `_sessions/2026-04-18-claude-general-docs/index.jsonld` | Machine-readable session index | Current |
| `_sessions/chatgpt-forge-sessions/excavation.md` | ChatGPT sessions excavation (composite) | Current |
| `_sessions/2026-04-19-chatgpt-skills-architecture/excavation.md` | ChatGPT skills architecture session excavation | Current |
| `_sessions/2026-04-19-chatgpt-skills-architecture/index.jsonld` | Machine-readable session index | Current |
| `_intake/README.md` | Staging protocol for raw session content | Current |
| `_intake/chatgpt-forge-sessions/` | ChatGPT session source files | Current — 5 files |
| `_intake/chatgpt-forge-sessions/intake-notes.md` | Pre-annotation for ChatGPT excavation | Current |
| `_intake/gemini-sessions/2026-04-19-gemini-citation-modality/excavation.md` | Gemini session excavation | Current |
| `_intake/gemini-sessions/2026-04-19-gemini-citation-modality/intake-notes.md` | Gemini session intake notes | Current |
| `_parked/README.md` | Park mechanism documentation | Current |
| `_parked/intent-registry-design.md` | Parked concept | Current |
| `_parked/github-pages-output-pipeline.md` | Parked concept | Current |
| `_parked/boundarymark-fitness-attestation.md` | Parked concept | Current |
| `_parked/completeness-scoring-methodology.md` | Parked concept — still parked; canvas artifact not accessible | Current |
| `_parked/forge-naming-and-scope.md` | Parked concept | Current |
| `_skills/README.md` | Placeholder for corpus-skills sync | Stub |

---

## Design Decisions

These are the significant structural choices made during Forge development, recorded here so that future sessions do not relitigate them without awareness of the prior reasoning.

**Forge is domain-agnostic — Capability Engineering is a consumer, not a component**

Forge is a general-purpose knowledge lifecycle system. It applies equally to investment assessment, product strategy, policy analysis, creative work, legal reasoning, engineering, and any other domain where valuable concepts emerge from conversation and need to be preserved, matured, and made reusable. Forge's stages, the CPR, the Guidance Engine, and the citation system are domain-agnostic mechanisms.

Capability Engineering (CE) is one consumer of Forge — a rich consumer because the Operationalization stage maps well onto capability specification and trial-based validation, but a consumer nonetheless. The CE concepts in `_concepts/` (capability-engineering-framework, world-specification, capability-trials, etc.) belong here as formalized design knowledge that Forge has captured and can promote into a CE corpus template. Their presence does not make Forge a CE system.

Structural consequence: `_capabilities/`, `_worlds/`, `_invariants/`, `_trials/`, `_evidence/` directories and CE-specific rubric artifacts belong in a CE corpus template, not in this repo. The Forge North Star and all control layer documents must use domain-spanning examples and language, not CE-centric framing. CE may appear as one example alongside others.

**Forge stages are the progression spine — Operationalization is the handoff point to consumer domains**

The canonical Forge stage progression (Excavation → Qualification → Rationalization → Formalization → Operationalization) is domain-agnostic. Operationalization is the stage where a concept becomes trialable or executable — and that is where Forge hands off to domain-specific consumer machinery.

**Promotion is a routing transition, not a maturity stage**

Promotion was previously listed as a step in the canonical stage sequence between Rationalization and Formalization. This was incorrect. Promotion is the decision to route a concept into active use in a specific project corpus or downstream context. It is orthogonal to maturity — a concept can be promoted at any stage and can be promoted before or after full formalization. The canonical stage sequence is Excavation → Qualification → Rationalization → Formalization → Operationalization. Promotion, parking, and forking are working transitions that can occur at any point. This distinction was identified and formalized during the 2026-04-19 ChatGPT skills architecture session and the associated README rewrite (PR #5).

**CE concepts are correctly placed in `_concepts/` as design knowledge**

The presence of CE-focused concepts in the Forge concept registry is appropriate. They represent knowledge about how CE works that Forge has captured and may promote into a CE corpus template. Forge is a registry of knowledge, not a filter that excludes non-Forge-Core topics. The distinction is between concepts as knowledge (belongs here) and structural artifacts implementing CE (belongs in a CE template).

---

## Known Gaps and Future Work

| Item | Priority | Notes |
|---|---|---|
| Forge North Star artifact | Critical | A short canonical document stating what Forge is and is not. Must use domain-spanning examples, not CE-centric framing. |
| Forge canonical concepts document | Critical | Curated list of concepts with canonical/provisional status. Referenced in ChatGPT sessions as a core anti-regression artifact. |
| Forge stage model document | Critical | Clean single document describing each stage, inputs, outputs, exit criteria. Must reflect promotion-as-transition decision. |
| Forge progression rules document | High | The non-negotiable behavioral constraints. Referenced in ChatGPT sessions. |
| Completeness scoring methodology | High | Canvas document not accessible from ChatGPT export; partial treatment in sessions. Remains parked. |
| AI_ARB Work Item vs CPR relationship | High | Are these the same concept or distinct? Needs resolution before either is promoted to implementation. |
| `corpus-skills` repo creation | High | Shared reusable skills need a canonical home; `jwineland/corpus-skills` does not yet exist. |
| Repo hook convention | High | Common convention for AGENTS.md, MANIFEST.md, _skills/, _context/, _memory/ was sketched but not formalized. |
| `inherits` edge type in vocabulary | Medium | OOD inheritance currently mapped to `dependsOn`; may need a distinct edge type. |
| Actor tier in citation address | Medium | Whether AI platform/model should be a first-class tier or embedded in SESSION_ID. |
| WRP full scope definition | Medium | What does the broader WRP building contain beyond the AI_ARB nucleus? |
| AI Oversight vs Velocity session excavation | Medium | 796KB session not fully excavated; covers oversight/velocity tensions relevant to `human-ai-role-separation`. |
| CE corpus template | Medium | A dedicated corpus template for Capability Engineering work. Separate from Forge Core. |
| Automated excavation Action | High | Currently manual; GitHub Action to trigger on conversation deposit. |
| `corpus-skills` sync Action | High | `_skills/` should sync from jwineland/corpus-skills when it exists. |
| Intent registry design | High | `_vocabulary/intent-registry.md` is a stub; needs full design session. |
| GitHub Pages concept browser | Low | Rendered view of concept registry for navigation. |
| Cross-repo promotion Action | Medium | Automated PR creation when concept is promoted into a project repo. |

---

## Maintenance Protocol

1. Concepts are never deleted — they are archived with a reason
2. Session records are immutable once committed — corrections go in a separate amendment file
3. The vocabulary spec is versioned — breaking changes require a new version, not in-place modification
4. Parked concepts must have a trigger condition — open-ended parking is not permitted
5. Commit messages must identify the concept or session being affected, not just the file
