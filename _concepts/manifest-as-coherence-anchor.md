---
id: manifest-as-coherence-anchor
name: MANIFEST as Coherence Anchor
status: formalized
citation: forge:2026-04-18-claude-general-docs:corpus-architecture:manifest-design
created: 2026-04-18
depends-on: []
related-to: [corpus-lifecycle-system, three-layer-skill-architecture, semantic-graph-foundation]
promoted-into: [general_docs:MANIFEST.md]
---

## Summary

A multi-file document corpus requires a single authoritative orientation document — the MANIFEST — that defines scope, authority chain, key invariants, and maintenance protocol. The MANIFEST is the coherence anchor that prevents drift across sessions, contributors, and AI platforms.

## Detail

The MANIFEST governs corpus coherence; it does not redefine business concepts owned by the authority document. If the MANIFEST and the authority document conflict on business content, that is drift to resolve — not two equal sources of truth.

The MANIFEST has four core functions:

1. **Authority chain** — which file owns which concept; which files are derived
2. **Invariants table** — facts that must remain consistent across all files
3. **File registry** — every file with its role and alignment status
4. **Design decisions** — significant structural choices with rationale

The authority hierarchy is: framework defines → manifest records and guards → derived files illustrate or instantiate → agent and skill files govern editing behavior.

For large corpora, a two-level hierarchy applies: a root MANIFEST owns cross-cutting invariants and a registry of sub-corpora. Directories that grow beyond a threshold get their own scoped MANIFEST that defers to the root for cross-cutting invariants.

## Open questions

The threshold for sub-manifest creation is not yet formally defined. Current working heuristic: five or more substantive files with internal authority dependencies.

## Promotion candidates

Already promoted into `general_docs`. Core concept for `corpus-template-doc` and `corpus-template-eng`.
