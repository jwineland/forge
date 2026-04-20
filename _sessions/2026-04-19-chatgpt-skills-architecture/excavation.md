# Session Excavation: 2026-04-19 — ChatGPT — skills architecture and Forge operating model

**Session ID:** `2026-04-19-chatgpt-skills-architecture`
**Platform:** ChatGPT
**Date:** 2026-04-19
**Context:** Forge README framing, concept lifecycle refinement, skill loading architecture, GitHub MCP operational discipline, context and memory patterns
**Excavation type:** Manual bootstrap — automated excavation not yet available
**Note:** Exchange boundaries and citations are approximate in this manual record.

---

## Thread Index

| Thread ID | Description | Approximate span |
|---|---|---|
| `forge-positioning` | Clarifying what Forge is, what it does, and how the README should frame it | Session start through README drafting |
| `lifecycle-refinement` | Revising the lifecycle model so promotion is treated as a transition rather than a stage | Mid-session |
| `github-operation-discipline` | Clarifying GitHub MCP-first operating behavior for repository work | Mid-session through branch/PR work |
| `skill-architecture` | Defining shared skills, Forge-local skills, repo hooks, and loader patterns | Late session |
| `memory-context-patterns` | Distinguishing skills, context files, and memory files in the architecture | Late session |
| `session-forging` | Applying Forge to this conversation and depositing the excavation record | Final session |

---

## Concepts Extracted

| Concept ID | Status | Thread | Citation |
|---|---|---|---|
| forge-readme-positioning-and-status-clarification | classified | forge-positioning | `forge:2026-04-19-chatgpt-skills-architecture:forge-positioning:exchange-1` |
| concept-artifact-support-hierarchy | classified | forge-positioning | `forge:2026-04-19-chatgpt-skills-architecture:forge-positioning:exchange-4` |
| promotion-as-transition-not-stage | classified | lifecycle-refinement | `forge:2026-04-19-chatgpt-skills-architecture:lifecycle-refinement:exchange-2` |
| github-mcp-first-operational-discipline | classified | github-operation-discipline | `forge:2026-04-19-chatgpt-skills-architecture:github-operation-discipline:exchange-3` |
| layered-skill-loading-architecture | classified | skill-architecture | `forge:2026-04-19-chatgpt-skills-architecture:skill-architecture:exchange-2` |
| shared-stubs-and-repo-hooks-pattern | classified | skill-architecture | `forge:2026-04-19-chatgpt-skills-architecture:skill-architecture:exchange-5` |
| skills-context-memory-separation | classified | memory-context-patterns | `forge:2026-04-19-chatgpt-skills-architecture:memory-context-patterns:exchange-2` |
| chat-bound-skill-loading-model | classified | skill-architecture | `forge:2026-04-19-chatgpt-skills-architecture:skill-architecture:exchange-7` |

---

## Promoted Concepts

| Concept | Promoted Into | Notes |
|---|---|---|
| forge-readme-positioning-and-status-clarification | `README.md` via PR #5 | Conversation produced a concrete README rewrite and framing update for Forge |
| promotion-as-transition-not-stage | README conceptual model | Lifecycle framing updated in README draft to distinguish stage progression from working transitions |

---

## Supporting Artifacts

| Artifact | Relation | Notes |
|---|---|---|
| `README.md` rewrite on `docs/readme-reframe` | supports `forge-readme-positioning-and-status-clarification` | Concrete framing artifact created during the session |
| PR #5 `Clarify Forge README positioning and lifecycle model` | supports `forge-readme-positioning-and-status-clarification`, `promotion-as-transition-not-stage` | Operationalization of session conclusions into repo-facing documentation |
| This excavation record | supports all extracted concepts | Canonical session deposit for later refinement |

---

## Parked Concepts

| Concept | Status | Trigger |
|---|---|---|
| github-mcp-first-skill | not yet authored | When `jwineland/corpus-skills` exists and shared operational skills can be authored there |
| repo-context-loader-skill | not yet authored | When common loader conventions are ready to be defined across repos |
| memory-loader-skill | not yet authored | When a stable memory/context resolution order is ready to be codified |

---

## Open Threads

| Thread | Description | Blocks |
|---|---|---|
| Shared skills repository creation | Broad reusable skills are planned, but `jwineland/corpus-skills` does not yet exist | Canonical home for GitHub MCP-first and other cross-repo skills |
| Repo hook convention | A common convention for `AGENTS.md`, `MANIFEST.md`, `_skills/`, `_context/`, and `_memory/` was sketched but not formalized | Reusable loader behavior across repos |
| Forge stage model alignment | README framing now treats promotion as a transition, but `MANIFEST.md` still names promotion inside the canonical stage spine | Full lifecycle coherence across control documents |
| Memory/context file convention | Strong architectural direction emerged, but no canonical file contract was created | Shared loader design and repo onboarding |

---

## Excavation Notes

This session was unusually operational as well as conceptual. It did not only clarify Forge's framing; it also produced a concrete GitHub branch and PR for README revision, then turned to the architecture of skills, hooks, context, and memory outside Forge itself.

The conversation sharpened a distinction that appears important for Forge going forward:

- **concepts** are primary asserted units of meaning
- **artifacts** support one or more concepts and often carry them toward implementation or project formation
- **skills** are reusable operational methods
- **context files** define the world or repo being worked in
- **memory files** preserve prior decisions, preferences, and active threads across sessions

The user also established a strong operating preference that GitHub repository work should use the GitHub MCP server directly, with live tool re-enumeration before any claim that a capability is unavailable. That preference was discussed as a potential shared skill rather than a Forge-local skill.
