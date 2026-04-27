---
id: completeness-scoring-methodology
name: Completeness Scoring Methodology
status: formalized
citation: forge:chatgpt-ai-tool-broker-oversight-velocity:elevation-scorecard:exchange-approx
citation-quality: approximate
created: 2026-04-18
previous-status: parked
parked-created: 2026-04-18
unparked: 2026-04-26
unpark-source: _intake/chatgpt-forge-sessions/AI_Tool_Broker - AI Oversight vs Velocity.md
depends-on: [forge-concept-lifecycle, human-ai-role-separation, concept-progression-record]
related-to: [challenge-loop-methodology, forge-guidance-engine, stage-aware-guided-advancement, capability-trials, evaluation-trust-plane]
promoted-into: []
---

## Summary

A methodology for scoring the completeness of a concept at each lifecycle stage, enabling systematic identification of missing elements, directed iterative refinement, and a principled signal for when a concept is ready to advance. Scoring is stage-aware: different stages use different dimensions because different things must be true about a concept at each maturity level. Human judgment governs advancement; the scorecard guides and informs, but does not replace the human decision.

**Formalization note:** This concept is formalized as a usable Forge methodology. The open questions preserved below concern parameterization and integration refinements — such as threshold tuning, multi-model scoring, and CPR score-history schemas — rather than blockers to using the core methodology.

## Citation Quality Note

The citation is approximate because the source was deposited from prior ChatGPT session material rather than transcript-exact indexed exchanges. The methodology is preserved from the deposited intake source, but the exchange address should not be treated as transcript-exact until a stable session index exists for that source material.

## Unpark Note

This concept was parked on 2026-04-18 pending deposit of the source ChatGPT sessions. The sessions were subsequently deposited in `_intake/chatgpt-forge-sessions/`. The full scorecard methodology was excavated from `AI_Tool_Broker - AI Oversight vs Velocity.md`, which contains the `Idea Elevation Scorecard v0.1` with detailed category definitions, loop mechanics, and advancement rules. This is the primary source of the methodology below.

---

## Core Design Principles

**Goal is sufficiency, not perfection.** A concept advances when it is sufficiently useful for the next stage, not when it achieves a perfect score. The target is: "can this concept support the work required at the next stage?"

**Human judgment is the final authority.** The system may score, recommend continuation, recommend advancement, or recommend parking. The human decides. A human may override a low score and advance, or override a high score and demand further refinement.

**Scoring drives directed clarification, not interrogation.** The primary use of scores is to identify the weakest categories and direct targeted questions toward those categories. Clarification cycles should be bounded (1–3 questions per cycle) and aimed at material improvement, not exhaustive intake.

**Stage-specific scoring.** A concept at Excavation is evaluated against different criteria than one at Rationalization. The same score in a different stage means a different thing. Scorecards are calibrated to what matters at each stage.

**Lifecycle matters as much as content.** It is not enough to preserve what the concept is. The methodology must also preserve how it developed, what was challenged, what was discarded, and why it advanced.

---

## The Qualification Stage Scorecard (Primary Scorecard)

This is the `Idea Elevation Scorecard v0.1` from the source session, adapted to Forge vocabulary. It applies at the **Qualification stage** — the point where excavated material is being assessed for whether it is real, distinct, and worth carrying forward into Rationalization.

Each category is scored **0–5**.

### Score interpretation

| Score | Meaning |
|---|---|
| 0 | Absent — not present at all |
| 1 | Barely surfaced — mentioned but undeveloped |
| 2 | Emerging but weak — some shape visible, significant gaps |
| 3 | Usable / moderately clear — sufficient to reason from, not polished |
| 4 | Strong — well-developed, only minor gaps |
| 5 | Highly mature for this stage — could not be meaningfully improved at this level |

These are **concept-rationalization scores**, not execution-ready scores. A 3 in "Constraint/Requirement Emergence" at Qualification does not mean the concept has all its requirements — it means it has enough constraint visibility to support Rationalization work.

### Category 1: Problem Clarity

Can the problem, friction, or gap this concept addresses be clearly described? High score means the pain or motivation is legible and can be stated cleanly — not just "this feels interesting."

### Category 2: Tension Definition

Is the core contradiction, pressure, or tradeoff at the center of the concept clearly visible? Examples: speed vs. rigor, drift vs. fluidity, extraction vs. nuance, autonomy vs. human oversight. High score means we know what is in tension and the concept has a meaningful center.

### Category 3: Outcome Visibility

Can we describe what "better" would look like if this concept is realized? High score means plausible beneficial outcomes are visible — not necessarily measured yet, but enough to guide refinement and evaluate design alternatives.

### Category 4: User / Stakeholder Grounding

Do we know who this concept helps or who experiences the problem it addresses? High score means likely users or participants are visible — not abstract "someone." This is where user stories can begin to enter.

### Category 5: Use-Case Concreteness

Are there believable real scenarios where this concept applies? High score means at least 1–3 concrete examples exist and the concept is not purely abstract. Concreteness is a strong anti-naivety signal.

### Category 6: Structural Shape

Do we know what kind of thing this concept might become? Examples: command, workflow, tool capability, pattern, primitive, UI surface, review process, schema, registry. High score means the concept has a plausible form even if not yet finalized.

### Category 7: Constraint / Requirement Emergence

Have meaningful constraints, requirements, or invariants started to emerge? Examples: "must preserve lineage," "must not depend on model memory," "must work on mobile," "must support multi-model review." High score means real "musts" are becoming visible — this is where hard requirements start to crystallize.

### Category 8: Challenge / Adaptation Maturity

Has the concept been meaningfully challenged and improved? High score means objections have been surfaced, assumptions have been refined, and the concept has demonstrably changed in response. This is a critical category — a concept that has not been challenged is unlikely to be well-grounded.

### Category 9: NIH / Existing Solution Awareness

Have existing solutions, adjacent approaches, or prior art been adequately considered? High score means relevant existing approaches have been considered and the concept understands whether it is adapting, extending, or genuinely creating something new. This is a mandatory anti-naivety safeguard — a concept should not proceed without this.

### Category 10: Advancement Readiness

Is this concept now structurally useful enough to advance into Rationalization — critique, deeper requirement framing, design alternatives, architectural implications? High score means the concept is coherent enough to support that work. This is the summary category: "can we leave Qualification?"

---

## Stage-Specific Scoring Dimensions

The Qualification scorecard above is the primary scorecard. Other lifecycle stages use different evaluation emphases because different things must be true at each stage. These are directional — the Qualification scorecard is fully specified; the others describe evaluation focus.

### Excavation stage evaluation focus

At Excavation, the goal is surfacing, not scoring. Evaluation is qualitative:
- Novelty: is this something worth capturing?
- Distinctiveness: is this a new concept or a restatement of something existing?
- Latent richness: does this have enough depth to warrant Qualification?
- Entanglement: is this one concept or several that need separation?

### Qualification stage (full scorecard above)

Categories 1–10, scored 0–5. This is the primary quantitative scoring point.

### Rationalization stage evaluation focus

- Architectural fit: does this concept belong in the design? Does it conflict with existing concepts?
- Consistency: is the concept internally coherent and consistent with Forge principles?
- Necessity: is this concept genuinely needed, or does an existing concept cover it?
- Elegance: is this the cleanest framing, or is there a better way to express the same idea?
- Tradeoff quality: have the design tradeoffs been honestly surfaced and addressed?

### Formalization stage evaluation focus

- Clarity: is the concept expressed precisely enough for others to use it without ambiguity?
- Completeness: are all required fields and sections present?
- Portability: can this concept be reused across projects and contexts?
- Reusability: is it expressed at the right level of abstraction for reuse?
- Structural soundness: does the concept record structure follow Forge conventions?

### Operationalization stage evaluation focus

- Testability: can claims about this concept be verified through trials?
- Observability: can the concept's behavior be observed in a world specification?
- Falsifiability: can the concept be shown to be wrong, and how?
- Trialability: can Capability Trials be written against this concept?
- Execution readiness: is this concept ready to be implemented by an execution agent?

---

## Loop Mechanics

### The Qualification loop pattern

```text
Enter concept → Discuss / examine → Score all categories → Identify weakest
→ Ask 1–3 targeted clarifying questions on weakest categories
→ Refine concept based on answers → Re-score → Decide: continue or advance
```

The loop repeats as many times as needed. There is no mandatory hard loop limit. Each cycle should aim to materially improve the concept's structural usefulness — if a cycle produces no meaningful maturity gain, stop and decide.

### Exit conditions

The Qualification loop exits when one of the following is true:

**A. Ready to advance to Rationalization** — the concept is sufficiently structured to be meaningfully pressure-tested against the design. Category 10 (Advancement Readiness) is high, and the overall score profile supports advancement.

**B. Needs more Excavation** — the concept is still too under-formed. Return it to Excavation with specific guidance on what is missing.

**C. Park** — the concept is not worth current advancement. Record park rationale and trigger conditions.

**D. Human checkpoint** — a useful milestone has been reached and the human wants to pause without advancing. Produce the best current artifact and preserve state.

### Clarification rules

Clarifying questions should:
- Improve weak score categories
- Reduce blocking ambiguity
- Increase structural usefulness
- Help the concept move toward a clearer next stage

Clarifying questions should not:
- Become a bureaucratic intake form
- Ask questions that are merely nice to have
- Force precision prematurely
- Continue endlessly without meaningful maturity gain

Recommended pattern: **1–3 questions per clarification cycle**, clustered by theme, in the same conversational style as the broader discussion.

### Clarification target selection

Clarification should target categories where improvement would most meaningfully strengthen the concept:
- Lowest-scoring categories
- Categories that are blocking advancement
- NIH uncertainty (Category 9) when poorly scored
- Use-case weakness (Category 5) when the concept remains abstract
- Constraint emergence (Category 7) when the concept has no visible requirements

---

## Integration with Concept Progression Record

The CPR (`concept-progression-record`) already tracks `stage`, `status`, and `current_definition`. The completeness scorecard integrates as follows:

- **Score at Qualification:** When a concept is in Qualification, a scorecard run produces per-category scores and a weighted profile. This populates the CPR's `readiness_signals` and `open_questions` fields.
- **Carry-forward:** The lowest-scoring categories and their recommended clarification questions become carry-forward items in the CPR's `carry_forward_points`.
- **Advancement gate:** The scorecard's Category 10 (Advancement Readiness) is the primary input to the CPR's `stage_advancement_recommendation`. A high Category 10 score combined with acceptable scores across other categories (no category below 2, no blocking gaps in categories 7 or 9) constitutes a recommendation to advance.
- **Regression detection:** A concept that was scored at Qualification and then regressed in a subsequent session should show lower scores. This signals drift and should trigger a rationalization task.

---

## Integration with Forge Guidance Engine

The Guidance Engine (`forge-guidance-engine`) reads concept state and back-prompts the user with recommended next actions. The scorecard gives the Guidance Engine concrete signals:

- When a concept at Qualification has no recent score: recommend running `/score`
- When Category 10 is ≥ 4 and no category is below 2: recommend advancement to Rationalization
- When Category 9 is ≤ 1: block advancement and surface NIH concern
- When Category 8 is ≤ 2: recommend a challenge-loop pass before advancement
- When multiple categories are ≤ 1: recommend continued Excavation rather than Qualification

This gives the Guidance Engine a structured basis for proactive back-prompting rather than requiring the human to manually assess concept readiness.

---

## Advancement Rules

**Principle:** A concept advances when it is sufficiently useful for the next stage, not when it achieves a perfect score.

**Authority:** Human judgment is the final authority. The scorecard recommends; the human decides.

**Typical advancement pattern:**

| Transition | Readiness signal |
|---|---|
| Excavation → Qualification | Concept is worth preserving and has some shape |
| Qualification → Rationalization | Category 10 ≥ 4; no category at 0; no blocking gap in categories 7, 9 |
| Rationalization → Formalization | Concept is architecture-coherent, internally consistent, and necessary |
| Formalization → Operationalization | Concept can be expressed as trials, invariants, and world specifications |

**Human override:** A human may say "I know the score suggests continuation, but I want to advance" or "I know the score is high, but I want one more challenge loop." Both are valid. The scorecard is an input to human judgment, not a replacement for it.

---

## Command Vocabulary (Forge Adaptation)

The source sessions used slash commands. Translated to Forge vocabulary:

| Source command | Forge equivalent |
|---|---|
| `/elevate` | Excavate and score — extract structured concept artifact, produce scorecard, identify weak areas |
| `/score` | Score all categories, explain each score, identify weakest, recommend focus |
| `/clarify` | Run targeted refinement loop on 1–3 weakest categories |
| `/qualify` | Transition to or operate within Qualification stage |
| `/advance` | Formally exit current stage and advance to next |
| `/park` | Defer with rationale and trigger conditions |
| `/finalize-stage` | Checkpoint without advancing — produce best current artifact |

---

## Open Questions

The following open questions are preserved as integration and parameterization refinements. They do not block use of the core methodology as a formalized Forge concept.

- Should the Qualification scorecard be the only quantitative scorecard, with other stages evaluated qualitatively? Or should Rationalization and Formalization also have structured 0–5 scorecards?
- What is the minimum acceptable score profile for Qualification → Rationalization advancement? The current guidance (Category 10 ≥ 4, no category at 0, no blocking gap in 7 or 9) is directional — should it be more precisely specified?
- Should the Guidance Engine enforce score thresholds, or only suggest them? Strong enforcement may conflict with the principle that humans govern advancement.
- How should the scorecard integrate with multi-model challenge loops? Should different models score independently and disagreement be tracked?
- Should concept scores be versioned and time-stamped in the CPR so regression can be detected across sessions?

## Promotion Candidates

Core input to the Guidance Engine and stage-aware advancement. Critical for the guidance layer MVP — without a defined scoring mechanism, the Guidance Engine cannot make principled back-prompting recommendations about concept readiness. Connects directly to `capability-trials` as the source of trial-readiness signals at Operationalization stage.
