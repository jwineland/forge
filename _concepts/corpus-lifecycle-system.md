---
id: corpus-lifecycle-system
name: Corpus Lifecycle System
status: formalized
citation: forge:2026-04-18-claude-general-docs:corpus-architecture:lifecycle-design
created: 2026-04-18
depends-on: [manifest-as-coherence-anchor, three-layer-skill-architecture]
related-to: [semantic-graph-foundation, forge-concept-lifecycle, human-ai-role-separation]
promoted-into: [general_docs:MANIFEST.md]
---

## Summary

A governed document corpus has three distinct operational modes — Birth, Growth, and Maintenance — each requiring different tooling and process. A static template repo handles Birth but not Growth or Maintenance. The full system requires template repos, a living manifest, and operational tooling across all three modes.

## Detail

**Birth** — repo created from template, seeded from corpus-seed.yaml (fully or partially), gaps filled interactively or by AI inference.

**Growth** — content accumulates, structure emerges, manifest evolves. Sub-elements break into scoped sub-manifests. System detects what is present, missing, and drifted.

**Maintenance** — drift checks, challenge loop reviews, PR-gated changes, living document governance.

### Template repo structure

```
jwineland/corpus-skills          shared _skills/ library
jwineland/corpus-template-doc    document corpus template
jwineland/corpus-template-eng    engineering corpus template (full stack)
```

### corpus-seed.yaml hybrid instantiation

Three input modes:
- **Declared** — field present in YAML, used directly
- **Inferred** — field absent but discoverable from existing content; AI proposes, human confirms
- **Prompted** — field neither declared nor inferable; system asks with structured options

Fully blank YAML gets fully populated through inference and prompting. Fully populated YAML skips all prompting. Mixed cases work proportionally.

### Platform portability

Core system (corpus-seed.yaml, MANIFEST, _skills/, .claude/) is platform-agnostic. Automation layer varies by platform and is handled by adapter modules in `corpus-skills/adapters/`. GitHub Actions, GitLab CI/CD, and Gitea Actions are all target adapters.

## Open questions

- Sub-manifest split threshold (working heuristic: 5+ substantive files with internal authority dependencies)
- corpus-seed.yaml full schema design not yet complete
- Adapter module format and activation mechanism not yet designed
- GitHub template repo feature limitations (all-or-nothing instantiation) need workaround design

## Promotion candidates

Candidate for `corpus-template-doc` and `corpus-template-eng` when created. Core concept for Forge system design.
