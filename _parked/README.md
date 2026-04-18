# Parked Concepts

This directory contains concepts that have been intentionally deferred. Every parked concept must have a trigger condition specifying when it should be revisited.

## Required front matter

```yaml
---
id: concept-id
name: Concept name
status: parked
citation: forge:SESSION_ID:THREAD_ID:EXCHANGE_N
created: YYYY-MM-DD
park-trigger: "Condition that would cause this to be revisited"
park-reason: "Why this is being deferred now"
decay-policy: "What happens if trigger never fires"
depends-on: []
related-to: []
---
```

## Decay policies

- `review-at-90-days` — surface for review 90 days after parking date
- `promote-if-referenced` — promote if cited in 3 or more future sessions
- `archive-if-no-references` — archive if no references after 180 days
- `manual-only` — only revisited by explicit human action

## Activation

When a trigger condition fires, move the concept from `_parked/` to `_concepts/`, update status to `classified` or `formalized` as appropriate, and record the activation in DECISIONS.md.
