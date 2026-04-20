# Forge

Forge is a framework for turning AI conversations into structured, lineage-preserving knowledge.

It exists to prevent the loss of useful data in human-AI discourse by providing a common method for asserting, classifying, refining, and mapping concepts, together with the artifacts that support and operationalize them over time.

## Purpose

Most AI conversations produce useful ideas, partial models, decisions, classifications, and artifacts that are easy to lose once a session ends. Forge is intended to make those outputs durable.

Rather than treating conversations as disposable transcripts, Forge treats them as source records. A forged conversation can yield canonical session structure, asserted concepts, supporting artifacts, semantic associations, qualification metadata, and traceable lineage back to the conversational context in which an idea emerged.

The long-term goal is simple: a user should be able to say **"forge this conversation"** and have its concepts and supporting artifacts captured, formalized, classified, and mapped into a reusable conceptual corpus.

## Concepts and Artifacts

Forge is concept-centered.

Concepts are the primary asserted units of meaning that the framework classifies, qualifies, links, and preserves. Artifacts are supporting materials such as code, documents, descriptive prose, specifications, models, or other work products that clarify, evidence, extend, or operationalize one or more concepts.

Artifacts are often critical to understanding a concept and may support many concepts at once. In some cases, related concepts and artifacts can accumulate into larger bodies of work such as projects or platforms.

## What Forge Does

Forge defines a reusable framework for:

- capturing conversations in canonical structure
- asserting concepts from discourse as durable knowledge units
- attaching and organizing artifacts that support, clarify, or operationalize those concepts
- classifying and associating concepts consistently
- iteratively qualifying incomplete or complex concepts through prompts, metadata, scoring, and modeling
- preserving lineage to the conversational "verse" where a concept arose
- formalizing and mapping concepts and their supporting artifacts into a durable semantic corpus
- promoting mature concept groupings into downstream project or platform contexts when appropriate

Forge is not just an archive for chats or notes. It is intended to provide a common operational method for converting discourse into reusable knowledge.

## Lifecycle and Transitions

Forge defines a concept lifecycle that begins with excavation and progresses through qualification, rationalization, formalization, and operationalization.

Concepts may also undergo working transitions such as promotion, parking, and reopening as they move through iterative refinement.

In this model, promotion is not the same as formalization. Promotion is the decision to elevate a concept into active refinement and possible formal declaration. Formalization is the act of expressing a concept in a more rigorous, canonical, and durable form. Parked concepts may later be reopened and promoted for further refinement or formalization.

## How It Is Intended to Work

At a high level, Forge treats a conversation as a source record rather than an endpoint.

A forged conversation should produce:

1. a canonical session record
2. extracted candidate concepts and supporting artifacts
3. assertions and classifications for those concepts
4. prompts for refinement where structure, metadata, or associations are incomplete
5. mapped outputs that can be retained here or promoted into other project repositories

In this model, concepts are not merely collected. They are asserted, classified, linked, refined, parked, promoted, formalized, and eventually operationalized over time.

## Current Status

Forge is an evolving framework and working repository, not yet a finished end-user product.

The repository currently defines the core model for:

- canonical session capture
- concept assertion and classification
- lifecycle handling and working transitions
- lineage and provenance
- semantic vocabulary
- staged refinement through repository structure

Some higher-level automation, browsing, and promotion workflows are still in progress. The framework is already usable as a structured operating model, while the long-term aim is to make its workflows increasingly reusable and automatable.

## Repository Structure

- `_intake/`  
  Raw or staged source material for future excavation.

- `_sessions/`  
  Canonical records of forged or excavated conversations.

- `_concepts/`  
  Formalized concepts extracted from sessions.

- `_parked/`  
  Concepts or artifacts worth retaining but not yet ready for formalization or promotion.

- `_skills/`  
  Reusable operational patterns, methods, or procedures.

- `_vocabulary/`  
  Shared semantic definitions and modeling context for the framework.

- `MANIFEST.md`  
  The primary operational and conceptual reference for the repository.

## Intended Usage Model

Forge is intended to become a common reusable framework through which AI discussions are routed and processed.

The target interaction is simple:

> forge this conversation

That invocation should eventually cause the conversation to be captured as a canonical record, analyzed for useful concepts and artifacts, checked for missing structure, refined through prompts where needed, and persisted as classified, lineage-preserving knowledge.

Today, much of that model is represented through repository structure, conventions, and guided workflows. Over time, the goal is to increase the degree of automation around concept extraction, classification, qualification, association, and promotion.

## Near-Term Direction

Forge is moving toward a more complete operational loop in which conversations can be forged into:

- canonical session records
- asserted concepts
- richer semantic associations
- qualification and scoring metadata
- reusable knowledge objects suitable for downstream project use

The framework is designed to support iterative refinement rather than one-pass capture. Its purpose is not only to preserve what was said, but to help complete, clarify, and organize what a conversation made possible.
