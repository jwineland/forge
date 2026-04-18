---
id: semantic-graph-foundation
name: Semantic Graph Foundation
status: formalized
citation: forge:2026-04-18-claude-general-docs:semantic-graph-intent:graph-design
created: 2026-04-18
depends-on: []
related-to: [manifest-as-coherence-anchor, intent-as-semantic-contract, bom-binding-locked-composition]
promoted-into: [forge:_vocabulary/forge-context.jsonld]
---

## Summary

The MANIFEST as currently designed is a manually-maintained flat projection of what is actually a directed acyclic graph. Making the graph explicit changes what the system can do — enabling transitive drift detection, BOM-binding, intent-as-graph-query, and fitness attestation — while remaining human-readable through rendered projections.

## Detail

### Why JSON-LD

- **W3C VC/DID alignment**: BoundaryMark targets W3C VCs and DIDs, both of which use JSON-LD natively. A content graph in JSON-LD can be directly embedded in or referenced from a VC.
- **SCITT alignment**: IETF SCITT expects content identifiers that are stable, resolvable, and content-addressed. JSON-LD `@id` fields with IRIs (not file paths) satisfy this.
- **Stable node identity**: Module IDs persist across renames, moves, and refactors. A module can move from `_modules/nic/ethtool-inventory.md` to `_modules/network/nic/ethtool-inventory.md` without breaking compositions that reference it by IRI.
- **Human-readable at the right level**: With a well-designed `@context`, JSON-LD reads almost like YAML for common cases.

### Core node types

- `Concept` — knowledge unit extracted from conversation
- `ContentModule` — discrete, independently versioned document unit
- `Session` / `Thread` / `Exchange` / `Emergence` — conversation provenance hierarchy
- `LockedComposition` — content-addressed snapshot of a module subgraph
- `IntentDeclaration` — named composition with audience and content contract
- `OutputArtifact` — materialized instance of an intent at a point in time

### Core edge types

- `dependsOn` — this node requires that node to be coherent
- `composesInto` — this module is included in this intent or composition
- `locksTo` — this artifact is bound to this module at this exact version
- `supersedes` — this content replaces that content; prior artifacts retain locked references
- `cites` — provenance link to session citation address
- `promotedInto` — concept has been promoted into a project corpus

### MANIFEST as derived view

With the graph as foundation, the MANIFEST becomes a human-readable projection of the graph — generated from the graph schema rather than authoritative over it. The authoritative representation is the schema; the MANIFEST is a rendered view. This is an inversion from the current design but enables automated consistency checking.

### Drift detection improvement

The current MANIFEST-based drift check requires knowing what to check. The graph catches transitive dependencies automatically. If Phase 3 validation criteria change, the graph knows the validation template, Phase 2 brief, and executive summary all have transitive dependencies on that node.

## Open questions

- Migration path from current flat MANIFEST to graph-derived MANIFEST
- Tooling for graph traversal and drift detection (Python library, GitHub Action, or both)
- IRI namespace finalization (currently using `forge.jwineland.io` as placeholder)
- Rendering pipeline: how graph nodes become MANIFEST table rows

## Promotion candidates

Already partially promoted into `forge:_vocabulary/forge-context.jsonld`. Core concept for Forge schema design.
