---
id: three-layer-skill-architecture
name: Three-Layer Skill Architecture
status: formalized
citation: forge:2026-04-18-claude-general-docs:corpus-architecture:skill-layer-design
created: 2026-04-18
depends-on: [manifest-as-coherence-anchor]
related-to: [corpus-lifecycle-system, human-ai-role-separation]
promoted-into: [general_docs:_skills/, general_docs:CLAUDE.md, general_docs:AGENTS.md]
---

## Summary

Skills and agent files in a governed corpus operate at three distinct layers with different portability, specificity, and purposes. Conflating these layers creates a tension between portability and immediate usability that is resolved by keeping them separate.

## Detail

The three layers are:

**Layer 1 — Generic procedure (`_skills/`):** Purpose, when-to-use, procedure steps, success criteria, output format. No project-specific references, no file names, no prompt templates. Portable across any corpus. Copy this directory to any new project and it works without modification.

**Layer 2 — Project-specific operational (`.claude/`):** Concrete prompts with actual file names, specific invariants, real phase names, and copy-paste templates. Written to be immediately executable without adaptation. These do not travel — they are rebuilt for each project by instantiating Layer 1 patterns against the project's MANIFEST.

**Layer 3 — Auto-load entrypoint (`CLAUDE.md`, `AGENTS.md`):** Thin, fast orientation. Session classification taxonomy, layer boundary rules, required reading sequence. Fires automatically on every CLI session. Should be scannable in under 30 seconds.

The practical rule: `_skills/` describes what and why. `.claude/` describes how for this specific corpus. `CLAUDE.md`/`AGENTS.md` describe what to do first.

## Open questions

None — this concept is fully formalized and implemented.

## Promotion candidates

Already promoted into `general_docs`. Candidate for `corpus-template-doc` and `corpus-template-eng` when those repos are created.
