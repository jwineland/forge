# Design Note: Retaining Cost Accounting and Classification from the Original Session

**Status:** Design retention note requiring review  
**Date:** 2026-04-26  
**Related session:** `2026-04-26-chatgpt-forge-drone-orchestration`  
**Purpose:** Verify that the original cost-accounting and usage-classification ideas that started this session remain preserved after later review emphasis shifted toward Atlas, federation, and drones.

---

## 1. Why This Note Exists

The session began with a practical economic question:

> How can the user monitor ChatGPT Pro / Codex subscription usage and estimate what equivalent API billing would have cost?

As the session progressed, the design focus expanded into drone orchestration, Design Atlas, global coherence, project-local Forge layers, and federated graphs.

This note confirms that the original cost-accounting ideas are still part of the design and should not be lost during rationalization.

---

## 2. Original Motivation

The user's acceptable actual subscription spend may be roughly hundreds of dollars per month, while API-equivalent usage for their preferred workflow could plausibly be several thousand dollars per month.

The core economic issue is not ordinary chat volume. It is the combination of:

- long-running design development
- repeated authority-document or Atlas-level coherence review
- high-reasoning frontier model challenge loops
- multi-model critique and synthesis
- GitHub/MCP-mediated context retrieval
- implementation planning
- prompt/handoff generation
- Codex / Claude Code implementation work
- tool calling and artifact cycling

The initial tracking problem therefore evolved into a cost architecture problem:

```text
Preserve high-value frontier reasoning while avoiding accidental metered frontier-model burn.
```

---

## 3. Usage Classification Scheme to Retain

The following usage classes should remain in the design model.

| Usage class | Description | Primary cost driver | Likely accounting unit |
|---|---|---|---|
| Quick chat | Small question/answer, no artifacts | output tokens | conversation/thread |
| Design discussion | Planning, reasoning, architecture exploration | reasoning + context | design session |
| Authority-doc cycle | Full or near-full document review/update/re-review | repeated large input | artifact cycle |
| Modular design packet review | Bounded context packet reviewed by frontier model | curated packet + reasoning | packet review |
| Atlas/global coherence review | Whole-design compressed survey | Atlas digest + frontier reasoning | Atlas review cycle |
| GitHub/MCP retrieval cycle | Model gathers repo/design context through tools | files read + summaries + tool output | tool cycle |
| Design rationalization | Resolve conflicts, weave concepts, formalize decisions | reasoning + selected context | rationalization cycle |
| Implementation planning | Convert design into plan/tasks/tests | design packet + output | plan cycle |
| Prompt/handoff generation | Produce Codex/Claude Code/Cline prompts | context compression + output | handoff artifact |
| Implementation-agent work | Codex/Claude Code/Cline execution | repo reads, tool calls, test output | implementation session |
| Verification/reconciliation | Compare output to frozen design intent | diffs + plan + Atlas links | verification cycle |

This classification should survive any later schema design. Exact token estimates may change, but these work modes are central to understanding the user's cost profile.

---

## 4. Cost Classes to Retain

The Green/Yellow/Red/Black classification is still relevant and should not be reduced to a minor implementation detail.

| Class | Meaning | Typical models/surfaces | Approval posture |
|---|---|---|---|
| Green | Local or very cheap housekeeping | local model, deterministic script, cheap API | run freely within policy |
| Yellow | Bounded utility or synthesis | cheap/standard API, local+validation | capped; maybe auto-run |
| Red | Frontier reasoning or high-impact design work | subscription frontier or approved API | explicit approval or subscription routing |
| Black | Multi-frontier debate or large-context frontier loops | multiple frontier models, large Atlas/authority review | exceptional approval only |

These classes should apply to:

- drone jobs
- prompt dispatches
- design review cycles
- Atlas review cycles
- implementation planning cycles
- implementation-agent sessions
- API fallback/escalation events

---

## 5. Subscription/API/Local Ledger Model

The design should distinguish three different economic ledgers.

### 5.1 Actual subscription spend

Actual monthly spend for subscription surfaces, such as ChatGPT Pro, Codex subscription access, Claude Pro/Max, Claude Code subscription use, etc.

This ledger answers:

```text
What did the user actually pay?
```

### 5.2 API-equivalent estimate

Estimated cost if the same work had been performed through metered APIs.

This ledger answers:

```text
What would this likely have cost through API billing?
```

### 5.3 Automation/API logistics spend

Actual API spend for low-cost drones, local-fallback escalation, dispatch automation, summarization, validation, and other utility work.

This ledger answers:

```text
How much did automation cost to reduce human message-bus burden?
```

Together:

```text
Total actual cost = subscription spend + automation/API logistics spend + local infrastructure amortization if tracked

Estimated value = API-equivalent estimate of subscription-surface work + API-equivalent estimate of implementation work avoided/contained
```

---

## 6. Session-Based Accounting Principle

The session moved away from per-message accounting toward a work-cycle model.

This should be retained.

Reason: the user's work is not best represented as individual messages. It is represented as design and implementation cycles:

```text
context gather → packetize → challenge → rationalize → plan → handoff → implement → verify → reconcile
```

Cost accounting should therefore attach to artifacts and cycles, not only chat turns.

Candidate accounting units:

- `DesignSession`
- `ArtifactCycle`
- `PacketReview`
- `AtlasReview`
- `RationalizationCycle`
- `ImplementationPlanCycle`
- `HandoffArtifact`
- `ImplementationSession`
- `VerificationCycle`
- `DroneJob`

---

## 7. Relationship to Design Atlas

The Atlas concept changes cost accounting in an important way.

Historical full-authority-document cycling had a cost:

```text
full document repeatedly processed by frontier models
```

Atlas introduces a replacement cost:

```text
local/API drones maintain map + frontier models periodically review compressed global digest
```

The economic comparison is therefore not simply:

```text
old full doc tokens vs. new modular packet tokens
```

It is:

```text
old full-authority cycles
vs.
Atlas maintenance + packet work + periodic global coherence reviews
```

The tracker should eventually measure whether Atlas reduces total API-equivalent cost while preserving or improving global coherence.

---

## 8. Relationship to Federated Project-Local Forge

Federated project-local Forge layers add another accounting dimension.

Cost may occur in:

- primary Forge registry work
- project-local Atlas maintenance
- project-local implementation planning
- cross-project concept promotion/back-promotion
- drift checks between global and project-local concepts
- synchronization of manifests, graphs, handoffs, and implementation evidence

Cost classification should therefore include a scope field:

| Scope | Example |
|---|---|
| `forge-registry` | concept rationalization in primary registry |
| `project-local` | project Atlas update or plan generation |
| `cross-project` | promotion/back-promotion of reusable concept |
| `implementation` | Codex/Claude Code execution work |
| `verification` | drift or acceptance check |

---

## 9. Relationship to Drones / Workers

Drones should not be evaluated only by capability. They should also be evaluated by economic role.

| Drone role | Expected cost class | Economic purpose |
|---|---|---|
| Index drone | Green | Reduce frontier context gathering |
| Classifier drone | Green/Yellow | Preserve concept metadata cheaply |
| Summarizer drone | Green/Yellow | Compress context before frontier review |
| Packet drone | Green/Yellow | Bound expensive model inputs |
| Drift drone | Green/Yellow | Detect risk before expensive review |
| Handoff drone | Yellow | Reduce manual transfer/error burden |
| Verification drone | Yellow | Avoid expensive rework and incoherence |
| Frontier critic | Red | High-quality design challenge |
| Frontier design court | Red/Black | Multi-model high-reasoning adjudication |
| Implementation drone | Yellow/Red | Execute plans, depending on model/scope |

The Cost Governor drone is therefore not optional long-term. It is the mechanism that prevents the operational layer from defeating the subscription/API hybrid cost strategy.

---

## 10. Minimum Fields for Future Cost Logging

No implementation is authorized by this note. However, future cost logging likely needs at least these fields:

| Field | Purpose |
|---|---|
| `cycleId` / `jobId` | Stable identity for accounting unit |
| `scope` | forge-registry, project-local, cross-project, implementation, verification |
| `workClass` | design discussion, Atlas review, handoff, implementation, etc. |
| `costClass` | Green, Yellow, Red, Black |
| `surface` | ChatGPT, Codex, Claude, Claude Code, API, local, MCP, GitHub |
| `modelTier` | local, cheap API, standard API, frontier subscription, frontier API |
| `contextSource` | pasted text, GitHub/MCP retrieval, Atlas digest, packet, diff |
| `artifactRefs` | packets, plans, handoffs, PRs, sessions, concepts |
| `estimatedInputTokens` | approximate or exact if available |
| `estimatedCachedInputTokens` | if known or estimated |
| `estimatedOutputTokens` | approximate or exact if available |
| `actualApiCost` | known for direct API work |
| `apiEquivalentEstimate` | estimated for subscription/local work |
| `confidence` | visible-only, likely, high, exact, unknown |
| `approvalStatus` | auto, human-approved, exceptional |
| `valueOutcome` | preserved concept, rationalized design, plan, handoff, PR, verification |

---

## 11. Has the Original Idea Been Retained?

Yes, but it had become distributed across several documents:

| Original idea | Where retained |
|---|---|
| Subscription vs API-equivalent estimation | `excavation.md`, `index.jsonld`, this note |
| Session/cycle-based accounting | `excavation.md`, this note |
| Artifact-cycle cost unit | `excavation.md`, this note |
| Human-as-message-bus cost | `excavation.md`, `engineer-orientation.md`, this note |
| Subscription cognition + API/local logistics | `excavation.md`, `engineer-orientation.md`, this note |
| Green/Yellow/Red/Black cost governance | `excavation.md`, `engineer-orientation.md`, this note |
| Local-first escalation | `excavation.md`, `engineer-orientation.md`, this note |
| API billing estimator artifact | `index.jsonld`, `excavation.md`; still unpreserved |
| Atlas as replacement for authority-doc cycling | `global-coherence-map-note.md`, `design-atlas-related-work-survey.md`, this note |
| Project-local/federated accounting scope | `federated-graphs-and-project-local-forge.md`, this note |

This note exists because those ideas are important enough to need a single preservation anchor.

---

## 12. Remaining Gaps

1. The interactive API billing estimator artifact is referenced but not preserved.
2. There is no formal cost ledger schema yet.
3. There is no token/cost estimation implementation yet.
4. There is no policy for when subscription-surface use should be preferred over API use.
5. There is no policy for how local compute costs or hardware amortization should be tracked.
6. There is no completed Cost Governor design.
7. The Green/Yellow/Red/Black classes need vocabulary representation before implementation.
8. API-equivalent estimates remain approximate unless direct usage logs are available.

---

## 13. Provisional Recommendation

Treat cost accounting and cost classification as first-class concerns in the design rationalization phase.

Do not reduce them to implementation details of future drones.

The original insight remains central:

> Forge should use subscriptions, API, and local models in concert, preserving high-value frontier reasoning while using lower-cost workers for context preparation, classification, validation, handoff, and dispatch.

---

## 14. Non-Implementation Constraint

This note preserves cost-accounting design intent. It does not implement cost logging, token estimation, billing dashboards, model routing, or a Cost Governor.
