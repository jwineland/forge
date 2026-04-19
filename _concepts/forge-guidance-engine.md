---
id: forge-guidance-engine
name: Forge Guidance Engine
status: formalized
citation: forge:chatgpt-ai-tool-broker-forge-design:guidance-engine-design:exchange-25
created: 2026-04-19
depends-on: [stage-aware-guided-advancement, forge-concept-lifecycle, human-ai-role-separation]
related-to: [multi-model-deliberation-roles, forge-mobile-safe-core, concept-progression-record]
promoted-into: []
---

## Summary

The Forge Guidance Engine is the named architectural subsystem responsible for monitoring concept progression state, inferring the best next action, routing to the appropriate stage skill, and delivering targeted back-prompts to the human. It is the mechanism that makes stage-aware guided advancement operational rather than merely aspirational.

## Detail

### Three components

**1. Central Progression Controller**

Reads current concept state, determines stage maturity, spots missing prerequisites, chooses the next best stage action, and decides whether to ask the user, proceed automatically, or queue for later.

Operates on a state object such as:
```json
{
  "artifact_state": "provisionally_acceptable",
  "objective_gate_status": "pass",
  "subjective_confidence": 0.71,
  "judge_disagreement": 0.34,
  "evidence_completeness": 0.82,
  "recommended_next_action": "revise_and_rejudge"
}
```

**2. Stage-Specialized Skills / Subagents**

Purpose-bound workers that execute within a specific stage. Not generic subagents — stage-native workers with bounded scope:

- **Excavation skill** — surfaces latent concepts, splits entangled thoughts, identifies tensions and assumptions
- **Qualification skill** — determines what is real, distinct, and worth carrying forward; merges overlap; bounds definitions
- **Rationalization skill** — challenges concepts, improves wording, tests fit with existing architecture, identifies tradeoffs
- **Promotion skill** — captures concepts into durable project structures, classifies destination, assigns status and lineage
- **Formalization skill** — packages concept sets into formal outputs, creates grouped hierarchies, elicits missing rationale
- **Operationalization skill** — derives trialable/executable/measurable forms, builds world definitions, specifies invariants

**3. Back-Prompting Layer**

Interacts with the human sensibly rather than generically. Formulates the smallest useful ask. Recommends next move. Avoids lazy or broad questions.

Examples of good back-prompts:
- "These three concepts are mature enough for promotion. I recommend promoting the stage model first because later formalization depends on it."
- "This formalization pass is blocked on grouping. I can propose a hierarchy if you want."
- "The concept seems reusable across projects. Should I classify it for the shared registry?"
- "This looks like a plan-development branch rather than a design-development branch. I can derive a plan if you want to shift modes."

### Human authority model

Humans remain responsible for:
- Ratifying major directions
- Choosing among important tradeoffs
- Confirming canonical concepts
- Deciding when something should become authoritative

The Guidance Engine is responsible for:
- Noticing stage transitions
- Suggesting the right next move
- Doing bounded stage work
- Asking targeted questions
- Preserving continuity
- Packaging state for later work

### Relationship to evaluation

The Guidance Engine also incorporates evaluation awareness. Different stage outputs use different evaluation strategies (see `evaluation-trust-plane` concept). The controller uses evaluation signals — confidence, disagreement, evidence completeness — to determine next action, not just a simple pass/fail gate.

### Back-prompting trigger examples

The Guidance Engine should proactively surface situations such as:
- "We have added many key aspects to the design — we should forge it"
- "We have formalization work to do on concepts — here is the list and my suggested priority order"
- "Regression detected: the current framing of [concept] differs from the earlier canonical definition in [specific way]"
- "Carry-forward set for this session is ready — shall I emit it?"

## Open questions

- Implementation path: Python service, GitHub Action, Claude Code integration, or prompt-layer pattern?
- How stage skills are invoked: separate API calls, system prompt variants, or tool definitions?
- Confidence threshold calibration for autonomous vs. human-confirmed actions
- How the Guidance Engine persists state between sessions (the CPR / concept ledger is the mechanism, but the operational integration needs design)

## Promotion candidates

Core architectural concept for Forge system design. Required for any implementation of Forge beyond manual operation. Should produce a concrete design spec as the next artifact.
