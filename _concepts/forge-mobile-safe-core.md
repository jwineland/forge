---
id: forge-mobile-safe-core
name: Forge Mobile-Safe Core
status: formalized
citation: forge:chatgpt-ai-tool-broker-forge-design:mobile-interaction:exchange-28
created: 2026-04-19
depends-on: [stage-aware-guided-advancement, concept-progression-record]
related-to: [forge-guidance-engine, forge-concept-lifecycle]
promoted-into: []
---

## Summary

Forge must work across devices with different capabilities. Mobile/phone is a primary working surface, not a degraded fallback. The mobile-safe core defines what must be possible on any device regardless of screen size or available tooling, and separates that from what can be deferred to richer clients.

## Detail

### The design constraint

If Forge only works well from a laptop with full visibility into canvases, files, and long-form artifacts, it will fail the actual workflow. Forge needs a mode-aware interaction model where the same conceptual ratchet works across devices, even if the interaction surface differs.

The key separation: **what must be preserved** (device-independent) vs. **how the user sees or edits it** (device-specific).

### Three interaction modes

**Conversational / Mobile Mode**
Best for: phone, quick iteration, excavation, qualification, lightweight rationalization, reviewing carry-forward state.
Characteristics: chat-first, compact outputs, minimal structured editing burden, strong summaries and carry-forward discipline.

**Structured Workspace Mode**
Best for: desktop/laptop, canvas/doc editing, formalization, hierarchy editing, registry review, artifact mapping, deeper rationalization.
Characteristics: document-aware, registry-aware, side-by-side comparison, longer-form artifact construction.

**Repository / Formal Artifact Mode**
Best for: durable docs, ADRs, specs, schemas, registries, tracked deltas.
Characteristics: persistence-first, versioned changes, patch-oriented work, formal outputs.

### What MUST work on mobile (Level 1)

If this does not work on phone, Forge is too brittle:

- Create or revise concept records
- Inspect active carry-forward set
- Mark status: canonical / provisional / needs review
- Mark stage: excavation through operationalization
- Record promotion intent
- List unresolved questions
- Emit session ratchet summary

### The four mobile-safe output primitives

**Carry-Forward Card** — compact, human-readable, phone-friendly. Active concepts, stage/status, must-not-drop points, next unresolved items.

**Concept Progression Record** — fuller structured object, not always shown in full on phone. Core concept state.

**Formalization Queue** — lightweight list of items that need richer follow-up on a richer client. Each entry: item, why queued, suggested mode, expected output.

**Session Handoff Summary** — at the end of a session, regardless of device: current concept state, today's deltas, provisional additions, pending formalization queue, suggested next actions for richer client.

### The mode handoff requirement

When moving from phone to laptop, Forge should not force re-excavation. Instead it should support **mode handoff**:
- Summarize current concept state
- List carry-forward items
- List pending deeper work
- Identify which items need rich editing
- Preserve exact wording of important discoveries

So instead of "what were we doing again?" you get the current canonical concepts, today's deltas, provisional additions, pending formalization queue, and suggested next actions.

### Canvas rule

Canvas and similar workspace features should be treated as **richer projection surfaces**, not as the source of truth. If Android cannot see canvas but canvas is where the "real" work is, mobile becomes second-class and continuity breaks.

Source of truth = concept ledger + carry-forward set + artifact references. Canvas = editable/rendered workspace for certain artifacts.

## Open questions

- Implementation of the four mobile-safe primitives in the current Claude/ChatGPT chat interfaces
- How formalization queues are tracked between sessions (currently requires manual discipline)
- Whether a lightweight Forge companion app for mobile would be worthwhile

## Promotion candidates

Core operational requirement for Forge. Should be a first-class section in the Forge Interaction Modes artifact. Informs the Forge Guidance Engine design for back-prompting behavior.
