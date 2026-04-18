---
id: session-citation-system
name: Session Citation System
status: formalized
citation: forge:2026-04-18-claude-general-docs:forge-design:citation-design
created: 2026-04-18
depends-on: []
related-to: [forge-concept-lifecycle, manifest-as-coherence-anchor]
promoted-into: [forge:MANIFEST.md]
---

## Summary

A canonical citation system for conversational knowledge that enables precise, stable, human-readable addresses for any concept emergence point in any session. Analogous to biblical citation — immutable source, addressable at multiple granularities, cross-referenceable.

## Detail

### Address format

```
forge:SESSION_ID:THREAD_ID:EXCHANGE_N[:EMERGENCE_N]
```

**Session** — the full conversation. Addressed by platform + date + context identifier. The source text is immutable once deposited.

**Thread** — a coherent sub-discussion within the session. Named topic areas that may flow continuously in conversation but represent distinct conceptual domains.

**Exchange** — a specific human/AI turn pair where a meaningful concept or decision occurs.

**Emergence** — optional subdivision: the specific statement within an exchange where the concept first appears in recognizable form. Used for precision citation.

### Example

`forge:2026-04-18-claude-general-docs:forge-design:exchange-47:emergence-2`

Reads: from the session of April 18, 2026 on Claude working with general_docs, in the forge-design thread, at the 47th exchange, second emergence point.

### Resolution

A tool given a citation address can retrieve: the full exchange, the surrounding thread context, the full session. Granularity is selectable.

### Integration with DECISIONS.md

Decision log entries can carry forge citation addresses, linking the recorded decision to the full conversational context in which it emerged. This is more precise than prose descriptions and recovers reasoning that prose cannot fully capture.

## Open questions

- Exchange numbering for manual bootstrapping (before automated excavation exists) is approximate — needs a convention
- Session deposit format (how a conversation transcript is stored in `_sessions/`) needs specification
- Resolution tooling implementation path TBD

## Promotion candidates

Already promoted into `forge:MANIFEST.md` as an invariant. Core to the Forge system design.
