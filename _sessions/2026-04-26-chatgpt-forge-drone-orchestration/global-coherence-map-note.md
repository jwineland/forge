# Design Note: Global Coherence After Authority-Document Decomposition

**Status:** Design concern requiring review  
**Date:** 2026-04-26  
**Related session:** `2026-04-26-chatgpt-forge-drone-orchestration`  

---

## Relationship to Existing Forge Concepts

The most directly related existing Forge concept is `manifest-as-coherence-anchor`, which already names the need for a coherence anchor across multi-file corpora and defines the MANIFEST as the place that records scope, authority chain, invariants, and design decisions.

The design pressure described in this note generalizes that concept's scope: `manifest-as-coherence-anchor` addresses corpus governance coherence; the Global Coherence Map addresses design-state coherence across modular design artifacts. The Atlas or equivalent artifact may be an extension of, companion to, or derived projection from the MANIFEST-as-anchor mechanism — this relationship should be resolved during rationalization.

See also `design-atlas-related-work-survey.md` in this session directory for a full survey of related existing concepts.

---

## Problem Statement

The historical full-authority-document workflow had an important advantage: a frontier reasoning model could survey the entire design at once and identify gaps, contradictions, duplicated concepts, missing assumptions, and inconsistencies that spanned individual concept or module boundaries.

As authority documents grew to several thousand lines, this became expensive, slow, and unwieldy. The emerging modular Forge approach reduces repeated full-document processing by decomposing design state into concepts, sessions, packets, plans, and project-specific artifacts.

However, decomposition creates a new risk:

> Local modular review may miss global design drift.

If each model or drone only sees bounded context packets, Forge may lose the cross-boundary coherence checks that made full authority-document cycling useful.

---

## Design Pressure

Forge needs a replacement for whole-document global survey that preserves the benefits of global coherence without requiring every design turn to reload the entire authority corpus.

This should not be treated as a minor housekeeping issue. It is central to whether Forge can support modular design without becoming incoherent over time.

---

## Candidate Requirement

Forge should maintain a first-class **Global Coherence Map** or equivalent artifact that represents the current design as a navigable, summarized, cross-linked structure.

This artifact should support:

- cross-boundary inconsistency detection
- concept dependency mapping
- design assumption tracking
- unresolved question visibility
- duplicate or divergent concept detection
- design area ownership or scope mapping
- ADR / decision linkage
- implementation-plan linkage
- drift detection between design and implementation
- periodic frontier review over compressed global state

---

## Possible Shape

A global coherence mechanism may include several layered artifacts:

1. **Design Atlas** — human-readable map of current project design areas, concepts, decisions, risks, and open questions.
2. **Concept Graph** — machine-readable nodes and edges representing concepts, designs, decisions, dependencies, tensions, and reuse relationships.
3. **Coherence Ledger** — list of known conflicts, unresolved tensions, stale assumptions, and deferred rationalization items.
4. **Design Digest** — compressed current-state summary suitable for frontier model review.
5. **Drift Report** — periodic comparison of implementation state, plans, and preserved design intent.

The goal is not to create another massive authority document. The goal is to create a layered map that can be inspected at different levels of detail.

---

## Review Question

What is the minimal global coherence mechanism that preserves the cross-design insight of full authority-document review while avoiding repeated processing of every underlying document?

Candidate names:

- Global Coherence Map
- Design Atlas
- Design Map
- Coherence Ledger
- Concept-Weave Map

**Rejected candidate: "Authority Map"** — In Forge vocabulary, "authority" denotes a canonical governance source (authority document, authority chain, authority repository). A Global Coherence Map is a *derived projection* over existing design state — the opposite of an authority source. Naming it "Authority Map" would create semantic tension with Forge's existing governance vocabulary and mislead models reasoning about which artifact governs which decisions. This name is rejected and should not be re-proposed.

---

## Relationship to Drone Architecture

Drones may help maintain the global coherence layer:

- local drones update indexes and summaries
- classifier drones update concept relationships
- drift drones flag mismatches and stale assumptions
- packet drones produce frontier-review digests
- frontier review drones periodically challenge the compressed global map

However, drones are not the solution by themselves. The core missing artifact is a durable cross-boundary representation of design coherence.

---

## Proposed Principle

> Modular design packets are safe only if they are anchored to a maintained global coherence map.

---

## Non-Implementation Constraint

This note captures a design gap and candidate requirement. It does not implement a global coherence map, schema, graph, drone, or review process.
