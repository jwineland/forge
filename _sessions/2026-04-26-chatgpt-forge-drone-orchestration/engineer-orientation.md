# Engineer Orientation: Forge Design State and Drone-Orchestration Direction

**Audience:** Human engineer joining Forge design work  
**Status:** Orientation and design-status document. Not an implementation directive.  
**Date:** 2026-04-26  
**Related session:** `2026-04-26-chatgpt-forge-drone-orchestration`  
**Branch:** `design/capture-drone-orchestration`  

---

## 1. Why This Document Exists

This document explains what Forge is, why the current design discussion matters, and where the project stands so another human engineer can participate without needing to reconstruct the project history from scattered conversations.

The immediate context is that Forge began as a system for **concept excavation, classification, preservation, and elevation** from AI-assisted design conversations. The current discussion extends that foundation toward **design rationalization, implementation planning, prompt generation, dispatch, and workflow orchestration** across subscription AI tools, direct APIs, local models, GitHub, and future custom infrastructure.

The project is still in design rationalization. We are not yet implementing the drone/worker orchestration layer described here.

---

## 2. One-Sentence Description

Forge is a semantic knowledge lifecycle system for extracting, preserving, challenging, elevating, weaving, and operationalizing concepts and designs that emerge from human/AI collaboration.

---

## 3. Current Forge Baseline

Forge already has mechanisms and conventions for:

1. **Excavation** — capturing valuable concepts and design threads from conversations.
2. **Classification** — labeling and organizing concepts with metadata, provenance, status, and relationships.
3. **Elevation / Formalization** — developing concepts through challenge loops, rationalization, metadata enrichment, and association with other concepts.
4. **Parking** — preserving concepts that are important but premature, with trigger conditions for future revival.
5. **Promotion / Reuse** — moving concepts into specific project corpora or reusing them across projects.
6. **Session provenance** — preserving citation addresses and session indices so concepts can be traced back to the conversation where they emerged.

The Forge repo itself is the default general concept registry, but the mechanisms are intended to apply to any project that is being elevated, not only Forge.

---

## 4. Existing Repository Orientation

The current Forge repo is organized around semantic lifecycle artifacts rather than application code.

Important areas:

| Location | Purpose |
|---|---|
| `MANIFEST.md` | Authoritative orientation and governance for the repo |
| `AGENTS.md` / `CLAUDE.md` | Tool/agent working instructions |
| `_vocabulary/` | JSON-LD vocabulary, node/edge/status definitions |
| `_concepts/` | Formalized and developing concept records |
| `_sessions/` | Excavated session records and machine-readable session indices |
| `_intake/` | Staging area for raw or pre-annotated session material |
| `_parked/` | Deferred concepts with trigger conditions |
| `_skills/` | Placeholder for future corpus-skills synchronization |

A new engineer should read `MANIFEST.md` before editing anything. Session records are append-only after initial commit.

---

## 5. Important Distinction: Forge Core vs. Projects Elevated by Forge

Forge is not only about the Forge repo. Forge should be able to operate over any project.

There are at least three kinds of target projects:

1. **Forge itself** — project design work introduced directly by the user.
2. **Named external project repos** — projects the user explicitly asks Forge to elevate.
3. **Emergent projects** — project candidates discovered from concept clusters, repeated design patterns, or parked concepts that mature into operational opportunities.

A concept can be reused across multiple projects. Promotion into one project should not destroy or erase the original concept lineage in Forge.

This means Forge needs to support both:

```text
concept lifecycle management
```

and:

```text
project/design lifecycle management
```

---

## 6. Design Elevation as a First-Class Modality

The current understanding is that Forge should not only elevate atomic concepts. It should also elevate **designs**.

Design elevation includes:

- design excavation
- design rationalization
- concept weaving
- clustering related concepts into candidate architectures
- challenge loops over design alternatives
- refinement of design metadata
- production of design packets, ADRs, implementation plans, and handoff prompts

A design may be understood as a composition of concepts, constraints, decisions, open questions, intended outcomes, and project-specific context.

Open question: whether designs should be represented as first-class Forge artifacts distinct from concepts, or as concept clusters with a design-level wrapper.

---

## 7. Implementation Planning as a First-Class Modality

Forge must also support implementation planning with the same general pattern used for concepts and designs:

```text
excavate → classify → challenge → rationalize → formalize → operationalize
```

Implementation planning is not the same as implementation. It includes:

- translating a rationalized design into an implementation plan
- identifying affected files/modules
- generating tasks, acceptance criteria, and test plans
- creating prompts or packets for Codex, Claude Code, Cline, or other implementation tools
- reviewing implementation results against frozen design intent
- reconciling implementation feedback back into Forge concepts/designs

This is important because the user often uses high-reasoning models for design and lower-cost or coding-specific agents for implementation. Forge should make that handoff explicit and durable.

---

## 8. Prompt Generation and Dispatch Are First-Class

A major problem the user identified is that they currently act as the human message bus between multiple AI surfaces and tools.

Examples:

```text
ChatGPT web / Android
→ GitHub
→ Codex
→ Claude Code
→ local files
→ PRs
→ back to ChatGPT
```

This causes friction, slows work, and introduces risk from copy/paste errors, stale context, missed values, and incomplete handoffs.

Therefore Forge must treat prompt generation and dispatch as first-class design concerns across all stages, not only implementation.

Prompt generation may apply to:

- concept excavation prompts
- challenge-loop prompts
- design review prompts
- rationalization prompts
- implementation planning prompts
- Codex / Claude Code execution prompts
- verification prompts
- reconciliation prompts

Dispatch may happen through many mechanisms:

- human copy/paste initially
- GitHub issues, PRs, branches, or committed handoff artifacts
- MCP servers
- direct API calls
- local agent frameworks
- custom front ends
- future Forge-controlled job runners

The key goal is to reduce or eliminate the user as manual transport while preserving user judgment and cost control.

---

## 9. Multi-Model Challenge Loops Remain Central

The user requires multiple frontier models to challenge and refine one another in high-value design work. This is not incidental; it is core to how design quality is achieved.

However, repeated high-reasoning review over large context is expensive under API billing. The current architectural principle is:

> Frontier models should adjudicate compressed arguments, not repeatedly re-read the universe.

This implies that Forge should prepare bounded design packets and route them to high-reasoning review only when appropriate.

---

## 10. Subscription, API, and Local Models Must Work Together

The system must account for multiple execution/cost surfaces:

| Surface | Strength | Risk |
|---|---|---|
| Subscription tools | Economically favorable frontier reasoning; interactive review | User becomes message bus; limited automation |
| Direct API | Automatable orchestration, dispatch, custom apps | Potentially high uncapped cost |
| Local models | Low marginal cost, privacy, high-volume housekeeping | Lower quality; requires validation/escalation |
| Alternative model hosts | Flexibility and cost options | Operational complexity and quality variance |

The emerging principle is:

```text
subscription cognition + API/local logistics
```

Use expensive/high-quality models for adjudication, critique, and hard synthesis. Use cheap/local/API workers for indexing, summarization, classification, packet creation, validation, dispatch support, and status maintenance.

---

## 11. Drone / Worker Concept

The current design discussion introduces **drones** or **workers** as bounded helpers that perform operational tasks around Forge artifacts.

They are not intended to replace human judgment or frontier-model design adjudication. Their role is to maintain the substrate, prepare context, route work, validate outputs, and reduce human message-bus burden.

Candidate drone classes:

### Local housekeeping drones

Run locally where possible, including on laptop CPU or future GB10-class hardware.

- index drone
- classifier drone
- summarizer drone
- deduplication drone
- drift detector
- packet builder
- metadata hygiene checker

### API utility drones

Use low-cost or standard API models for bounded tasks when local models are insufficient.

- plan normalizer
- handoff builder
- PR digest worker
- acceptance checker
- retrieval judge
- router

### Frontier design drones

Escalated, expensive, and bounded.

- critic
- architect
- risk reviewer
- decision synthesizer
- implementation-review judge

### Execution drones

Implementation or operational agents.

- Codex
- Claude Code
- Cline
- custom scripts
- test runner
- PR creator
- repair loop helper

Open vocabulary question: whether Forge should formally call these `drones`, `workers`, `agents`, `operators`, or something else.

---

## 12. Cost-Class Governance

The current proposal uses a four-level cost class model:

| Class | Meaning | Approval posture |
|---|---|---|
| Green | Local or very cheap housekeeping | Runs freely within policy |
| Yellow | Bounded low/medium API utility work | Runs with per-job/monthly caps |
| Red | Frontier reasoning or high-impact design work | Explicit approval or subscription-surface routing |
| Black | Multi-frontier debate or large-context frontier loops | Exceptional approval only |

This is meant to prevent accidental API blowouts while preserving the design value of multi-model frontier challenge loops.

---

## 13. GitHub as Shared State Layer

GitHub currently appears to be the most practical shared substrate for Forge-mediated work.

Potential roles:

- authority repository
- design artifact store
- session preservation surface
- branch/PR review surface
- prompt/handoff exchange layer
- audit trail
- partial message bus among AI surfaces

However, GitHub should not necessarily be the only state layer forever. Forge may later use databases, MCP servers, memory frameworks, custom front ends, or agent frameworks.

Open design question: whether GitHub should be modeled as the canonical state substrate, one dispatch surface among many, or an implementation detail beneath Forge abstractions.

---

## 14. Potential Future Infrastructure

The design does not assume Forge must remain a static repo. It may require new infrastructure, including:

- custom MCP servers
- memory frameworks
- local model runners
- vector/graph databases
- job queues
- agent frameworks
- front ends for review and dispatch
- cost governance services
- GitHub apps/actions
- local-first tooling

Nothing in this branch implements those yet. The point is to recognize that Forge may need such infrastructure to achieve its goals.

---

## 15. Current Implementation Status

As of this branch:

### Implemented / present

- Repo-level manifest and governance model
- Concept registry structure
- Session excavation format
- JSON-LD session indexing pattern
- Concept status vocabulary
- Parking mechanism
- Existing formalized concept files
- Manual session captures
- Draft PR preserving the drone-orchestration design discussion

### Designed / under review

- Drone/worker orchestration as an extension of Forge
- Local/API/subscription cost-tier strategy
- Prompt generation and dispatch as first-class concerns
- Bounded context packets
- Human-as-message-bus as a design pressure
- Design elevation and implementation planning as Forge modalities
- Cost-class governance model

### Not implemented

- Drone runtime
- Job schema
- Cost governor
- Automated dispatch
- MCP server(s)
- Local model integration
- `.forge/` project workspace template
- Design packet schema
- Implementation planning schema
- Front end
- Database / graph persistence beyond current files

---

## 16. How a Human Engineer Can Help Now

The most valuable near-term engineering contribution is not coding the drone runtime yet. It is helping clarify the architecture and implementation path.

Suggested review tasks:

1. Read `MANIFEST.md`.
2. Read `_sessions/README.md`.
3. Read this orientation document.
4. Read `excavation.md` in this same session directory.
5. Review whether the proposed drone layer belongs in Forge Core, a Forge Operations package, or project-specific tooling.
6. Identify the smallest useful schema set for:
   - design packet
   - drone job
   - prompt/handoff artifact
   - implementation plan
   - review/challenge output
7. Propose an MVP implementation sequence that preserves current Forge invariants.
8. Identify which work should remain file-based vs. move to database/graph storage.
9. Identify which parts should be local-first, API-backed, or subscription-mediated.
10. Challenge whether `drone` is the right abstraction/vocabulary.

---

## 17. Suggested First Architecture Questions

Before implementation, resolve these:

1. What is the boundary between Forge Core and Forge Operations?
2. Are designs first-class artifacts or concept-cluster projections?
3. Are implementation plans first-class artifacts?
4. What does a bounded context packet contain?
5. What metadata is required for a prompt/handoff artifact?
6. What is the minimal viable job schema?
7. How does a job declare model/cost policy?
8. How does Forge record results from subscription UI surfaces that cannot be automated directly?
9. How does Forge avoid becoming a generic agent framework?
10. What is the first workflow that proves value without overbuilding?

---

## 18. Candidate MVP Framing

A possible MVP is:

> Remove the user as the manual message bus for one design-to-implementation handoff workflow.

Candidate workflow:

```text
1. Select a design goal.
2. Gather relevant Forge/project context.
3. Build a bounded design packet.
4. Generate challenge prompts for frontier review.
5. Capture model review results.
6. Rationalize into a frozen design decision.
7. Generate an implementation plan.
8. Generate a Codex/Claude Code handoff prompt.
9. Preserve all artifacts in GitHub.
10. Verify implementation result against the frozen plan.
```

This MVP should likely use existing GitHub/file mechanics first, with explicit human approval gates, before adding autonomous dispatch.

---

## 19. Key Mental Model

Forge should preserve and elevate meaning, not merely automate tasks.

Drones/workers are useful only if they strengthen that lifecycle:

```text
excavate → classify → challenge → rationalize → weave → plan → dispatch → verify → reconcile
```

The human remains responsible for intent, judgment, and authorization. Frontier models provide high-value critique and synthesis. Drones maintain continuity, structure, and operational hygiene.
