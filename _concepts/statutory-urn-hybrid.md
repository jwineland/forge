---
id: statutory-urn-hybrid
name: Statutory-URN Hybrid Citation Format
status: formalized
citation: forge:2026-04-19-gemini-citation-modality:urn-design:exchange-7
created: 2026-04-19
depends-on: [session-citation-system]
related-to: [semantic-graph-foundation, object-oriented-documentation]
promoted-into: []
---

## Summary

A citation format that combines the precision and gravitas of legal/statutory citation with machine-readable URN structure. The human-readable form reads like a legal reference; the machine-readable form is a URN addressable by scripts and grep.

## Detail

### The two forms

**Human citation:** `Title 2, Part 1 (Gemini) Ch. 4:12` — reads like a legal or academic reference; provides context at a glance; suitable for inline documentation, code comments, and design docs.

**Machine URN:** `urn:sec-arch:spiffe:gemini:04:v12` — colon-delimited, grep-friendly, scriptable; can be scanned across a Git repo to generate a table of assertions or cross-reference map.

### Tier mapping

| Tier | Legal term | URN segment | Example |
|---|---|---|---|
| 1 | Title | domain | `sec-arch`, `srv-val`, `km` |
| 2 | Part | book | `spiffe`, `net`, `storage` |
| 3 | Section | actor | `gemini`, `claude`, `gpt4` |
| 4 | Chapter | session | `04`, `2026-04-19` |
| 5 | Verse | element | `v12`, `v04` |

### Sub-verse branching

When a response is regenerated or a prompt is edited within a session, linear verse numbering breaks. The notation `v12.b` handles the second attempt at exchange 12. This must be encoded in the citation system.

### Git integration properties

- URN delimiter (colon) makes grep reliable: `grep -r "urn:sec-arch:*:gemini" .`
- URN as primary key means workflow systems store only the pointer, not the logic
- Conflict documentation: `urn:spiffe:gemini:04:v12 vs urn:spiffe:claude:02:v05 re: MediationGrant TTL`

### Relationship to JSON-LD `@id`

The URN format maps directly to JSON-LD IRI identifiers. The `@id` field in the Forge vocabulary can carry the full URN, giving machine-readable citations a standard semantic web anchor.

## Open questions

- Whether the actor/AI platform tier should be a first-class citation segment or embedded in session ID
- Namespace registration: `forge.jwineland.io` as IRI base, or a public namespace like `urn:forge:`
- Sub-verse branching notation needs to be incorporated into the citation system invariant

## Promotion candidates

Candidate for `MANIFEST.md` citation address invariant (update to include sub-verse branching). Candidate for `_vocabulary/forge-context.jsonld` (sub-verse notation). Integrates with `session-citation-system` as a refinement.
