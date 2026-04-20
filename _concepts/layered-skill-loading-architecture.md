---
id: layered-skill-loading-architecture
name: Layered Skill Loading Architecture
status: classified
citation: forge:2026-04-19-chatgpt-skills-architecture:skill-architecture:exchange-2
created: 2026-04-20
depends-on: [three-layer-skill-architecture]
related-to: [skills-context-memory-separation, forge-mobile-safe-core]
promoted-into: []
---

## Summary

Skills available to an AI system in a given session are loaded in layers, with different scopes and portability. Shared skills live in a canonical cross-repo location, repo-local skills live in the project repository, and session-specific or concept-scoped skills are bound at session initialization. A skill that is not loaded into the active session context is not available, regardless of where it is stored.

## Detail

### The three loading layers

**Layer 1 — Shared / cross-repo skills**
Live in a canonical shared location (e.g., `jwineland/corpus-skills`). These are reusable operational patterns with no project-specific dependencies. They must be explicitly loaded into a session to become active — their existence in the shared repo does not automatically make them available.

**Layer 2 — Repo-local skills**
Live in the project repository under `_skills/`. These are instantiated versions of shared skills that have been bound to the specific repo's MANIFEST, authority chain, and conventions. Available in any session that loads the repo context.

**Layer 3 — Session-bound / concept-scoped skills**
Loaded at session initialization from a project's context files or dynamically based on the concept being worked on. These are the most specific and may reference project-specific file names, phase names, invariants, and operational details.

### The binding requirement

A skill that exists in a shared repository but has not been explicitly loaded into the current chat session is not active. It must be bound into the session context to be used. This is a key operational difference from how static documentation works — documentation is read; skills must be loaded and activated.

### Repo hooks

A common convention was sketched (but not yet formalized) for how `AGENTS.md`, `MANIFEST.md`, `_skills/`, `_context/`, and `_memory/` files interact to make the right skills available at session start without requiring manual invocation. This convention is a Known Gap in the MANIFEST.

### Relationship to three-layer-skill-architecture

This concept extends the three-layer skill architecture (which defines the `_skills/`, `.claude/`, and `CLAUDE.md`/`AGENTS.md` layers) by adding the dynamic loading and binding dimension. The three-layer architecture answers "where do skills live?" This concept answers "how do they become active in a session?"

## Open questions

- Formal specification of the repo hook convention for automatic skill loading at session start
- How skill conflicts are resolved when the same skill exists at multiple layers with different versions
- Whether skills should declare their own loading requirements (e.g., "load me when working on concept formalization")

## Promotion candidates

Candidate for the `corpus-skills` repo design when it is created. Should inform the repo hook convention formalization.
