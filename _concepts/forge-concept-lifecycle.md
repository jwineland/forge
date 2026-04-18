---
id: forge-concept-lifecycle
name: Forge Concept Lifecycle
status: formalized
citation: forge:2026-04-18-claude-general-docs:forge-design:lifecycle-design
created: 2026-04-18
depends-on: [session-citation-system]
related-to: [manifest-as-coherence-anchor, human-ai-role-separation]
promoted-into: [forge:MANIFEST.md]
---

## Summary

Concepts extracted from collaborative AI sessions follow a defined lifecycle with explicit states, transitions, and routing rules. The lifecycle prevents loss of meaningful structured knowledge and enables progressive formalization without requiring complete specification at time of extraction.

## Detail

### State machine

```
excavated → classified → formalized
                ↓
             parked (with trigger)
                ↓
            (trigger fires)
                ↓
          promoted | forked
```

**Excavated** — concept extracted from conversation, identity established, citation address assigned. Minimal metadata.

**Classified** — type assigned, dependencies noted, related concepts identified. Enough structure to know where it belongs.

**Formalized** — fully described with complete metadata, open questions identified, promotion candidates specified.

**Parked** — intentionally deferred. Requires trigger condition, parking reason, and optional decay policy. Cannot be parked without a trigger.

**Promoted** — moved into a project corpus as a content element. Promotion record carries citation address.

**Forked** — branched for specialized use. Original remains; fork has its own identity.

### Routing

- `forge this conversation` → default repo (jwineland/forge)
- `forge this in [repo]` → directly to named project repo
- `forge this for [repo]` → default repo, tagged as candidate for named project

### Iterative excavation

Excavation is idempotent. Each concept has a stable identity derived from semantic content fingerprint. Subsequent excavations of the same conversation process only the delta — new concepts since the last session marker. Evolved concepts generate update candidates for human review rather than auto-merging.

## Open questions

- Fingerprinting algorithm for concept identity needs formal specification
- Session marker format and storage location needs design
- Decay policy enforcement mechanism (time-based vs reference-count-based) needs decision

## Promotion candidates

Core concept for Forge system design. Already partially promoted into `forge:MANIFEST.md`.
