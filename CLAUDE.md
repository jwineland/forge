# CLAUDE.md

This repository is the Forge default concept registry. Begin every non-trivial session by reading `MANIFEST.md`.

## Required orientation

1. Read `MANIFEST.md` — scope, authority chain, invariants, routing rules
2. Read `_vocabulary/forge-context.jsonld` if the session involves vocabulary or graph work
3. Check `_parked/` for concepts with triggers relevant to current work

## Session classification

Classify the task before any action:

- **Excavation** — extracting concepts from a conversation into the registry
- **Concept development** — formalizing, linking, or updating an existing concept
- **Promotion** — moving a concept into a project corpus
- **Vocabulary work** — modifying the JSON-LD context or intent registry
- **Governance** — updating MANIFEST, edit protocol, or registry structure

## Layer boundary rules

- `_vocabulary/` defines — do not invent vocabulary outside it
- `_concepts/` records — do not embed business logic in concept files
- `_sessions/` is append-only — do not edit committed excavation records
- `_parked/` requires a trigger — do not park without a condition

## Routing

- Default: all excavations deposit here
- `forge this in [repo]`: deposit directly to named project repo
- `forge this for [repo]`: deposit here, tag as candidate for named project

## Anti-patterns

- Do not merge concepts that have distinct identities even if they seem similar
- Do not promote a concept without checking for prior formalization in `_concepts/`
- Do not modify `_sessions/` records after they are committed
- Do not create a concept file without a citation address linking to its source
