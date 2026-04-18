---
id: bom-binding-locked-composition
name: BOM-Binding and Locked Composition
status: formalized
citation: forge:2026-04-18-claude-general-docs:semantic-graph-intent:manufacturing-pattern
created: 2026-04-18
depends-on: [semantic-graph-foundation]
related-to: [intent-as-semantic-contract, boundarymark-fitness-attestation]
promoted-into: []
---

## Summary

Content modules can be composed into two reference types: floating (always resolve to most current validated version) and locked (resolve to specific content hash, immutable). A first-article build generates a locked composition snapshot that binds a specific set of content module versions to a specific BOM. Future builds of that BOM resolve against that snapshot.

## Detail

This pattern generalizes the software dependency management model (npm lockfiles, cargo.lock) to knowledge content. The core distinction:

**Floating reference** — "use the most current validated version of this module." Appropriate for firmware version, test tooling, style guidelines. These evolve and consuming artifacts should track current.

**Locked reference** — "use exactly this content at exactly this content hash." Appropriate for the specific procedure by which a specific BOM was built and validated. Immutable. First-article build generates the lockfile; all future builds of that BOM resolve against it.

The semantic graph makes both reference types explicit and computable. A locked composition is a snapshot of a subgraph at a specific point in time with every node replaced by its content hash. A floating composition is a subgraph where edges carry version constraints rather than hashes.

### Manufacturing application

System: specific HBA, two NIC types, SSDs, HDDs. Content modules: 100Gbps bandwidth test, NIC ethtool inventory, NIC ethtool optimization, HBA inventory, HBA config, HBA stress test.

First article build: compose modules → validate → snapshot → lock to BOM. The locked composition is the "how this platform was built" record.

Subsequent builds from same BOM: resolve against locked snapshot. Upstream module changes do not affect locked builds.

New system (different BOM): compose from most current modules. Records specifically what content set it was built from.

### Selective invariance

Not all elements need to be locked or floating uniformly. Card population and component mix may be locked (BOM-invariant). Firmware version may be floating (always use current). The composition model supports mixed reference types at the module level.

### Broader pattern

Reproducible knowledge composition is domain-agnostic: legal documents composed from clauses, regulatory submissions from evidence modules, technical handbooks from procedure modules, AI output audit trails. The pattern applies wherever "prove this instance was produced from this exact knowledge set and reproduce it on demand" is a requirement.

## Open questions

- Content hash algorithm standardization (SHA-256 assumed; needs formal specification)
- Lockfile format and storage location
- Version constraint syntax for constrained reference type
- Integration with BoundaryMark attestation chain

## Promotion candidates

Candidate for `forge:_vocabulary/forge-context.jsonld` (LockedComposition node type already defined). Candidate for manufacturing-specific corpus template when that is created.
