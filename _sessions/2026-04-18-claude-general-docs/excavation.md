# Session Excavation: 2026-04-18 — Claude — general_docs and Forge Design

**Session ID:** `2026-04-18-claude-general-docs`
**Platform:** Claude (Sonnet 4.5)
**Date:** 2026-04-18
**Context:** Investment assessment framework development, corpus architecture design, Forge system design
**Excavation type:** Manual bootstrap — automated excavation not yet available
**Note:** Exchange numbers are approximate in this manual record.

---

## Thread Index

| Thread ID | Description | Approximate span |
|---|---|---|
| `investment-framework` | Investment assessment framework content work | Session start through PR #3 |
| `corpus-architecture` | MANIFEST, skills, agent files design | PR #3 planning through PR #6 |
| `review-methodology` | Multi-platform challenge loop discussion | Mid-session |
| `systematization` | Systematization and template repo discussion | Post-PR #6 |
| `forge-design` | Forge concept registry and lifecycle design | Late session |
| `semantic-graph-intent` | Semantic graph, JSON-LD, intent architecture | Final session |

---

## Concepts Extracted

| Concept ID | Status | Thread | Citation |
|---|---|---|---|
| three-layer-skill-architecture | formalized | corpus-architecture | `forge:2026-04-18-claude-general-docs:corpus-architecture:skill-layer-design` |
| manifest-as-coherence-anchor | formalized | corpus-architecture | `forge:2026-04-18-claude-general-docs:corpus-architecture:manifest-design` |
| intent-as-semantic-contract | formalized | semantic-graph-intent | `forge:2026-04-18-claude-general-docs:semantic-graph-intent:intent-abstraction` |
| forge-concept-lifecycle | formalized | forge-design | `forge:2026-04-18-claude-general-docs:forge-design:lifecycle-design` |
| session-citation-system | formalized | forge-design | `forge:2026-04-18-claude-general-docs:forge-design:citation-design` |
| bom-binding-locked-composition | formalized | semantic-graph-intent | `forge:2026-04-18-claude-general-docs:semantic-graph-intent:manufacturing-pattern` |
| semantic-graph-foundation | formalized | semantic-graph-intent | `forge:2026-04-18-claude-general-docs:semantic-graph-intent:graph-design` |
| corpus-lifecycle-system | formalized | corpus-architecture | `forge:2026-04-18-claude-general-docs:corpus-architecture:lifecycle-design` |
| human-ai-role-separation | formalized | forge-design | `forge:2026-04-18-claude-general-docs:forge-design:role-separation` |
| challenge-loop-methodology | formalized | review-methodology | `forge:2026-04-18-claude-general-docs:review-methodology:loop-design` |

---

## Promoted Concepts

| Concept | Promoted Into | Notes |
|---|---|---|
| three-layer-skill-architecture | general_docs:_skills/, CLAUDE.md, AGENTS.md | Fully implemented in PRs #3 and #4 |
| manifest-as-coherence-anchor | general_docs:MANIFEST.md | Core structure of all MANIFEST files |
| challenge-loop-methodology | general_docs:_skills/challenge-loop-skill.md | Implemented and reconciled in PR #5 |
| corpus-lifecycle-system | general_docs:MANIFEST.md | Partially implemented |
| session-citation-system | forge:MANIFEST.md | Bootstrap implementation |
| forge-concept-lifecycle | forge:MANIFEST.md | Bootstrap implementation |
| semantic-graph-foundation | forge:_vocabulary/forge-context.jsonld | v0.1 vocabulary |

---

## Parked Concepts

| Concept | Park File | Trigger |
|---|---|---|
| intent-registry-design | _parked/intent-registry-design.md | When Forge schema design session begins |
| github-pages-output-pipeline | _parked/github-pages-output-pipeline.md | When corpus-template-doc is created |
| boundarymark-fitness-attestation | _parked/boundarymark-fitness-attestation.md | When BoundaryMark design resumes |
| completeness-scoring-methodology | _parked/completeness-scoring-methodology.md | When ChatGPT Forge session is deposited |
| forge-naming-and-scope | _parked/forge-naming-and-scope.md | When corpus-template repos are created |

---

## Open Threads

| Thread | Description | Blocks |
|---|---|---|
| ChatGPT Forge session deposit | Prior ChatGPT work on completeness scoring and concept lifecycle needs to be deposited and integrated | completeness-scoring-methodology promotion, human-ai-role-separation open questions |
| corpus-seed.yaml schema design | Full schema with intent section not yet designed | corpus-template-doc, corpus-template-eng creation |
| Intent registry design | Named intent types and content contracts not yet specified | intent-as-semantic-contract promotion, output materialization |
| Forge naming finalization | "Forge" confirmed; sub-component naming (Forge Core, Forge Corpus, Forge Compose, Forge Graph) proposed but not decided | Architecture documentation |
| corpus-skills repo creation | Shared _skills/ library repo not yet created | All template repo work |
