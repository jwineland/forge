# Intake Notes: ChatGPT Forge Sessions

**Status:** Awaiting content deposit
**Prepared by:** Claude session 2026-04-18
**Purpose:** Pre-annotation to guide excavation once session content is placed here

## Known concepts to look for

Based on references in the April 18 Claude session, these concepts are known to exist in the ChatGPT Forge work:

### High priority (parked concepts depending on this content)

- **Completeness scoring methodology** — a quantitative approach to scoring how complete a concept is at each lifecycle stage. Expected to include: scoring dimensions, weights, threshold values for state transitions, and integration with the iterative prompting mechanism.

- **Human/AI prompted interchange design** — the formal design of how the AI proposes, the human validates, and incomplete items get surfaced for structured prompting. Expected to include: prompt templates, decision taxonomies, confidence thresholds.

### Medium priority (open questions in existing formalized concepts)

- **Concept fingerprinting algorithm** — how concept identity is computed for idempotent excavation. May be in the ChatGPT work or may need to be designed fresh.

- **Prior concept lifecycle version** — the ChatGPT version of the state machine may differ from the current one. Reconciliation needed; neither is automatically correct.

- **`forge this conversation` invocation design** — the slash command or equivalent trigger mechanism. May have been more fully designed in ChatGPT sessions.

### Cross-reference opportunities

The following concepts in `_concepts/` have open questions that ChatGPT sessions may answer:

| Concept | Open question |
|---|---|
| `human-ai-role-separation` | Confidence threshold for autonomous vs. prompted classification |
| `forge-concept-lifecycle` | Fingerprinting algorithm; session marker format |
| `challenge-loop-methodology` | Integration with completeness scoring |

## Suggested excavation approach

1. Start with the completeness scoring methodology — it is the highest-value parked concept and likely the most fully developed
2. Then reconcile the concept lifecycle state machine versions
3. Then extract any prompt templates or invocation designs
4. Cross-reference against existing `_concepts/` entries before creating new ones — many concepts may already be formalized here

## Notes on integration

The ChatGPT work predates the JSON-LD vocabulary and citation address system. Extracted concepts will need citation addresses assigned retroactively using approximate exchange numbers. Note this limitation in the session excavation record.
