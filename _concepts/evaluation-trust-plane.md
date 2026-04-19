---
id: evaluation-trust-plane
name: Evaluation and Trust Plane
status: formalized
citation: forge:chatgpt-ai-tool-broker-forge-design:evaluation-architecture:exchange-8
created: 2026-04-19
depends-on: [human-ai-role-separation, capability-engineering-framework]
related-to: [multi-model-deliberation-roles, forge-guidance-engine, capability-trials]
promoted-into: []
---

## Summary

Evaluation in Forge is a first-class subsystem, not a prompt. Informed by CMU LLM-as-judge research and TrustJudge findings, the evaluation and trust plane treats judge outputs as probability distributions rather than scalars, uses multiple evaluators to generate productive disagreement, and distinguishes between objective gates, structured semantic validation, and subjective strategic judgment.

## Detail

### The core implication of LLM-as-judge research

If Forge orchestrates design critique, code review, and loop progression, evaluation is one of the core control planes. A weak, biased, or overconfident evaluator turns the whole loop into a confidence amplifier for nonsense.

Key findings from CMU/TrustJudge work:
- Common judge patterns are internally inconsistent, especially when converting rich judgments into simple scores
- **Score-comparison inconsistency** and **pairwise transitivity failures** (A > B, B > C, yet C > A) are common
- For many subjective tasks there is no single "gold label" — assuming one produces false certainty
- Single-pass judge outputs are too brittle to safely steer autonomous systems

### Judge output schema (replacing scalar scores)

For each criterion, capture:

```json
{
  "criterion": "architectural_coherence",
  "verdict": "borderline",
  "confidence": 0.63,
  "uncertainty": 0.28,
  "evidence": ["service boundaries defined", "state ownership unclear"],
  "failure_modes": ["hidden coupling", "insufficient workflow ownership model"],
  "recommended_actions": ["formalize ownership per bounded context"]
}
```

This is better than "7.8/10" because Forge decisions are governance decisions, not leaderboard rankings.

### Three evaluation classes

**A. Deterministic validation** — tools, not judges. Schema valid, tests pass, code compiles, lint clean. Hard gates. These should run first, before any judgment-based evaluation.

**B. Structured semantic validation** — constrained evaluators with explicit criteria and evidence requirements. Does implementation match design? Does ADR contradict prior ADRs?

**C. Subjective/strategic judgment** — panel-style judging only. Never single-judge/single-score. Examples: Is this elegant? Is this over-engineered? Is this architecture likely to scale?

### Multi-judge disagreement as signal

Disagreement between judges should be treated as useful information, not noise to suppress. Disagreement may indicate: ambiguity in the task, underspecified rubric, domain subjectivity, insufficient evidence, or evaluator weakness. The controller asks "did judges agree enough to justify progressing?" — not just "did we get a high score?"

### Judge Qualification Profiles

Each evaluator (or ensemble) gets qualified for a domain:
- `judge_profile.architecture_review.v1`
- `judge_profile.python_code_quality.v2`
- `judge_profile.security_prompt_review.v1`

A model good at prose quality may be bad at systems code correctness. Forge should never treat judge capability as globally portable.

### Versioned rubrics as governed artifacts

Rubrics should be explicit artifacts with:
```yaml
id: forge.eval.architecture.coherence
version: 1.2.0
applies_to: [architecture_docs, service_designs]
criteria: [boundary_clarity, ownership_definition, dependency_direction]
required_evidence: [system_context, component_model, relevant_adrs]
escalate_if:
  - disagreement > 0.25
  - confidence < 0.65
  - contradiction_detected == true
```

### Escalation classes

- `auto-pass` — confidence high, deterministic gates passed, judges agree
- `auto-revise` — clear improvement path, low stakes
- `requires-human-approval` — disagreement high or stakes high
- `requires-domain-owner` — judgment requires specific expertise
- `blocked-insufficient-evidence` — cannot evaluate without more data

## Open questions

- Implementation of Judge Qualification Profiles — how calibration corpora are built and maintained
- Integration with the Forge Guidance Engine confidence signals
- Whether rubric storage should be in the Forge repo or a separate registry

## Promotion candidates

Core architectural component for Forge implementation. Should produce a concrete Evaluation and Trust Plane design spec. Informs the Forge Guidance Engine controller design and the capability trials evaluation model.
