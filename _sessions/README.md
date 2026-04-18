# Session Records

This directory contains excavation records from collaborative AI sessions. Each session gets its own subdirectory named by date, platform, and context.

## Directory naming

```
YYYY-MM-DD-PLATFORM-CONTEXT/
```

Examples:
- `2026-04-18-claude-general-docs/` — Claude session working on general_docs
- `2026-04-17-chatgpt-forge-design/` — ChatGPT session on Forge design

## Required files per session

**`excavation.md`** — human-readable excavation record. Contains:
- Session metadata (date, platform, context, participants)
- Thread index (named topic areas identified in the session)
- Concept list (all concepts extracted, with status and citation address)
- Promoted concepts (what was promoted into which repo)
- Parked concepts (what was deferred and why)
- Open threads (unresolved questions carrying forward)

**`index.jsonld`** — machine-readable session index. JSON-LD representation of the session graph: Session node, Thread nodes, key Exchange nodes, Concept nodes with citation edges.

## Citation address system

Every concept extracted from a session gets a citation address in the format:

```
forge:SESSION_ID:THREAD_ID:EXCHANGE_N[:EMERGENCE_N]
```

Components:
- **SESSION_ID** — matches the directory name (YYYY-MM-DD-PLATFORM-CONTEXT)
- **THREAD_ID** — kebab-case name of the thread within the session
- **EXCHANGE_N** — turn pair number within the thread (approximate for manual bootstrapping)
- **EMERGENCE_N** — optional precision locator within an exchange

## Immutability rule

Session records are append-only after initial commit. If a correction is needed, create an amendment file (`excavation-amendment-YYYY-MM-DD.md`) in the same directory. Do not modify the original excavation record.

## Manual vs automated excavation

This directory is currently populated manually. The automated excavation Action (planned) will deposit structured records here directly from conversation transcripts. Manual records use approximate exchange numbers and note the approximation.
