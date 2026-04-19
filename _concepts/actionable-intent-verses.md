---
id: actionable-intent-verses
name: Actionable Intent Verses (Narrative/Intent Split)
status: formalized
citation: forge:2026-04-19-gemini-citation-modality:actionable-intent:exchange-18
created: 2026-04-19
depends-on: [object-oriented-documentation, intent-as-semantic-contract]
related-to: [bom-binding-locked-composition, corpus-lifecycle-system]
promoted-into: []
---

## Summary

A verse (content module) has two distinct views: a Narrative View for human consumption and an Intent View for machine execution. The two views are always kept together in the same source artifact but serve different consumers. Template placeholders in the Intent View are rendered by an orchestration system using inventory-supplied arguments at execution time.

## Detail

### The two views

**Narrative View** — human-readable prose describing what the test or procedure is, why it matters, and what a passing result looks like. This is the public interface of the object in OOD terms.

**Intent View** — a YAML or JSON payload describing the machine-executable action, with template placeholders for platform-specific arguments. This is the implementation in OOD terms.

### Example structure

```yaml
# Verse ID: urn:srv_val:net:gemini:opt_eth:v04
# Title: Maximize NIC Ring Buffers

narrative: |
  To prevent packet drops at 100Gbps line rate, the NIC ring buffers
  must be set to their maximum hardware-supported values.

intent:
  action: "network_config.ethtool"
  parameters:
    interface: "{{ target_interface }}"
    rx_ring: "{{ nic_max_rx | default(4096) }}"
    tx_ring: "{{ nic_max_tx | default(4096) }}"
```

### Template rendering

The orchestration runner holds platform-specific inventory (e.g., `target_interface: eth0` for one system, `target_interface: ens3f0` for another). The runner fetches the verse by URN, passes inventory variables into the intent block, and renders the final command. One canonical verse executes correctly on any target platform.

### Relationship to intent-as-semantic-contract

The two concepts are complementary and address intent at different layers:

| Layer | Concept | Concern |
|---|---|---|
| Audience/purpose layer | Intent as semantic contract | What this output is *for* and *who it serves* |
| Execution layer | Actionable intent verses | How this content is *executed* by a machine |

Neither subsumes the other. A content module can have both an audience intent (executive-presentation) and an execution intent (the YAML payload that generates the slide deck). Both need to be encoded.

### Producing human-readable output

Because narrative and intent are co-located in source but rendered separately, a compiler/filter script can:
- Extract only narrative fields → clean test plan PDF for stakeholders
- Extract only intent fields → executable manifest for orchestration
- Combine both → annotated technical reference with inline commands

This eliminates double maintenance — there is one source, two renderings.

### Relationship to BOM-binding

When a composition is locked to a BOM, both the narrative and intent views are locked together. The locked composition captures the exact rendered intent — the specific commands that were actually executed on that build — not just the template.

## Open questions

- How intent views are versioned when template schema changes (parameter renamed, new required field)
- Whether intent views should be validated against a schema at commit time
- How orchestration systems authenticate against the Git repo to fetch verses by URN at runtime

## Promotion candidates

High-value candidate for the manufacturing corpus template when created. Also relevant to the GitHub Pages output pipeline — the narrative view is what gets published; the intent view drives the build action.
