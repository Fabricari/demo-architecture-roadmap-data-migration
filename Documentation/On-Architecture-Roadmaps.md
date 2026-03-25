# On Architecture Roadmaps

Architecture roadmaps express how a system evolves over time. Each state in a roadmap represents the architecture at a meaningful point in the transformation. Taken together, the states tell the story of where the system is today, how it changes, and where it is headed.

The states in a roadmap can be illustrated using whatever architectural view best communicates the strategy — whitebox component diagrams, C4 diagrams, deployment diagrams, or any other notation that makes the evolution accessible to the intended audience. What matters is that the reader can see how the architecture changes from one state to the next, not the visual format used to depict it.

The diagrams in this document use abstract shapes to represent architectural elements without labeling specific technologies. Each shape corresponds to a type of concern:

- Green square — web application (backend)
- Blue cylinder — relational database
- Orange rectangle — external platform (CRM)
- Purple hexagon — microservice
- Red sideways cylinder — message queue / event-driven pipeline

---

## Non-Branching Roadmap

![Non-Branching Roadmap](Images/Non-Branching%20Roadmap.jpg)

A non-branching roadmap presents a single linear path from current state to target state. Each transition leads to exactly one next state, and the sequence is fixed.

This is the simplest form of a roadmap. It communicates a clear plan and is easy to follow. It works well when the sequence of changes is well understood and unlikely to shift.

However, Gregor Hohpe warns in *Platform Strategy* that this simplicity can be deceptive. He calls this a **misleading roadmap**:

> "Strategies should be concrete and actionable, but that doesn't mean that they can define a simple linear path — that's simply not what the world looks like. Pretending a linear sequence of predictable steps is the classic fallacy of a misleading roadmap."

A linear roadmap implies that every step is predetermined and that no decisions remain. In practice, priorities shift, constraints change, and new information emerges between states.

---

## Branching Roadmap

![Branching Roadmaps](Images/Branching%20Roadmaps.jpg)

A branching roadmap acknowledges that there are multiple possible paths through a transformation. At each decision point, the roadmap branches into alternative next states that reflect different prioritization choices — which capability to modernize next, which integration to introduce first, or which constraint to address sooner.

Not every step needs to be predetermined. Early transitions may be committed while later ones remain open, reflecting the reality that decisions further out depend on what we learn along the way.

Hohpe calls this a **strategic roadmap**:

> "Seeing the future as uncertain forms an honest roadmap and is a big step ahead. But giving in to uncertainty doesn't make for a very meaningful strategy and runs the risk of 'we'll figure it out as we go along.' A strategic roadmap therefore anticipates decision points, possible paths to be taken, and the data needed to make those decisions."

A branching roadmap is not an admission that we lack a plan. It is an acknowledgment that the plan must adapt to what we learn along the way. The roadmap captures:

- The decision points where priorities could diverge
- The alternative paths that each prioritization would take
- The criteria that would inform which branch to follow

This makes the roadmap a tool for strategic reasoning, not just a timeline of deliverables.
