---
id: object-oriented-documentation
name: Object-Oriented Documentation (OOD)
status: formalized
citation: forge:2026-04-19-gemini-citation-modality:ood-documentation:exchange-11
created: 2026-04-19
depends-on: [semantic-graph-foundation]
related-to: [actionable-intent-verses, bom-binding-locked-composition, statutory-urn-hybrid]
promoted-into: []
---

## Summary

An application-layer pattern for structured documentation that treats knowledge sections as object instances with properties (metadata), methods (tests or procedures), and inheritance relationships. Documents are not flat text — they are typed objects that can be composed, extended, and queried like code.

## Detail

### Core mapping

| OOD concept | Documentation equivalent | Example |
|---|---|---|
| Namespace / Class | Subsystem or domain | `NET`, `STORAGE`, `COMPUTE` |
| Object / Instance | Specific test or procedure | `100G_BW`, `HBA_FW`, `CPU_INT` |
| Method | Executable action within a test | `ethtool -G eth0 rx 4096` |
| Property | Metadata field | `actor`, `urn`, `status` |
| Inheritance | Dependency relationship | `HBA_PATH_B inherits HBA_FW` |
| Encapsulation | Narrative/Intent separation | Human summary hides YAML payload |
| Polymorphism | Multi-platform variants | Same test, different target implementations |

### Inheritance in practice

If `HBA_PATH_B` inherits `HBA_FW`, a change to the firmware update procedure propagates automatically — every test that depends on it is flagged as potentially affected. This is the graph traversal pattern that prevents silent drift in modular test plans.

In the semantic graph vocabulary, this maps to the `dependsOn` edge type. An explicit `inherits` edge type may be warranted for the OOD inheritance case, to distinguish structural dependency (module A requires module B to make sense) from procedural inheritance (module A's execution presupposes module B has been executed).

### Document structure as class hierarchy

```
Namespace: SRV_VAL (Server Validation)
  Book/Class: NET (Network subsystem)
    Chapter/Method: 100G_BW
    Chapter/Method: OPT_ETH
    Chapter/Method: LACP_REL
  Book/Class: STORAGE
    Chapter/Method: HBA_FW
    Chapter/Method: HBA_PATH_A
    Chapter/Method: HBA_PATH_B  ← inherits HBA_FW
  Book/Class: COMPUTE
    Chapter/Method: MATH_INT
    Chapter/Method: MATH_FLT
```

### Relationship to semantic graph

OOD is an application-layer pattern that runs on top of the semantic graph infrastructure. The graph provides identity, edges, and traversal. OOD provides the naming conventions, inheritance semantics, and human mental model for working with the graph. They are complementary, not competing.

### Relationship to intent-as-semantic-contract

In OOD terms, an `IntentDeclaration` is a class definition — it specifies what an instance of that intent type must contain and what it inherits. A specific output artifact is an instance of that class.

## Open questions

- Whether `inherits` should be a distinct edge type from `dependsOn` in the vocabulary
- How OOD class hierarchies map to the corpus sub-manifest hierarchy
- Namespace conflict detection — if a verse in a child document contradicts the parent class definition

## Promotion candidates

Candidate for `_vocabulary/forge-context.jsonld` (potential `inherits` edge type). Candidate for corpus template documentation as the mental model for how modules relate. The server test application is a strong concrete example for documentation.
