---
id: promotion-as-transition
name: Promotion as Routing Transition, Not Maturity Stage
status: formalized
citation: forge:2026-04-19-chatgpt-skills-architecture:lifecycle-refinement:exchange-2
created: 2026-04-20
depends-on: [forge-concept-lifecycle]
related-to: [concept-progression-record, stage-aware-guided-advancement]
promoted-into: [forge:MANIFEST.md, forge:README.md]
---

## Summary

Promotion is the decision to route a concept into active use in a specific project corpus or downstream context. It is a working transition, not a maturity stage. A concept can be promoted at any point in the maturity progression — before or after formalization — and promotion does not indicate that formalization is complete.

## Detail

### The distinction

**Formalization** is about the *form* of the concept — making it rigorous, canonical, durable, and fully described. It is a maturity milestone.

**Promotion** is about the *routing* of the concept — elevating it into active use in a specific project, corpus, or downstream context. It is a disposition decision.

These are orthogonal. You can:
- Formalize a concept without ever promoting it (it stays in the registry as a reference)
- Promote a concept before it is fully formalized (early promotion for active use, with formalization to follow)
- Promote a concept to multiple downstream contexts
- Promote a concept and later revoke or supersede the promotion

### Why this matters

Earlier Forge designs (including the ChatGPT sessions) listed the canonical stage sequence as Excavation → Qualification → Rationalization → **Promotion** → Formalization → Operationalization. This implied promotion was a required step before formalization, and that all concepts should be promoted before being formalized.

That framing was incorrect for two reasons:
1. Many concepts are formalized and remain in the registry without ever being promoted to a specific project
2. Some concepts are useful to promote early, before full formalization, to unblock downstream work

The correct framing: the canonical maturity progression is Excavation → Qualification → Rationalization → Formalization → Operationalization. Promotion (along with parking and forking) is a working transition that can occur at any point.

### Parking is analogous

The same logic applies to parking. A parked concept is not at a fixed maturity stage — it is a concept that has been deliberately deferred regardless of its current maturity. When unparked, it returns to whatever stage it was at before parking.

### The concept status field

In concept front matter, the `status` field reflects the maturity stage (excavated, classified, formalized, operationalized, archived). Promotion status is tracked separately in the `promoted-into` field. A concept with `status: classified` and `promoted-into: [project:foo]` is a classified-stage concept that has been promoted — both facts are recorded independently.

## Open questions

- Whether promoted concepts that are later superseded should have their promotion records updated or remain as historical record
- How promotion to multiple downstream contexts is tracked when those contexts have different versions of the concept

## Promotion candidates

Already reflected in MANIFEST.md Design Decisions and concept status vocabulary. Should inform the Forge stage model document when created.
