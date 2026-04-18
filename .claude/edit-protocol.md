# Forge Edit Protocol

## Before any edit

1. Read `MANIFEST.md`
2. Identify which layer the change affects (vocabulary / concepts / sessions / parked / governance)
3. Confirm the change is appropriate for that layer — session records are append-only, vocabulary requires versioning

## Making changes

4. For concept files: update status field when status changes; always preserve citation address
5. For vocabulary: increment version comment at top of `forge-context.jsonld`; document breaking changes
6. For session records: never edit — create an amendment file if correction is needed
7. For parked concepts: update trigger and reason fields; do not change the original parking record

## Committing

8. Concept-first commit messages: identify the concept or operation
   - Good: `Formalize intent-as-semantic-contract concept`
   - Bad: `Update concept file`
9. One concept or operation per commit where practical

## MCP tool call formatting

MCP tool call content is raw text, not JSON-encoded. Use actual line breaks in parameter content — not `\n` escape sequences. This applies to PR descriptions, review bodies, and any multi-line string passed to a GitHub MCP tool. Broken formatting can be corrected with `update_pull_request` after the fact.

## Drift detection

Run `.claude/drift-check.md` before closing any session that touched vocabulary or multiple concept files.
