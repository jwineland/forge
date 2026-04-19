---
id: multi-model-deliberation-roles
name: Multi-Model Deliberation Roles
status: formalized
citation: forge:chatgpt-ai-tool-broker-forge-design:multi-model-routing:exchange-20
created: 2026-04-19
depends-on: [human-ai-role-separation, challenge-loop-methodology]
related-to: [forge-guidance-engine, evaluation-trust-plane]
promoted-into: []
---

## Summary

Rather than using multiple AI models because "more models = more truth," Forge assigns deliberate cognitive roles to different models to create productive tension. The value is role specialization and independence of perspective, not averaging or consensus. Different models are assigned specific purposes that match their strengths and create adversarial coverage.

## Detail

### The four canonical roles

**Synthesizer**
- Turns chaos into coherent framing
- Produces candidate structures
- Unifies terminology
- Best for: early-stage concept formation, resolving conflicting inputs into a coherent proposal

**Adversarial Critic**
- Attacks assumptions
- Finds overreach, leakage, ambiguity
- Identifies failure modes and false novelty
- Best for: challenging mature concepts, finding what was missed, pressure-testing architectural decisions

**Implementation Grounder**
- Translates design into repo structure, services, APIs, tasks, contracts
- Says "this is what would actually need to exist"
- Best for: converting formalized concepts into buildable plans

**Consistency / Ratification Auditor**
- Compares against existing ADRs, docs, glossary, repo corpus
- Finds drift, contradiction, conceptual bleed
- Best for: integration checks, ensuring new concepts don't conflict with established ones

### What is NOT useful

> "I asked four models and they all kind of liked it."

This is distributed flattery with extra latency. Consensus among models that share overlapping training does not validate a design — it merely confirms that the design is internally coherent by the standards of that shared training. The challenge loop stopping criterion (absence of new substantive gaps) applies here: stop when models stop finding new issues, not when they start agreeing.

### Deliberation Packet

A structured bundle sent to a model for a deliberation run. Contains:

- The work item or concept under deliberation
- Relevant corpus excerpts and constraints
- The assigned role (Synthesizer, Critic, Grounder, Auditor)
- Required output format
- Anti-sprawl instructions specific to the role

This prevents every model interaction from starting from scratch and creates repeatability. It is the difference between "chatting with AI" and "running a design process."

### Integration with the Guidance Engine

The Forge Guidance Engine routes concepts to the appropriate model role based on the current stage and what kind of input is needed. Excavation-stage concepts benefit from a Synthesizer. Rationalization-stage concepts benefit from an Adversarial Critic. Formalization candidates benefit from an Implementation Grounder.

### Relationship to the challenge loop

This concept extends the cross-platform challenge loop methodology by adding explicit role assignments to the model invocations. The challenge loop provides the structural pattern; multi-model deliberation roles provide the semantic assignments within that structure.

## Open questions

- Whether role assignments should be model-specific (e.g., "Claude for synthesis, GPT for adversarial") or capability-agnostic (any model can fill any role)
- How to handle role assignments when only one model is available
- Integration with the evaluation trust plane — different roles produce different evidence types

## Promotion candidates

Candidate for the Forge Guidance Engine design spec. Should inform the Deliberation Packet schema design. Candidate for `_skills/challenge-loop-skill.md` update with role definitions.
