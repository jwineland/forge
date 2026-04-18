# AGENTS.md

This repository is the Forge default concept registry.

## Before any work

1. Read `MANIFEST.md`
2. Follow `.claude/edit-protocol.md` for all changes
3. Session records in `_sessions/` are append-only — never modify committed records

## Authority rule

`_vocabulary/forge-context.jsonld` owns all node and edge type definitions. Concept files, session records, and parked concept files all defer to it. Do not introduce new types outside the vocabulary without a vocabulary update.

## Routing rule

Default excavation target is this repo. Named project routing (`in` or `for`) overrides the default.

## Constraints

- Every concept file must have a `citation` field pointing to its source session address
- Every parked concept must have a `trigger` field
- Vocabulary changes require a version bump in `forge-context.jsonld`
- Commit messages must identify the concept or operation, not just the filename
