# Session Excavation: 2026-04-26 — ChatGPT — Forge Drone Orchestration Design

**Session ID:** `2026-04-26-chatgpt-forge-drone-orchestration`  
**Platform:** ChatGPT  
**Date:** 2026-04-26  
**Context:** Forge design; subscription/API cost architecture; drone-worker orchestration; GitHub/MCP-mediated design and implementation workflow  
**Excavation type:** Manual design capture — automated excavation not yet available  
**Citation quality:** Approximate — exchange numbers are reconstructed from this session summary, not a full transcript import. Thread-level citations are reliable; exchange numbers should be treated as approximate until transcript-exact data is available. See the Forge citation spec for quality tier definitions.  
**Status:** Design input for review, challenge, rationalization, and possible incorporation. Not an implementation directive.  
**Note:** Exchange numbers are approximate because this is a manually captured session summary rather than a full transcript import.

---

## Purpose of This Capture

This session extends Forge's existing concept-preservation and classification model into a proposed design direction for **bounded worker / drone orchestration**. The immediate motivation is the user's existing workflow: high-reasoning design development across ChatGPT, Codex, Claude, Claude Code, GitHub, and possibly local compute, with the user currently acting as a human message bus between surfaces.

The session argues that Forge may need a new operational layer that preserves the economic advantage of subscription-based frontier reasoning while using lower-cost API or local workers for housekeeping, routing, context preparation, validation, and dispatch.

This capture is intended to be reviewed by other models and rationalized against existing Forge concepts before any implementation work begins.

---

## Thread Index

| Thread ID | Description | Approximate span |
|---|---|---|
| `subscription-api-equivalence` | Estimating what subscription usage would cost under API billing | Early session |
| `usage-shape-analysis` | Characterizing the user's real usage as design development, artifact cycling, tool calling, GitHub/MCP, and implementation handoff | Early-to-mid session |
| `cost-architecture` | Reframing the problem from metering to cost architecture and model tiering | Mid-session |
| `hybrid-subscription-api-model` | Subscription frontier cognition plus API/local automation for logistics | Mid-session |
| `forge-housekeeping-workers` | Extension of Forge from concept preservation/classification into low-cost worker support | Late session |
| `drone-orchestration` | Treating workers as drones with local/API/subscription capability tiers and escalation paths | Late session |
| `design-capture-meta` | Capturing this discussion into Forge as design input for Forge itself | Final session |

---

## Core Observations Captured

### 1. The user's workflow is not ordinary chat usage

The session identifies the user's pattern as a design-and-implementation operating loop:

```text
design authority docs
→ modular design fragments
→ GitHub-backed review/update cycles
→ branches / commits / PRs
→ implementation plans
→ Codex / Claude Code prompts
→ implementation feedback
→ design rationalization
```

This has high API-equivalent cost because it combines large context retrieval, high-reasoning model debate, repeated design refinement, and agentic implementation handoff.

### 2. The user is currently the message bus

Subscription surfaces provide economically favorable access to frontier models, but they force the user to transport context and work products among ChatGPT, Codex, Claude, Claude Code, GitHub, local files, and other tools. This produces manual friction, error risk, stale values, missed context, and failed handoffs.

### 3. Pure API migration is economically dangerous

The session concludes that replacing the whole workflow with API agents would improve orchestration but could expose the most expensive part of the workflow — frontier design reasoning over large context — to uncapped metered billing. The likely API-equivalent cost may be far above the user's acceptable monthly spend.

### 4. The proposed architecture is hybrid

The proposed model is:

```text
subscription cognition + API/local logistics
```

High-reasoning design adjudication remains on subscription or explicitly approved frontier calls. Lower-cost workers handle context packing, indexing, validation, summarization, dispatch, and artifact maintenance.

### 5. Forge is the natural continuity layer

Forge already exists to preserve concepts, classify them, retain lineage, and support rationalization. This discussion proposes that Forge can also coordinate operational drones that maintain the substrate around those preserved concepts.

---

## Candidate Concepts Extracted

| Concept ID | Proposed status | Thread | Citation |
|---|---|---|---|
| subscription-api-equivalent-usage-estimation | excavated | subscription-api-equivalence | `forge:2026-04-26-chatgpt-forge-drone-orchestration:subscription-api-equivalence:exchange-1` |
| session-based-cost-modeling | excavated | usage-shape-analysis | `forge:2026-04-26-chatgpt-forge-drone-orchestration:usage-shape-analysis:exchange-2` |
| artifact-cycle-as-cost-unit | excavated | usage-shape-analysis | `forge:2026-04-26-chatgpt-forge-drone-orchestration:usage-shape-analysis:exchange-3` |
| human-as-message-bus | excavated | hybrid-subscription-api-model | `forge:2026-04-26-chatgpt-forge-drone-orchestration:hybrid-subscription-api-model:exchange-4` |
| subscription-cognition-api-logistics | excavated | hybrid-subscription-api-model | `forge:2026-04-26-chatgpt-forge-drone-orchestration:hybrid-subscription-api-model:exchange-5` |
| frontier-design-court | excavated | cost-architecture | `forge:2026-04-26-chatgpt-forge-drone-orchestration:cost-architecture:exchange-6` |
| bounded-context-packet | excavated | cost-architecture | `forge:2026-04-26-chatgpt-forge-drone-orchestration:cost-architecture:exchange-7` |
| forge-housekeeping-workers | excavated | forge-housekeeping-workers | `forge:2026-04-26-chatgpt-forge-drone-orchestration:forge-housekeeping-workers:exchange-8` |
| drone-cost-class-governance | excavated | drone-orchestration | `forge:2026-04-26-chatgpt-forge-drone-orchestration:drone-orchestration:exchange-9` |
| local-first-drone-escalation | excavated | drone-orchestration | `forge:2026-04-26-chatgpt-forge-drone-orchestration:drone-orchestration:exchange-10` |
| github-as-shared-state-substrate | excavated | drone-orchestration | `forge:2026-04-26-chatgpt-forge-drone-orchestration:drone-orchestration:exchange-11` |
| design-packet-freeze | excavated | drone-orchestration | `forge:2026-04-26-chatgpt-forge-drone-orchestration:drone-orchestration:exchange-12` |
| forge-drone-coordination-layer | excavated | design-capture-meta | `forge:2026-04-26-chatgpt-forge-drone-orchestration:design-capture-meta:exchange-13` |

### Rationalization Notes

**Concept boundary overlap requiring pre-promotion rationalization:**

`forge-housekeeping-workers` (exchange-8) and `forge-drone-coordination-layer` (exchange-13) have substantially overlapping scope. The first covers the extension of Forge into low-cost worker support; the second covers the coordination mechanism for those workers. The boundary between execution workers and coordination layer is not yet clearly defined. Before either concept is promoted to qualification, a rationalization task should resolve whether these are:

1. Two distinct concepts (execution vs. coordination concerns),
2. A single `forge-operational-layer` concept with coordination as a sub-concern, or
3. A primary concept and a derivative.

This ambiguity should not block excavation-stage capture, but must be resolved before formalization.

**Causal linkage note:**

`human-as-message-bus` is the named design pressure that motivates `subscription-cognition-api-logistics`. These are cause and architectural response. During rationalization, the concept records should encode an explicit `motivatedBy` or `addressesPressure` relationship so they are not treated as independent concepts.

---

## Candidate Design Direction

### Proposed extension to Forge

Forge may extend from:

```text
concept preservation / classification / lineage
```

to:

```text
concept preservation + workflow orchestration + low-cost housekeeping drones
```

This does not mean Forge becomes a general autonomous agent. Instead, Forge would coordinate bounded workers that maintain context, prepare artifacts, route work, and preserve durable state while reserving high-level design judgment for humans and frontier models.

---

## Drone Classes Proposed

### Class A — Local housekeeping drones

Run on laptop CPU, local workstation, or GB10-class local hardware where possible.

| Drone | Role |
|---|---|
| Index drone | Maintains file, concept, ADR, and module indexes |
| Classifier drone | Labels docs, commits, issues, design concepts |
| Summarizer drone | Produces cheap summaries of files, diffs, threads |
| Deduplication drone | Finds repeated, stale, or conflicting concepts |
| Drift drone | Detects mismatch between design intent and implementation |
| Packet drone | Builds bounded context packets for expensive models |
| Hygiene drone | Checks formatting, metadata, references, missing fields |

### Class B — API utility drones

Use lower-cost API models where local models are inadequate but frontier reasoning is not required.

| Drone | Role |
|---|---|
| Plan normalizer | Turns rough design notes into structured plans |
| Handoff builder | Creates Codex / Claude Code implementation prompts |
| PR digest drone | Summarizes branch changes and review state |
| Acceptance checker | Verifies plan includes scope, constraints, tests |
| Retrieval judge | Selects files or excerpts for a design packet |
| Router drone | Chooses next workflow step or target surface |

### Class C — Frontier design drones

Expensive, bounded, and explicitly escalated. These may be subscription-surface mediated or approved API calls.

| Drone | Role |
|---|---|
| Critic drone | Challenges a design packet |
| Architect drone | Synthesizes competing positions |
| Risk drone | Looks for hidden architectural failure modes |
| Decision drone | Produces an ADR or final design position |
| Review drone | Reviews implementation against frozen intent |

### Class D — Execution drones

Codex, Claude Code, Cline, local scripts, or other execution workers.

| Drone | Role |
|---|---|
| Implementation drone | Applies code changes |
| Test drone | Runs tests, lint, build, and checks |
| Patch drone | Creates mechanical file updates |
| Migration drone | Applies broad but low-risk changes |
| PR drone | Opens branch, commit, and PR |
| Repair drone | Interprets failures and prepares the next attempt |

---

## Cost-Class Governance Proposal

Every drone job should declare a cost class and escalation policy.

| Class | Meaning | Approval posture |
|---|---|---|
| Green | Local or very cheap housekeeping | Runs freely within policy |
| Yellow | Bounded low/medium API utility work | Runs with per-job and monthly caps |
| Red | Frontier reasoning or high-impact design work | Requires explicit approval or subscription-surface routing |
| Black | Multi-frontier debate or large-context frontier loops | Exceptional approval only |

Proposed rule:

> Frontier models should adjudicate compressed arguments, not repeatedly re-read the universe.

---

## Proposed Core Drone Loop

```text
1. Intake
   User creates or selects a design goal.

2. Gather
   Local/API drones inspect repo, docs, issues, prior decisions.

3. Packetize
   Packet drone creates a bounded design packet.

4. Classify
   Classifier tags concepts, risks, affected modules, dependencies.

5. Frontier review
   ChatGPT/Claude critiques the packet.

6. Adjudicate
   Decision drone or human produces frozen design decision.

7. Plan
   Plan drone creates implementation plan.

8. Handoff
   Handoff drone creates Codex / Claude Code prompt.

9. Dispatch
   Execution drone applies change on branch.

10. Verify
   Test/drift drones compare implementation to frozen intent.

11. Reconcile
   Forge updates concepts, indexes, ADRs, packets, PR notes.
```

Key design requirement:

> The output of each phase is a durable artifact, not an ephemeral chat message.

---

## Proposed Shared State Layout

The session proposed a possible future `.forge/` operational workspace in project repositories, not necessarily in the Forge concept registry itself:

```text
.forge/
  concepts/
  packets/
  plans/
  handoffs/
  jobs/
  decisions/
  reports/
  indexes/
```

Example artifacts:

```text
.forge/jobs/2026-04-26-auth-refactor.yml
.forge/packets/auth-refactor-design-packet.md
.forge/plans/auth-refactor-implementation-plan.md
.forge/handoffs/codex-auth-refactor-prompt.md
.forge/decisions/ADR-0042-auth-boundary.md
```

Open question: whether this layout belongs in Forge Core, a Forge workflow template, consumer project repos, or a separate operational package.

---

## Minimum Viable Drone System Proposed

The proposed first MVP would not implement a full swarm. It would start with five drones:

1. Index drone
2. Packet drone
3. Handoff drone
4. Verification drone
5. Cost governor drone

The MVP goal:

```text
Remove the user as the message bus for design-to-implementation handoff.
```

The MVP workflow:

```text
repo/design goal
→ bounded packet
→ frontier review
→ frozen plan
→ Codex/Claude Code handoff
→ verification
→ GitHub reconciliation
```

---

## Local Compute Considerations

The user may soon have GB10-class local resources and can also run lighter models on CPU on a laptop. The design should support local-first drones for high-volume, low-risk work, with escalation ladders:

```text
local model
→ cheap API model
→ standard API model
→ subscription frontier review
→ approved frontier API call
```

Candidate local-first tasks:

```text
file indexing
chunking
embedding
keyword extraction
concept classification
summary refresh
diff summarization
metadata validation
stale-reference detection
packet assembly
test result parsing
```

---

## Relationship to Existing Forge Concepts

This design appears related to, but not identical with, existing Forge concepts:

| Existing concept | Likely relationship |
|---|---|
| `forge-concept-lifecycle` | Drone outputs may become lifecycle transition artifacts |
| `human-ai-role-separation` | Drones refine the boundary between human judgment, frontier reasoning, and utility work |
| `challenge-loop-methodology` | Frontier design court is a structured model challenge loop over compressed packets |
| `multi-model-deliberation-roles` | Drone classes may operationalize differentiated model roles |
| `forge-guidance-engine` | Drones may become execution machinery for guidance outputs |
| `stage-aware-guided-advancement` | Drone escalation could be stage-aware |
| `evaluation-trust-plane` | Cost governor, verification, and drift drones may contribute to trust/evaluation layer |
| `actionable-intent-verses` | Drone handoffs and dispatch artifacts may be actionable intent verses |
| `human-as-message-bus` | *Motivates* → `subscription-cognition-api-logistics`; the design pressure this entire layer is a response to |

Review task: determine whether the new concepts should become formalized concepts, parked design threads, amendments to existing concepts, or a new Forge subsystem design.

---

## Open Design Questions

1. Is `drone` the right term, or should Forge use `worker`, `agent`, `operator`, `tasklet`, or another vocabulary term?
2. Does the drone layer belong in Forge Core, a Forge Operations layer, a separate project template, or downstream consumer repos?
3. What is the minimal schema for a drone job?
4. How should Forge represent local vs API vs subscription-surface model execution?
5. How should cost-class governance interact with concept lifecycle states?
6. Should bounded context packets be first-class Forge artifacts?
7. Is `human-as-message-bus` a problem concept, an anti-pattern, or a named design pressure?
8. How should GitHub be represented: shared state substrate, authority repository, or dispatch surface? (Note: GitHub is a substrate that *replaces* the human message bus, not a message bus itself. See concept `github-as-shared-state-substrate`.)
9. How should Forge capture model-to-model review outputs when some review occurs in subscription UI surfaces outside the API?
10. What is the boundary between Forge preserving design artifacts and Forge actively orchestrating implementation work?
11. Should drone outputs be immutable once committed, like session records, or mutable working artifacts?
12. What proof would show that drones reduce human message-bus burden without causing uncontrolled API spend?

---

## Review Prompts for Other Models

Use these prompts to challenge and rationalize this design before implementation.

### Review Prompt A — Architectural Fit

> Review the proposed Forge drone orchestration layer. Does it fit Forge's stated identity as a semantic knowledge lifecycle system, or does it overextend Forge into general agent orchestration? Identify which parts belong in Forge Core, which parts belong in a downstream operational package, and which parts should remain parked.

### Review Prompt B — Concept Rationalization

> Compare the candidate concepts from this session against existing Forge concepts such as `human-ai-role-separation`, `challenge-loop-methodology`, `multi-model-deliberation-roles`, `forge-guidance-engine`, and `evaluation-trust-plane`. Which concepts are genuinely new, which are refinements, and which are duplicate framings? In particular, resolve the boundary between `forge-housekeeping-workers` and `forge-drone-coordination-layer`.

### Review Prompt C — Economic Model

> Evaluate the proposed cost-class governance model: Green, Yellow, Red, Black. Is this sufficient to prevent accidental API cost blowouts while preserving high-quality frontier design review? What budget, logging, and approval primitives are missing?

### Review Prompt D — Local-First Drones

> Assess the proposal to use local models and local compute for housekeeping drones. Which drone tasks are safe for local models? Which require API or frontier escalation? What confidence and validation mechanisms are required?

### Review Prompt E — MVP Scope

> Evaluate the proposed five-drone MVP: Index, Packet, Handoff, Verification, and Cost Governor. Is this the right minimal set to remove the user as human message bus for design-to-implementation handoff? What should be added, removed, or deferred?

---

## Parked / Deferred Items

| Item | Trigger |
|---|---|
| Full drone schema | When Forge decides whether drone jobs are first-class artifacts |
| `.forge/` operational workspace layout | When a consumer repo or Forge operations package is selected |
| Automated dispatch implementation | After design review and rationalization complete |
| Cost governor implementation | After job schema and model tier vocabulary are defined |
| Local model selection | When GB10/local hardware environment is available and target tasks are benchmarked |
| API billing estimator (full implementation) | When subscription/API hybrid operation begins and real logs are available. Note: a prototype interactive estimator was produced as a Claude.ai artifact on 2026-04-26 as an output of `subscription-api-equivalent-usage-estimation`. That artifact should be preserved and linked when an `OutputArtifact` record is established for this concept. |

---

## No-Implementation Constraint

This capture explicitly does **not** authorize implementation of drones, job runners, dispatch automation, or `.forge/` workspace creation. It preserves the design input so it can be challenged by other models, rationalized against existing Forge concepts, and incorporated through Forge's normal concept lifecycle.
