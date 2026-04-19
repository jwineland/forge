---
id: concept-progression-record
name: Concept Progression Record (CPR)
status: formalized
citation: forge:chatgpt-ai-tool-broker-forge-design:anti-regression-primitives:exchange-18
created: 2026-04-19
depends-on: [forge-concept-lifecycle, conversational-concept-regression]
related-to: [session-citation-system, manifest-as-coherence-anchor, stage-aware-guided-advancement]
promoted-into: [forge:_concepts/forge-concept-lifecycle.md]
---

## Summary

A small, explicit, durable object that carries the current state of a concept across conversation turns, sessions, and AI platforms. The CPR is the primary anti-regression primitive — the "ratcheting concept ledger" that prevents meaningful conceptual work from dissolving into conversational residue.

## Detail

The CPR was identified as the missing bridge between conversation and formal design documents. Without it, every new refinement pass must reconstruct the design from fragments, and meaningful distinctions get dropped.

### Why "ratcheting"

The key property is that concepts can move forward, be refined, gain links, and gain formality — but they do not silently disappear. A concept may evolve, merge, be superseded, or be archived — but it cannot simply evaporate because the next turn sounded smoother. The ratchet is the mechanism that enforces this.

### Schema

Each CPR entry carries:

```yaml
id: stable-concept-identifier
name: Human-readable concept name
stage: excavated | classified | formalized | parked | promoted | forked | archived
status: canonical | likely-canonical | provisional | superseded
current_definition: The current best statement of the concept
why_it_matters: Why this concept is worth preserving
carry_forward_points: Must-not-drop assertions about this concept
new_discoveries: Things learned about this concept in the most recent session
open_questions: Unresolved aspects that block full formalization
related_concepts: [list of concept IDs]
promotion_targets: Where this concept could or should be promoted
supporting_artifacts: Citations pointing to source conversations
regression_risks: Specific ways this concept has been or could be misrepresented
```

### The Concept Ledger

The CPR at the individual concept level aggregates into a **Concept Ledger** — the full collection of active CPR entries for a project. The ledger is the continuity spine. Every serious AI-assisted design session should read from and write to the ledger.

The ledger is not the same as formal design documents. It is smaller, more frequently updated, and focused on preserving conceptual state rather than producing final outputs. It is the ratchet layer that formal documents depend on.

### Relationship to the Forge concept registry

The `_concepts/` directory in the Forge repo is the implementation of the Concept Ledger. Each concept file is a CPR entry. The MANIFEST.md file registry and known gaps table are the aggregate projection of the ledger state.

### Carry-Forward Set

A companion primitive: at the end of any significant session, the system emits a compact **Carry-Forward Set** — a short list of must-not-drop points from that session. This is the session-level version of the CPR. It is designed to be phone-safe: compact enough to read and produce on mobile.

Example carry-forward set output:
- Forge core stages are excavation, qualification, rationalization, promotion, formalization, with operationalization as provisional
- Forge is a structured method for advancing meaningful work from conversation
- Promotion is the capture boundary between conversation and retained project knowledge
- CPR is the ratcheting primitive that prevents concept loss between sessions

## Open questions

- How carry-forward sets are automatically generated vs. manually curated
- Integration with completeness scoring to determine when a CPR entry is ready to advance to next stage
- Storage format: the current `_concepts/*.md` pattern works for the repo but may not be optimal for in-session use

## Promotion candidates

Core concept for Forge system design. The `_concepts/` directory structure is the current implementation. Should be referenced in the Forge North Star artifact when created.
