---
id: stage-aware-guided-advancement
name: Stage-Aware Guided Advancement
status: formalized
citation: forge:chatgpt-ai-tool-broker-forge-design:proactive-advancement:exchange-22
created: 2026-04-19
depends-on: [forge-concept-lifecycle, human-ai-role-separation, concept-progression-record]
related-to: [forge-guidance-engine, forge-mobile-safe-core, conversational-concept-regression]
promoted-into: []
---

## Summary

Forge must not depend on the human to manually direct every stage transition. Instead, the system monitors concept maturity, recognizes when stage transitions are warranted, and proactively back-prompts the human with specific recommendations — rather than waiting passively for instructions. This is a hard requirement, not an optional enhancement.

## Detail

If Forge requires constant manual stage-driving by the human, it is not solving the core problem. It is providing a better whiteboard while leaving the human as the continuity engine. That is the burden Forge is designed to reduce.

### The distinction: guided initiative vs. blind autonomy

Stage-aware guided advancement is not autonomous operation. It is the system saying:

- "We have enough surfaced material to qualify now — here are the candidates."
- "These concepts appear mature enough for promotion."
- "Formalization is blocked on invariants and grouping decisions — here is what I need from you."
- "There are three plausible next refinement paths; here is the one I recommend and why."
- "This looks like a world-definition gap — shall I draft one?"
- "These concepts are drifting and should be reconciled before we continue."

The human retains authority to approve, redirect, or refine. The system takes responsibility for noticing, proposing, and executing.

### What the system must monitor

For each active concept or concept cluster:

- Current stage and confidence in stage placement
- Readiness signals for stage advancement
- Missing prerequisites that block advancement
- Regression risks that need flagging
- Cross-concept coherence issues

### The back-prompting pattern

The system should not ask:
> "What do you want to do next?"

It should ask:
> "Here is the best next move and why. Approve, redirect, or refine."

This is the difference between a passive tool and a proactive design partner. The key is that the question is always bounded — not "what should we do" but "should we do this specific thing."

### Stage-readiness schema

For each active concept, the system should track:

```yaml
concept: concept-id
current_stage: excavation | qualification | rationalization | promotion | formalization | operationalization
readiness_to_advance: high | medium | low
recommended_next_action: specific action description
recommended_skill: excavation-skill | qualification-skill | etc.
human_confirmation_required: true | false
blocking_issues: [list of what prevents advancement]
suggested_back_prompt: >  
  Specific proposed question or recommendation text
```

### Relationship to the Forge Guidance Engine

Stage-aware guided advancement is the behavioral requirement. The Forge Guidance Engine is the architectural subsystem that implements it. The two concepts are related but distinct — this concept defines what must happen, the Guidance Engine concept defines how it is built.

### Mobile-safe considerations

On mobile/phone, the back-prompting model becomes even more important. The user cannot manually orchestrate complex structure-heavy work on a small screen. Forge should do more of the orchestration and ask for less, but better, human input. The back-prompt must be:

- Compact enough to read on mobile
- Specific enough to answer with a single decision
- Clear enough that the user doesn't need to reconstruct context to respond

## Open questions

- Formal specification of readiness signals — what observable properties of a concept indicate it is ready to advance?
- Confidence threshold for autonomous action vs. requiring human confirmation
- How to handle cases where the system's recommended path conflicts with the human's implicit direction from prior turns

## Promotion candidates

Core behavioral requirement for Forge system design. Should be a first-class section in the Forge Progression Rules artifact. Candidate for the Forge Guidance Engine design spec.
