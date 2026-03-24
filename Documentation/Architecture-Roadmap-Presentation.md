# E-Commerce Modernization Roadmap

## How to Read Each Step
- Green elements = newly introduced capabilities
- Orange elements = refactored capabilities
- White elements = unchanged from the previous state

## Full Roadmap View
![Full Roadmap](../Images/Architecture%20Roadmap%20-%20Technical%20Strategy.jpg)

---

## Current State: 3-Tier, Modular-Monolith

### Diagram
![State 1 - Current Diagram](../Images/Architecture%20Roadmap%20-%2001%20Current.jpg)

### Architecture Overview
Each actor/persona accesses the system through a bespoke user-experience with shared backend capabilities. The backend has been developed as a modular monolith with sub-domains isolated at the component level, but releasable as a single deployment. State for all of the system's entities is maintained within the single, normalized relational database.

#### Architecture Qualities
- Consistency: all domain data shares a single transactional boundary.
- Simplicity: one deployable unit and one relational database to operate.
- Cohesion: sub-domains are logically separated at the component level.

---

## Transition State 1: Salesforce Integration (Customer Mgmt)

### Why This Step
Centralize all customer management in an organizational CRM so the business can leverage Salesforce's customer lifecycle capabilities instead of self-managing customer data in SQL.

### Diagram
![State 2 - Transition 1 Diagram](../Images/Architecture%20Roadmap%20-%2002%20CRM.jpg)

### Architecture Change
Subsequent changes should not affect the clients with code changes or re-deployment. The Customer Management module is refactored to have loose coupling with dependencies using required interfaces and adapters to consume a new Salesforce Client. The Salesforce Client module is introduced to handle all communication with the new Salesforce dependency. The system is integrated with Salesforce to centralize all customer management in an organizational CRM.

#### Architecture Qualities
- Interoperability: customer data is managed through an industry-standard CRM platform.
- Modifiability: required interfaces and adapters decouple Customer Management from its data source.
- Deployability: client applications remain unaffected by backend integration changes.

---

## Transition State 2: Microservices Decomposition (Orders & Catalog)

### Why This Step
Decompose order and catalog responsibilities into domain-specific microservices so each domain can own its state independently and the web service stays focused on user-experience and use-case-specific logic.

### Diagram
![State 3 - Transition 2 Diagram](../Images/Architecture%20Roadmap%20-%2003%20Microservices.jpg)

### Architecture Change
Order Processing and Catalog Management modules are refactored to have loose coupling with dependencies using required interfaces and adapters to consume domain-specific microservices. Service Client modules are introduced to handle all communication with the new domain-specific microservices. Microservices are introduced to handle centralized management of domain-specific state, enabling subsequent reuse of domain-specific responsibilities and keeping the web service focused on user-experience and use-case-specific logic.

#### Architecture Qualities
- Scalability: each microservice scales independently based on domain workload.
- Deployability: domain services release independently from the web application.
- Reusability: domain-specific responsibilities are exposed for reuse beyond the web service.
- Data autonomy: each service owns its persistence with a store matched to its access patterns.

---

## Target State: Modernized, AI-Enabled Semantic-Search for Catalog

### Why This Step
Introduce a new user-facing capability to search the catalog with descriptive text, improving product discovery through semantic-search experiences.

### Diagram
![State 4 - Target Diagram](../Images/Architecture%20Roadmap%20-%2004%20AI%20Search.jpg)

### Architecture Change
Catalog Management capabilities are extended to retrieve products within the catalog through semantic-search queries, orchestrating calls with a new Product Semantic Search Service. A Service Client module is introduced to handle communication with the new Product Semantic Search Service. The Product Semantic Search Service is introduced to handle responsibilities of semantic-search against an AI-engineered solution. The service provides encapsulation of a solution that is likely to be fine-tuned over time.

#### Architecture Qualities
- Extensibility: AI-driven search is added without modifying existing transactional catalog operations.
- Evolvability: the semantic-search solution is encapsulated behind a service boundary, allowing it to be fine-tuned independently.
- Resilience: asynchronous indexing decouples the search path from the catalog write path.


