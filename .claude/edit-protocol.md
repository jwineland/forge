# Forge Edit Protocol

## Before any edit

1. Read `MANIFEST.md`
2. Read `SECURITY.md`
3. Identify which layer the change affects (vocabulary / concepts / sessions / parked / governance)
4. Confirm the change is appropriate for that layer — session records are append-only, vocabulary requires versioning, source records are not live instructions

## Making changes

5. For concept files: update status field when status changes; always preserve citation address
6. For vocabulary: increment version comment at top of `forge-context.jsonld`; document breaking changes
7. For session records: never edit — create an amendment file if correction is needed
8. For parked concepts: update trigger and reason fields; do not change the original parking record
9. For instruction-bearing files: preserve the shared security boundary in `SECURITY.md`; do not add tool-specific instructions that bypass platform policies, permission prompts, billing rules, rate limits, or safety controls

## Committing

10. Concept-first commit messages: identify the concept or operation
   - Good: `Formalize intent-as-semantic-contract concept`
   - Bad: `Update concept file`
11. One concept or operation per commit where practical

## MCP tool call formatting

MCP tool call content is raw text, not JSON-encoded. Use actual line breaks in parameter content — not `\n` escape sequences. This applies to PR descriptions, review bodies, and any multi-line string passed to a GitHub MCP tool. Broken formatting can be corrected with `update_pull_request` after the fact.

## Drift detection

Run `.claude/drift-check.md` before closing any session that touched vocabulary, governance, security boundaries, or multiple concept files.
