---
id: skills-context-memory-separation
name: Skills, Context, and Memory Separation
status: classified
citation: forge:2026-04-19-chatgpt-skills-architecture:memory-context-patterns:exchange-2
created: 2026-04-20
depends-on: [three-layer-skill-architecture]
related-to: [layered-skill-loading-architecture, forge-mobile-safe-core, manifest-as-coherence-anchor]
promoted-into: []
---

## Summary

Three distinct file types serve different roles in an AI-assisted repository workflow and should not be conflated. Skills define reusable operational methods. Context files define the world or repository the AI is working in. Memory files preserve prior decisions, preferences, and active threads across sessions. Mixing these responsibilities degrades both clarity and reliability.

## Detail

### The three types

**Skills** (`_skills/`, `.claude/`)
- Reusable operational patterns, procedures, and methods
- Domain-agnostic or lightly parameterized
- Do not change based on project state
- Example: the challenge loop procedure, the drift check, the edit protocol
- Portable — can be copied across projects

**Context files** (e.g., `MANIFEST.md`, `CLAUDE.md`, `AGENTS.md`)
- Define the world the AI is operating in for a given session
- Project-specific — describes the authority chain, file registry, invariants, and conventions of this repo
- Loaded at session start to orient the AI to the specific project
- Not portable — must be authored per project
- Example: MANIFEST.md, which tells the AI what Forge is and how to work within it

**Memory files** (e.g., `DECISIONS.md`, carry-forward sets, concept ledger state)
- Preserve prior decisions, preferences, active threads, and ongoing state across sessions
- Accumulate over time
- Prevent re-litigating resolved decisions
- Example: DECISIONS.md recording why promotion was separated from the stage sequence

### Why the separation matters

Conflating these types leads to predictable failures:
- Putting decisions into skill files makes skills project-specific and non-portable
- Putting skills into context files bloats the session orientation load
- Putting context into memory files makes it hard to know what is current vs. historical

Each type has a different update frequency, portability, and authority scope. Skills are slow-changing and portable. Context is project-specific and changes with the project structure. Memory accumulates and should be append-primarily (old decisions are rarely removed).

### The loading order

At session start, the correct loading order is:
1. Context files (orient to the project)
2. Memory files (restore prior state)
3. Skills (activate operational methods)

Skills loaded before context may operate on wrong assumptions. Memory loaded before context may reference entities the AI doesn't yet know about.

### Relationship to the layered skill loading architecture

This concept defines what the three types *are*. The layered skill loading architecture defines *how* skills (one of the three types) are loaded into a session. Together they provide a complete model for session initialization.

## Open questions

- Whether memory files should have a canonical location and format in the repo (currently ad-hoc)
- How context files should signal to the AI what memory files are relevant to load
- Whether the loading order should be encoded in `AGENTS.md`/`CLAUDE.md` as an explicit instruction

## Promotion candidates

Candidate for the repo hook convention formalization. Should inform the design of session initialization in the Forge Guidance Engine.
