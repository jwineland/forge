---
id: github-pages-output-pipeline
name: GitHub Pages Output Pipeline
status: parked
citation: forge:2026-04-18-claude-general-docs:systematization:pages-discussion
created: 2026-04-18
park-trigger: When corpus-template-doc is created
park-reason: Depends on stable corpus template structure and intent registry — premature to design the delivery pipeline before those are settled
decay-policy: review-at-90-days
depends-on: [intent-registry-design, corpus-lifecycle-system]
related-to: [intent-as-semantic-contract]
---

## Summary

GitHub Pages serves as the content delivery surface for Forge-governed corpora. Marp HTML export produces self-contained slide decks. Pandoc with a minimal professional CSS theme converts MD to styled HTML documents. Content stays in Markdown in the repo; rendered output is served via Pages. Updates to source files trigger a rebuild.

## What needs to be designed

- GitHub Actions workflow for Marp HTML export on push to main
- Pandoc pipeline configuration and CSS theme selection
- Which content gets published vs. stays internal (intent-driven selection)
- Access control model (public vs. authenticated access)
- URL structure for published artifacts
- Version/snapshot publishing for locked compositions

## Prior context

This directly addresses the goal of moving away from Word/PPTX formats while providing a simple professional-looking way for stakeholders to review designated content. The BoundaryMark connection: published artifacts at known URLs with cryptographic provenance extends naturally from this.
