# Forge Manifest

## Purpose of This File

This manifest is the authoritative orientation document for the Forge repository. Forge is a semantic knowledge lifecycle system — it governs how concepts are excavated from conversations, classified, versioned, parked, promoted, and composed into corpus content across any project.

This repo is the **default general concept registry**. It is the landing place for all `forge this conversation` operations unless a specific project repo is named.

**Read this file first** at the start of any working session involving concept excavation, classification, or promotion.

---

## Corpus Identity

**What this is:** A concept registry and knowledge lifecycle management system. It captures meaningful concepts emerging from human-AI collaborative work, records their provenance, tracks their development state, and routes them for use in specific project corpora.

**What it is not:** A project-specific corpus. Project corpora (general_docs, ironfish, etc.) are governed by their own MANIFESTs and contain their own authority documents. Forge governs the lifecycle of the concepts that feed those corpora.

**The problem it solves:** Collaborative AI sessions generate more structured knowledge than can be tracked manually. Concepts arise, relate to each other, become partially formalized, get set aside, and are lost when sessions end. Forge is the persistence and organization layer that prevents that loss.

---

## Session Bootstrap

1. Read this file
2. Read `_vocabulary/forge-context.jsonld` if the session involves schema or graph work
3. Check `_parked/` for concepts with triggers relevant to current work
4. Check `_concepts/` for prior work on the topic at hand
5. For a new excavation: follow the procedure in `_sessions/README.md`

---

## Authority Model

| Layer | Location | Owns |
|---|---|---|
| Vocabulary authority | `_vocabulary/forge-context.jsonld` | Node types, edge types, status vocabulary, reference types |
| Concept registry | `_concepts/` | Individual concept definitions, dependencies, promotion status |
| Session index | `_sessions/` | Excavation records, citation addresses, session metadata |
| Parked concepts | `_parked/` | Deferred concepts with trigger conditions |
| Manifest coherence | `MANIFEST.md` | This file — authority chain, invariants, maintenance protocol |
| Editing behavior | `CLAUDE.md`, `AGENTS.md`, `.claude/` | How humans and AI tools work on this repo |

---

## Key Invariants

### Concept status vocabulary
Exactly these states, in this progression:
- `excavated` — extracted from conversation, not yet classified
- `classified` — type assigned, dependencies noted
- `formalized` — fully described with metadata complete
- `parked` — intentionally deferred with trigger condition
- `promoted` — promoted into a specific project corpus
- `forked` — forked for specialized use in a project
- `archived` — no longer actively tracked

### Reference types for content modules
- `floating` — always resolve to most current validated version
- `locked` — resolve to specific content hash, immutable
- `constrained` — resolve to version satisfying declared constraints

### Citation address format
```
forge:SESSION_ID:THREAD_ID:EXCHANGE_N[:EMERGENCE_N]
```
Example: `forge:2026-04-18-claude-general-docs:forge-design:exchange-47:emergence-2`

Components:
- **SESSION_ID** — date + platform + context identifier
- **THREAD_ID** — named topic area within the session
- **EXCHANGE_N** — turn pair number within the thread
- **EMERGENCE_N** — optional: specific emergence point within an exchange

### Routing rules
- `forge this conversation` — deposits to this repo, no project scope
- `forge this in [repo]` — deposits directly to named project repo
- `forge this for [repo]` — deposits here, tagged as candidate for named project

---

## File Registry

| File | Role | Status |
|---|---|---|
| `MANIFEST.md` | Corpus orientation and governance | Current |
| `CLAUDE.md` | Claude Code entrypoint | Current |
| `AGENTS.md` | Agent framework entrypoint | Current |
| `.claude/edit-protocol.md` | Edit procedure | Current |
| `.claude/drift-check.md` | Alignment audit | Current |
| `_vocabulary/forge-context.jsonld` | JSON-LD vocabulary and @context | v0.1 — active design |
| `_vocabulary/intent-registry.md` | Named intent type definitions | Stub — needs design session |
| `_concepts/README.md` | Concept file format and usage | Current |
| `_concepts/*.md` | Individual concept records | See each file |
| `_sessions/README.md` | Session excavation format and citation system | Current |
| `_sessions/2026-04-18-claude-general-docs/excavation.md` | First excavation — this session | Current |
| `_sessions/2026-04-18-claude-general-docs/index.jsonld` | Machine-readable session index | Current |
| `_parked/README.md` | Park mechanism documentation | Current |
| `_parked/*.md` | Individual parked concept records | See each file |
| `_skills/README.md` | Placeholder for corpus-skills sync | Stub |

---

## Known Gaps and Future Work

| Item | Priority | Notes |
|---|---|---|
| Automated excavation Action | High | Currently manual; GitHub Action to trigger on conversation deposit |
| `corpus-skills` sync Action | High | `_skills/` should sync from jwineland/corpus-skills when it exists |
| Intent registry design | High | `_vocabulary/intent-registry.md` is a stub; needs full design session |
| ChatGPT Forge session excavation | High | Prior ChatGPT work on completeness scoring and concept lifecycle to be deposited |
| Completeness scoring methodology | Medium | Developed in ChatGPT sessions; needs integration with concept status model |
| GitHub Pages concept browser | Low | Rendered view of concept registry for navigation |
| Cross-repo promotion Action | Medium | Automated PR creation when concept is promoted into a project repo |

---

## Maintenance Protocol

1. Concepts are never deleted — they are archived with a reason
2. Session records are immutable once committed — corrections go in a separate amendment file
3. The vocabulary spec is versioned — breaking changes require a new version, not in-place modification
4. Parked concepts must have a trigger condition — open-ended parking is not permitted
5. Commit messages must identify the concept or session being affected, not just the file
