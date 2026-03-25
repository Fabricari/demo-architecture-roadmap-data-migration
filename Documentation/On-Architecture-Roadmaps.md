# On Architecture Roadmaps

Architecture roadmaps express how a system evolves over time. Each state in a roadmap represents the architecture at a point in the transformation, and the connections between states represent transitions — the work required to move from one state to the next.

The diagrams in this document use abstract shapes to represent architectural elements without labeling specific technologies. Each shape corresponds to a type of concern:

- Green square — web application (backend)
- Blue cylinder — relational database
- Orange rectangle — external platform (CRM)
- Purple hexagon — microservice
- Red sideways cylinder — message queue / event-driven pipeline

Each state is enclosed in a circle. Lines between circles represent transitions.

---

## Non-Branching Roadmap

![Non-Branching Roadmap](Images/Non-Branching%20Roadmap.jpg)

A non-branching roadmap presents a single linear path from current state to target state. Each transition leads to exactly one next state, and the sequence is fixed.

This is the simplest form of a roadmap. It communicates a clear plan and is easy to follow. It works well when the sequence of changes is well understood and unlikely to shift.

However, it can also be misleading. A linear roadmap implies that every step is predetermined and that no decisions remain. In practice, priorities shift, constraints change, and new information emerges between states.

---

## Branching Roadmap

![Branching Roadmaps](Images/Branching%20Roadmaps.jpg)

A branching roadmap presents the same current state and target state, but acknowledges that there are multiple possible paths between them. At each decision point, the roadmap branches into alternative next states that reflect different prioritization choices.

In this diagram, the first transition from the current state is committed (solid lines). Subsequent transitions branch (dashed lines) to indicate that the path forward depends on decisions that have not yet been made. Different branches represent different sequencing priorities — which capability to modernize next, which integration to introduce first, or which constraint to address sooner.

All branches in this example converge on the same target state. The destination is shared, but the order in which we get there is not fixed.

---

## Why Branching Matters

Gregor Hohpe writes in *Platform Strategy*:

> "Strategies should be concrete and actionable, but that doesn't mean that they can define a simple linear path — that's simply not what the world looks like. Pretending a linear sequence of predictable steps is the classic fallacy of a misleading roadmap."

He continues:

> "Seeing the future as uncertain forms an honest roadmap and is a big step ahead. But giving in to uncertainty doesn't make for a very meaningful strategy and runs the risk of 'we'll figure it out as we go along.' A strategic roadmap therefore anticipates decision points, possible paths to be taken, and the data needed to make those decisions."

A branching roadmap is not an admission that we lack a plan. It is an acknowledgment that the plan must adapt to what we learn along the way. The roadmap captures:

- The decision points where priorities could diverge
- The alternative paths that each prioritization would take
- The shared target state that all paths are working toward
- The criteria that would inform which branch to follow

This makes the roadmap a tool for strategic reasoning, not just a timeline of deliverables.
