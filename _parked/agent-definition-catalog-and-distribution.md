---
id: agent-definition-catalog-and-distribution
name: Agent definition catalog, RAG, and distribution
status: parked
citation: forge:2026-07-22-claude-ekion-benchcheck-and-agent-workflow:rfc-scope-clarification:exchange-14
created: 2026-07-22
park-trigger: "Any one of: (a) enough of the owner's own agent definitions accumulate across multiple project repos that a search/fetch mechanism over them earns its complexity, independent of any external catalog; (b) a genuine, current need arises to pull agent definitions from an external catalog (e.g. VoltAgent's awesome-claude-code-subagents) rather than hand-author them; (c) a second or third project repo actually adopts the layered-agent-directive-governance pattern and copy-paste friction between repos becomes a real, observed cost rather than a hypothetical one; (d) a concrete cross-tool (not Claude-Code-specific) use case for agent coordination emerges that justifies real design work on an independent agent MCP service."
park-reason: "Raised during ekion-benchcheck (jwineland/syscheck-uk) bootstrap work as three related but not-yet-justified ideas: an agent-definition catalog/RAG, plugin-based distribution of an agent set across repos, and an independent agent MCP service usable across tools beyond Claude Code. None has a current triggering need in any active project. VoltAgent's awesome-claude-code-subagents catalog was reviewed directly (not by reputation) as a concrete reference point for two of the three -- its subagent-catalog skill (search/fetch/list over 154 agents) and its Claude Code plugin marketplace distribution mechanism are real, working precedent, not speculation. The third (independent MCP service) has no concrete precedent examined yet and would need real design work (auth, versioning, cross-tool semantics) whenever it's actually justified."
decay-policy: "manual-only"
depends-on: []
related-to:
  - ai-arb-realization-system
  - capability-engineering-framework
  - multi-model-deliberation-roles
---

## What this is

Three related, not-yet-justified ideas surfaced while bootstrapping an agent
workflow for a specific project (`ekion-benchcheck`, in `jwineland/syscheck-uk`):

1. **An agent-definition catalog/RAG** — a way to search, fetch, and reuse
   agent role definitions across projects (this owner's own accumulated
   definitions) or from external sources. Real precedent exists: VoltAgent's
   `awesome-claude-code-subagents` repo ships a `subagent-catalog` Claude Code
   skill with `/subagent-catalog:search|fetch|list` commands over its
   154-agent, 10-category collection.

2. **Plugin-based distribution of an agent set across repos** — rather than
   the copy-paste replication checklist currently used (see
   `jwineland/syscheck-uk`'s `docs/architecture/agents/README.md`). Real
   precedent exists: Claude Code plugin marketplaces
   (`claude plugin marketplace add`/`install`), which VoltAgent uses to
   distribute its catalog by category.

3. **An independent agent MCP service** — agent definitions and/or
   coordination exposed as an MCP server, usable across AI tools beyond
   Claude Code specifically (relevant given this owner's actual multi-platform
   workflow: Claude, ChatGPT, Gemini, DeepSeek). No concrete precedent
   examined yet; this is the least-developed of the three ideas.

Also potentially relevant, raised in the same conversation but not yet
investigated at all: third-party agent-definition scraping (e.g. from
community discussion sites) as a possible input to (1). This is noted here
so it isn't lost, not because any investigation has happened.

## Why this is parked, not acted on

None of the three has a current triggering need. Building any of them now
would be speculative infrastructure against a hypothetical future need,
which is exactly the kind of premature complexity this owner's projects
(see `ai-arb-realization-system`'s anti-overengineering charter, and
`ekion-benchcheck`'s own repeated "don't build until justified" discipline
— e.g. deferring typed `developer` agent variants until real frontend/db
code exists) are designed to avoid.

## Relationship to existing Forge material

This is **not** the same concern as the drone/worker orchestration design
captured in `_sessions/2026-04-26-chatgpt-forge-drone-orchestration/`,
though it's closely related and cross-references it:

- The drone-orchestration session is about **dispatching work** to
  agents/tools (execution) — its Section 14 ("Potential Future
  Infrastructure") already lists "custom MCP servers" as recognized,
  unimplemented future infrastructure, and its Section 17 asks, as an
  open architecture question, "What is the boundary between Forge Core
  and Forge Operations?"
- This parked concept is about **sourcing and organizing agent
  definitions themselves** (content — what an agent *is*, not what it
  *does*).

These should stay as separate, cross-referencing parked/open items rather
than being merged into one, but it's worth noting that this is the
**second independent surfacing** of the Forge-Core-vs-Operations boundary
question — once from the drone/dispatch angle, once from the
agent-definition-sourcing angle, from two different originating projects.
Per the same reasoning that validated Forge's design when the Claude and
Gemini sessions independently converged on the same concepts (PR #1), two
unrelated projects independently hitting the same unresolved boundary is
evidence the question is real and load-bearing — worth weighing when
`agent-coach` (or a human) next reviews `MANIFEST.md`'s Known Gaps.

## What activation should look like

When a trigger condition fires: move this file to `_concepts/`, resolve
whether the three ideas remain one concept or split into three (they may
mature at different rates — the catalog/RAG and plugin-distribution ideas
already have real precedent to design against; the MCP-service idea does
not and may need a preliminary investigation phase first), and record the
activation in `MANIFEST.md` per the standard protocol.
