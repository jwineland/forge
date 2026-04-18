# Concept Registry

This directory contains individual concept records. Each file represents one concept that has been excavated from a conversation, classified, and recorded for future use.

## File naming

Files are named by concept ID using kebab-case: `concept-id.md`

The concept ID is stable — it does not change if the concept is renamed or refined. The `name` field in the front matter carries the current human-readable name.

## Front matter schema

Every concept file must have YAML front matter with these fields:

```yaml
---
id: concept-id-kebab-case
name: Human-readable concept name
status: excavated | classified | formalized | parked | promoted | forked | archived
citation: forge:SESSION_ID:THREAD_ID:EXCHANGE_N[:EMERGENCE_N]
created: YYYY-MM-DD
depends-on: []           # list of concept IDs this concept requires
related-to: []           # list of concept IDs with non-dependency relationships
promoted-into: []        # list of repo:path references if promoted
forked-from: null        # concept ID if this is a fork
---
```

## Body sections

After front matter, each concept file contains:

- **Summary** — one to three sentences capturing the core idea
- **Detail** — fuller description, design rationale, known constraints
- **Open questions** — unresolved aspects that block full formalization
- **Promotion candidates** — where this concept could be promoted and what's needed

## Status transitions

Status moves forward, never backward. If a promoted concept needs revision, a new version is forked from it. The original promotion record is preserved.
