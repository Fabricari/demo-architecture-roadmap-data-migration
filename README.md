# Architecture Roadmaps – Demo Repository

## Overview

This repository demonstrates how architecture roadmaps can be used to communicate and guide technical strategy. It contains three sets of diagrams and accompanying documentation that illustrate architecture roadmaps at different levels of abstraction:

1. **Strategic Architecture Roadmap** — A four-state roadmap illustrating a modernization strategy for an e-commerce web application, from monolith through SaaS integration and microservices decomposition to AI-enabled semantic search.

2. **Tactical Architecture Roadmap** — A four-step roadmap illustrating the refactoring approach needed to execute the first strategic transition, showing how developers incrementally decouple Customer Management from SQL Server and migrate it to Salesforce CRM.

3. **On Architecture Roadmaps** — A conceptual discussion of architecture roadmaps themselves, contrasting non-branching (linear) roadmaps with branching roadmaps, informed by Gregor Hohpe's ideas on misleading vs. strategic roadmaps from *Platform Strategy*.

## Strategic Roadmap

The strategic roadmap models the evolution of an e-commerce platform through four architecture states:

- **Current State** — A 3-tier modular monolith backed by a single SQL Server database.
- **Transition 1** — Customer management is carved out behind a Salesforce CRM integration using required interfaces and adapters.
- **Transition 2** — Order and catalog capabilities are decomposed into domain-specific microservices with independent persistence.
- **Target State** — Catalog is extended with an AI-enabled semantic search pipeline using asynchronous indexing, embeddings generation, and an OpenSearch vector store.

Each state is represented as a whitebox UML component diagram. Color coding communicates change over time: green indicates newly introduced elements, orange indicates refactored elements, and white indicates elements unchanged from the prior state.

See [Documentation/Architecture-Roadmap-Presentation.md](Documentation/Architecture-Roadmap-Presentation.md).

## Tactical Roadmap

The tactical roadmap zooms into the first strategic transition and shows the step-by-step refactoring needed to migrate Customer Management from direct SQL Server access to Salesforce CRM. It demonstrates interface extraction, dependency inversion, and adapter patterns applied incrementally:

1. Direct coupling between CustomerManager and SqlServerCustomerRepository.
2. Extract `ICustomerRepository` interface and introduce an adapter within the same component.
3. Extract the adapter into a dedicated component.
4. Replace the adapter and client with Salesforce equivalents — CustomerManagement remains unchanged.

See [Documentation/Tactical-Roadmap-Presentation.md](Documentation/Tactical-Roadmap-Presentation.md).

## On Architecture Roadmaps

This document steps back from the specific e-commerce scenario to discuss architecture roadmaps as a concept. Using abstract diagrams, it contrasts two forms:

- **Non-branching roadmaps** — a fixed linear sequence of states. Simple and easy to follow, but potentially misleading when the future is uncertain.
- **Branching roadmaps** — multiple possible paths through a transformation, capturing decision points and alternative prioritization choices.

The discussion draws on Gregor Hohpe's *Platform Strategy*, connecting non-branching roadmaps to what he calls a "misleading roadmap" and branching roadmaps to his concept of a "strategic roadmap."

See [Documentation/On-Architecture-Roadmaps.md](Documentation/On-Architecture-Roadmaps.md).

## Repository Structure

```
Architecture/          draw.io source files for all diagrams
Documentation/         presentation markdown and supporting documentation
  Images/              exported diagram images (JPG)
Custom Draw-IO/        custom draw.io component (unrelated to roadmap content)
```
