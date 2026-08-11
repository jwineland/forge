---
id: challenge-loop-methodology
name: Cross-Platform Challenge Loop Methodology
status: formalized
citation: forge:2026-04-18-claude-general-docs:review-methodology:loop-design
created: 2026-04-18
depends-on: [human-ai-role-separation]
related-to: [manifest-as-coherence-anchor, forge-concept-lifecycle]
promoted-into: [general_docs:_skills/challenge-loop-skill.md, general_docs:.claude/review-prompt.md]
---

## Summary

Systematically reviewing a document or corpus across multiple AI platforms surfaces gaps with higher confidence than single-platform review. The value is not consensus but independence — platforms trained on overlapping corpora share blind spots, so the stopping criterion is absence of new substantive gaps, not platform agreement.

## Detail

### The loop structure

1. **Comprehension verification** — run first on every platform before issuing any challenge. Prevents acting on reviews based on misread content.
2. **Reviewer role assignment with structured output** — one finding per row, not prose. Gap | Location | Severity | Finding | Proposed resolution.
3. **Cross-platform synthesis** — consensus gaps (2+ platforms), platform-unique findings, contradictions, prioritized action list.
4. **Incorporation decisions** — for each finding: incorporate as proposed / incorporate with modification / reject with reason / defer. Document all rejections.

### Stopping criterion

Stop when two consecutive rounds produce no new CRITICAL or MAJOR findings. Convergence on tone or praise is not the signal. Absence of new substantive gaps is.

### Independence caveat

The independence assumption is weaker than it appears. GPT-4, Gemini, and Claude share largely overlapping training corpora. When all three miss something, it is more likely because the gap is invisible to all three than because the thing is not a gap. Consensus represents high confidence within the shared knowledge base — not high confidence in an absolute sense.

### Integration with intent

If content intent declares the decision being supported and the primary audience, the challenge loop can select the adversarial reviewer role automatically — specifically choosing the perspective most likely missing from the authoring session.

Reviewer roles are bounded task stances for structured critique. They are not hidden system prompts, prompt-injection mechanisms, or authorization to bypass a tool's active instruction hierarchy. See `SECURITY.md`.

## Open questions

- Integration with completeness scoring from ChatGPT Forge work
- Automated reviewer role selection from intent declarations not yet implemented

## Promotion candidates

Already promoted into `general_docs`. Candidate for all corpus template repos.
