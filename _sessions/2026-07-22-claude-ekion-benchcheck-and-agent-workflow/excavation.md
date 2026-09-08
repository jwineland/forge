# Session Excavation: 2026-07-22 — Claude — ekion-benchcheck Bootstrap and Agent Workflow Design

**Session ID:** `2026-07-22-claude-ekion-benchcheck-and-agent-workflow`
**Platform:** Claude (Sonnet 5, `claude.ai` mobile app)
**Date:** 2026-07-22 (session continued past UTC midnight into 2026-07-23 for some commits; dated to session start per project convention)
**Context:** Bootstrapping `ekion-benchcheck` (Python reimplementation of legacy `syscheck`/`netscript` factory-floor tooling) in `jwineland/syscheck-uk`; establishing its ADR/authority-doc process; building a cross-tool AI agent workflow (`AGENTS.md`/`CLAUDE.md`/`.claude/agents/`) with a self-tuning `agent-coach`; reviewing an external agent catalog (VoltAgent); and clarifying the boundary between project-scoped ADRs and meta-framework RFCs, which led directly to discovering and using Forge's own `_parked/` mechanism.
**Excavation type:** Live session excavation — written from the actual conversation transcript by the assistant that participated in it, not reconstructed after the fact from an export or summary.
**Citation quality:** Higher-confidence than a reconstructed-export excavation (e.g. the ChatGPT drone-orchestration session): exchange numbers reflect the real turn sequence of this conversation as experienced by the excavating assistant. Still hand-assigned rather than tool-extracted, so treat exchange numbers as reliable-approximate rather than transcript-indexed-exact.
**Status:** Design input for review, challenge, and rationalization. One item (see Parked Concepts) has already been formally parked with a trigger condition; the rest are excavated candidates only.

---

## Purpose of This Capture

This session was substantive `ekion-benchcheck` engineering work in a different repository (`jwineland/syscheck-uk`), not primarily a Forge design session. It is being excavated into Forge because several things that emerged are genuinely domain-agnostic — reusable across any project the owner works on — and because one specific question (where does a meta-framework-scoped idea belong when it surfaces mid-project?) turned out to already have an answer in Forge's existing `_parked/` mechanism. That discovery is itself worth recording as a convergence finding, the same way the independent Claude/Gemini convergence in PR #1 validated Forge's early design.

This capture does not excavate `ekion-benchcheck`'s own implementation details (the `CapabilityAdapter` pattern, collector adapters, etc.) — those are that project's concern and are recorded in its own ADR log. What's excavated here is the generalizable process/workflow knowledge that surfaced while doing that work.

---

## Thread Index

| Thread ID | Description | Approximate span |
|---|---|---|
| `ekion-benchcheck-bootstrap` | Repo scaffolding, ADR/authority-doc process, CapabilityAdapter framework, CI tooling, and two real incidents (a stale-branch merge conflict, a batch-push verification failure) | Early-to-mid session |
| `agent-workflow-and-coach` | Building `AGENTS.md`/`CLAUDE.md`/`.claude/agents/` with a fixed template and a five-role taxonomy, and `agent-coach`'s dual auditor/tuner mandate under a hard governance constraint | Mid session |
| `model-effort-tiering` | Pinning `model`/`effort` per agent role, verified against official Claude Code docs rather than assumed | Mid session |
| `voltagent-catalog-review` | Reviewing VoltAgent's 154-agent catalog as a reference point; deciding against adopting its length/style | Mid-to-late session |
| `rfc-scope-clarification` | Recognizing that cross-project meta-framework ideas don't belong in a project-scoped ADR log; discovering Forge's `_parked/` mechanism as the actual answer | Late session |

---

## Core Observations Captured

### 1. Two real incidents produced generalizable process lessons, not just local fixes

While bootstrapping `ekion-benchcheck`, two mistakes occurred that were fixed locally (in that repo's `CONTRIBUTING.md`/`AGENTS.md`) but are clearly not specific to that project:

- A feature branch was cut before a prior PR had merged, producing a real merge conflict that a content-only fix couldn't resolve because the branch's git history never derived from the merge commit. The fix was procedural (always branch from freshly-pulled `main`; don't run two overlapping-file PRs concurrently without rebasing), not a one-off code fix.
- A large multi-file batch push (via a GitHub API tool rather than `git push`) silently diverged from locally-tested content — one file's already-applied fix was omitted, another file's stale pre-reformat version was pasted in by mistake — and CI caught both, twice, after everything had looked clean locally. The generalizable lesson: for any multi-file batch operation, especially one that bypasses the normal `git diff`-before-commit gut-check, do a final fresh re-fetch-and-verify pass before considering it done.

Both lessons are currently recorded only in `ekion-benchcheck`'s own `CONTRIBUTING.md`. They're candidate Forge concepts because they'd apply to any project using an AI-assisted, API-mediated (rather than local-`git`-mediated) commit workflow — which is close to how this owner works across most of their repos.

### 2. A layered, governed agent-directive architecture was built and is itself a reusable pattern

The core structure: a terse, cross-tool `AGENTS.md` (safe default for any AI tool reading cold, no other context) at the top; a thin `CLAUDE.md` pointer beneath it (no duplicated content); a fixed five-section template for Claude Code subagent files; a minimal starting taxonomy (architect, developer, code-reviewer, security-reviewer, agent-coach) explicitly kept small until real need justifies growth; and `agent-coach` as a dual-mandate role (structural auditor + behavioral tuner) governed by one non-negotiable constraint: agent/skill definition files are *operationally active* (they shape future agent behavior), so they get the same branch-and-PR review gate as code, regardless of file extension, with no exception — not even the narrow live-session exception that otherwise lets this project's owner have documentation committed directly during a supervised pairing session. Coach may draft and propose autonomously; it may never merge its own proposal, and may never propose weakening the review gate itself.

This is a fully reusable pattern independent of `ekion-benchcheck`'s specific taxonomy — the layering, the template discipline, and specifically the "operationally-active-content gets code-like governance regardless of file type" principle all generalize.

### 3. Model/effort tiering per agent role was verified against real product documentation, not assumed

Rather than guess at Claude Code's subagent frontmatter capabilities, the actual current documentation was fetched and read before making tiering decisions. This confirmed `model` and `effort` are both independently pinnable per subagent (defaulting to `inherit`), while extended-thinking on/off is *not* independently controllable per subagent — it always inherits from the session. The resulting tiering (high-stakes/infrequent roles → stronger model/higher effort; high-frequency/well-scoped roles → a considered mid-tier default, deliberately not cut to the cheapest tier) is a direct, finer-grained instantiation of the role-specialized model routing already formalized in `multi-model-deliberation-roles` — worth cross-referencing there rather than treating as an unrelated new concept.

### 4. A real external agent catalog was reviewed and explicitly not imitated, with the reasoning recorded

VoltAgent's `awesome-claude-code-subagents` (154 agents, 10 categories) was fetched and inspected directly — not assessed by reputation. One representative agent file (287 lines, ~3x this project's agent file length) was pulled to ground the comparison. The finding: that catalog's length comes from being repo-agnostic (generic industry checklists substitute for codebase-specific grounding it structurally can't have) and from genuine 154-agent inter-agent handoff choreography (a structured JSON "Communication Protocol"). Neither reason applies to a small, single-codebase agent set grounded in real ADRs and named incidents. The decision was to keep the current short, specific style rather than pad it toward generic bulk — with the reasoning itself recorded (not just the decision), which is what makes it useful for a future project weighing the same tradeoff.

Three things from that catalog were flagged as real, working precedent for genuinely different future needs — deferred, not rejected — see the Parked Concept below.

### 5. The RFC-scope question directly validated Forge's own architecture

The most significant finding of this session, from Forge's own point of view: a project-scoped ADR (in `ekion-benchcheck`) had been used to record an idea — a future agent-definition catalog/RAG, a possible independent agent-MCP-service, third-party agent-definition scraping — that was actually out of that project's scope entirely. The person recognized this themselves and asked whether "RFC" was the right classification. Investigation (conversation search, then direct inspection of this repo) found that:

- The scope question was already answered in principle in an earlier Forge session: `corpus-template-eng` was slated to carry an ADR/RFC/ARB stack, distinct from Forge Core.
- Forge's `_parked/` mechanism — real, live, with a defined front-matter schema and decay-policy vocabulary — is a better-fitting answer than either an ADR or a formal RFC for an idea that is real, not the current project's to decide, and must not be lost. It was used exactly as designed.
- The specific idea (agent-definition catalog/RAG, MCP-service, distribution) turned out to be a close cousin of an already-recorded, still-open Forge question: the drone-orchestration session's Section 14 ("Potential Future Infrastructure" — custom MCP servers, explicitly unimplemented) and Section 17, Question 1 ("What is the boundary between Forge Core and Forge Operations?"). This is the **second independent surfacing of the same open architectural question**, from a different originating project and a different angle (agent-definition sourcing/cataloging rather than work dispatch/drones). Per the same reasoning that validated Forge's design when the Claude and Gemini sessions independently converged on the same concepts in PR #1, an unrelated project independently bumping into the same unresolved boundary question is evidence the question is real and load-bearing, not an artifact of one session's framing.

---

## Candidate Concepts Extracted

| Concept ID | Proposed status | Thread | Citation |
|---|---|---|---|
| batch-operation-verification-discipline | excavated | ekion-benchcheck-bootstrap | `forge:2026-07-22-claude-ekion-benchcheck-and-agent-workflow:ekion-benchcheck-bootstrap:exchange-6` |
| stale-branch-conflict-prevention | excavated | ekion-benchcheck-bootstrap | `forge:2026-07-22-claude-ekion-benchcheck-and-agent-workflow:ekion-benchcheck-bootstrap:exchange-5` |
| layered-agent-directive-governance | excavated | agent-workflow-and-coach | `forge:2026-07-22-claude-ekion-benchcheck-and-agent-workflow:agent-workflow-and-coach:exchange-9` |
| repo-grounded-agent-specificity-principle | excavated | voltagent-catalog-review | `forge:2026-07-22-claude-ekion-benchcheck-and-agent-workflow:voltagent-catalog-review:exchange-11` |
| forge-core-vs-operations-boundary-recurrence | excavated | rfc-scope-clarification | `forge:2026-07-22-claude-ekion-benchcheck-and-agent-workflow:rfc-scope-clarification:exchange-13` |

### Rationalization Notes

**`layered-agent-directive-governance` and `model-effort-tiering` (the thread, not yet a separate concept) overlap with `multi-model-deliberation-roles`:** the per-subagent model/effort tiering captured in this session is best understood as a concrete, finer-grained instantiation of the existing formalized concept, not a sibling concept. During rationalization, prefer extending `multi-model-deliberation-roles` (or adding a worked example to it) over formalizing a new standalone concept for tiering alone.

**`forge-core-vs-operations-boundary-recurrence` should be rationalized alongside the drone-orchestration session's open questions, not independently.** It is evidence bearing on an existing open question (drone session, Section 17, Q1), not a new question in its own right. Treat it as a second citation supporting that question's priority, and consider whether the "Forge North Star" / "Forge stage model document" Critical gaps already tracked in `MANIFEST.md` should explicitly address Forge Core vs. Forge Operations, since two independent projects have now hit this boundary.

**`batch-operation-verification-discipline` and `stale-branch-conflict-prevention` are candidates for `ai-arb-realization-system` or a new shared "engineering practice" concept**, not yet clear which. Both are concrete, named failure modes with concrete fixes; they read more like a growing checklist of "things that go wrong in AI-mediated, API-tool-driven git workflows specifically" than either belongs alone. Worth holding until there's a third instance to see if a pattern-level concept (e.g. `ai-mediated-git-workflow-failure-modes`) is warranted, per the same "don't formalize on one instance" discipline `ekion-benchcheck`'s own agent-coach uses.

---

## Parked Concept

**`agent-definition-catalog-and-distribution`** — parked, not merely excavated, with a full trigger condition. See `_parked/agent-definition-catalog-and-distribution.md` for the formal record. Summary: covers a future agent-definition catalog/RAG (real precedent: VoltAgent's `subagent-catalog` skill), plugin-based distribution of an agent set across repos (real precedent: Claude Code plugin marketplaces), and an independent, cross-tool agent MCP service — none justified by current need in any project, all explicitly cross-referenced to the drone-orchestration session's Section 14 and to `ai-arb-realization-system`/`capability-engineering-framework`.

---

## Relationship to Existing Forge Concepts

| Existing concept | Relationship |
|---|---|
| `ai-arb-realization-system` | The originating person's own name for this — "our AI-ARB development approach" — points here. This session's process lessons (batch-operation verification, stale-branch prevention) and the layered agent-governance pattern are candidate inputs to this concept's ongoing development, pending rationalization. |
| `capability-engineering-framework` | Cross-referenced by the parked concept; not directly extended by this session's other findings. |
| `multi-model-deliberation-roles` | The model/effort tiering work in this session is a concrete instantiation of this concept at Claude Code subagent granularity — see Rationalization Notes. |
| `human-ai-role-separation` | `agent-coach`'s constraint (drafts, never merges; agent-directive content gets code-like review regardless of file type) is a specific, concrete case of this concept's general boundary — worth citing as a worked example during that concept's next revision. |
| `challenge-loop-methodology` | The VoltAgent review (external reference, actual artifact pulled and inspected, decision recorded with reasoning rather than assumed) is a small-scale instance of this methodology applied to a design-tooling decision rather than a concept/design decision. |

---

## Open Design Questions Carried Forward

1. Should `batch-operation-verification-discipline` and `stale-branch-conflict-prevention` be formalized now, held for a third instance, or folded directly into `ai-arb-realization-system` as named failure modes? (See Rationalization Notes.)
2. Does the recurrence of the Forge-Core-vs-Operations boundary question (now seen from two independent projects) raise the priority of the already-Critical "Forge North Star" / "Forge stage model document" gaps in `MANIFEST.md`, or is it evidence a dedicated boundary-definition document is its own Critical gap?
3. Should `layered-agent-directive-governance` (the AGENTS.md/CLAUDE.md/.claude/agents/coach pattern) be formalized as a standalone concept, or is it better captured as a worked example/case study attached to `human-ai-role-separation` and `multi-model-deliberation-roles`?
4. This session originated in a different project's repo (`jwineland/syscheck-uk`) rather than as Forge design work proper — does that change how it should be weighted during rationalization compared to a session that was Forge design work from the start?

---

## No-Formalization Constraint

This capture excavates candidates only, except for the one concept explicitly parked with a trigger (`agent-definition-catalog-and-distribution`). It does not formalize any of the five excavated candidates above, and does not authorize treating any of them as settled Forge concepts until rationalized against the existing registry.
