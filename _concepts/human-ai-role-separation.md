---
id: human-ai-role-separation
name: Human/AI Role Separation
status: formalized
citation: forge:2026-04-18-claude-general-docs:forge-design:role-separation
created: 2026-04-18
depends-on: []
related-to: [forge-concept-lifecycle, corpus-lifecycle-system]
promoted-into: []
---

## Summary

Humans declare direction, validate proposals, and approve state transitions. AI agents execute graph operations, propose classifications, detect drift, and generate structured options for human decision points. This separation must be encoded in the framework as a first-class architectural principle, not just a workflow convention.

## Detail

### Decision surfaces vs autonomous zones

**Decision surface** — a defined point where the system pauses for human input. The question has no objectively correct answer derivable from the declared constraints. Example: the hybrid YAML/prompted instantiation path, concept promotion approval, park trigger definition.

**Autonomous zone** — an operation the AI executes without prompting because the criteria are fully specified and the action is deterministic given the inputs. Example: drift detection, graph traversal, delta excavation, file registry enumeration.

The framework's job is to maximize autonomous operation while surfacing only genuine decision points. The failure mode to avoid: asking humans to validate things that can be inferred (wastes human attention), and making decisions that require human judgment without asking (creates unaccountable outputs).

### Encoding in the system

The YAML pre-declaration path and the AI-prompted path are both inputs to the same resolver. The resolver maximizes autonomous operation and surfaces only genuine decision points — never asks for information it can infer, never decides what requires human judgment.

This principle applies across all Forge operations: excavation (AI proposes, human approves), concept classification (AI classifies, human validates uncertain cases), promotion (AI generates PR, human merges), drift detection (AI detects, human decides whether to fix or accept).

## Open questions

- Formal specification of decision surface criteria (what makes something a genuine decision point vs an autonomous operation)
- Confidence threshold for autonomous classification vs. surfacing for human review
- Integration with completeness scoring from ChatGPT Forge work

## Promotion candidates

Core principle for Forge system design. Candidate for `corpus-seed.yaml` schema design (governs instantiation flow). Candidate for all template repo CLAUDE.md files.
