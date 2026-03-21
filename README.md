# Demo Architecture Roadmap – Data Migration

## Overview

This repository supports a demonstration of how architecture roadmaps can be used to communicate and guide technical strategy aligned with business objectives. The focus is on expressing system evolution over time in a way that makes complex transformation efforts understandable and actionable.

## Scenario

The demonstration models a migration from a tightly coupled, highly normalized legacy data system running on-premises to a cloud-based architecture that evolves through pragmatic transition states.

The roadmap shows incremental modernization rather than wholesale replacement. It begins with a shared-database web application, introduces SaaS integration for customer management, then decomposes business capabilities into service-aligned components with independent data ownership. Transitional approaches include in-process client modules, extracted services, and asynchronous integration patterns that preserve continuity for existing consumers while reducing coupling over time.

## Roadmap Model

Architecture roadmaps in this repository are expressed as a sequence of states:

* **Current State** — existing system structure and constraints
* **Transition States (1..n)** — incremental steps that reshape architecture, integration boundaries, and data ownership
* **Target State** — a service-aligned, cloud-oriented architecture with AI-enabled search capabilities

Each state is represented using diagram types appropriate to the concern being communicated, such as system context, service boundaries, data models, or deployment topology.

## Roadmap Sequence

The roadmap currently illustrates a progression like this:

* **State 1** — A web application with shared access to a centralized SQL Server database
* **State 2** — Customer management is carved out behind a Salesforce integration while the remaining capabilities continue to use the legacy data platform
* **State 3** — Order and catalog capabilities are extracted behind service clients and implemented as separate microservices with service-specific repositories
* **State 4 (Target)** — Catalog data also drives an asynchronous semantic search pipeline using queue-based indexing, embeddings generation, and an OpenSearch vector index to support AI-oriented retrieval scenarios

This progression is intended to demonstrate realistic architectural evolution under delivery and continuity constraints, not a single-step rewrite.

## Artifacts

The repository contains architecture artifacts that capture different perspectives of the roadmap, including:

* Diagrams representing each state in the roadmap
* Variations that reflect different assumptions or migration paths
* Supporting documentation that provides context for decisions, tradeoffs, and transitions
* Presentation-oriented views that use color coding and legends to improve readability across roadmap states

Artifacts are versioned to reflect how the roadmap evolves over time.

## Target Considerations

The target state is not only service-aligned and cloud-based, but also designed to demonstrate plausible downstream AI engineering use cases.

In particular, the catalog domain is extended with a semantic search path in which catalog changes flow through an asynchronous indexing process, embeddings are generated through a managed model service, and vectors are stored in OpenSearch for retrieval. This provides a concrete example of how service-aligned data and event-driven projections can enable retrieval-augmented generation (RAG), semantic product discovery, and other context-driven AI workflows without tightly coupling AI concerns to transactional services.

## Purpose

This repository is intended as a portfolio-oriented demonstration of architectural thinking. It emphasizes staged modernization, bounded-context-aware decomposition, polyglot persistence, external platform integration, event-driven processing, and selective introduction of AI capabilities within a coherent roadmap.
