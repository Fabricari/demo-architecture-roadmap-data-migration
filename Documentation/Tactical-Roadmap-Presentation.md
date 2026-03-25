# Tactical Roadmap: Refactoring Customer Management from SQL Server to Salesforce

This roadmap illustrates the step-by-step refactoring approach for migrating Customer Management from direct SQL Server access to Salesforce CRM integration. It is intended for the development team to understand how to execute the transition incrementally using interface extraction, dependency inversion, and adapter patterns.

## How to Read Each Step
- Green elements = newly introduced
- Orange elements = refactored from the previous step
- White elements = unchanged from the previous step

## Full Tactical Roadmap View
![Full Tactical Roadmap](../Images/Tactical%20Roadmap.jpg)

---

## Step 1 - Current Implementation

### Diagram
![Step 1](../Images/Tactical%20Roadmap%20-%2001.jpg)

### Architecture State
The CustomerManagement component contains a CustomerManager class that directly depends on SqlServerCustomerRepository within the SqlServerClient component. SqlServerCustomerRepository communicates with the SQL Server E-Commerce Database. CustomerManager is tightly coupled to the repository implementation.

---

## Step 2 - Extract Interface and Introduce Adapter

### Diagram
![Step 2](../Images/Tactical%20Roadmap%20-%2002.jpg)

### Architecture Change
CustomerManager is refactored to depend on a new ICustomerRepository required interface instead of directly depending on SqlServerCustomerRepository. A new CustomerRepositoryToSqlServerCustomerRepositoryAdapter class is introduced that implements ICustomerRepository and delegates to SqlServerCustomerRepository. Both the interface and the adapter are introduced within the CustomerManagement component. The existing SqlServerClient component and SqlServerCustomerRepository remain unchanged.

#### Architecture Qualities
- Modifiability: CustomerManager no longer has a direct dependency on the SQL Server implementation.
- Testability: CustomerManager can be tested against ICustomerRepository without requiring a database.

---

## Step 3 - Extract Adapter into Dedicated Component

### Diagram
![Step 3](../Images/Tactical%20Roadmap%20-%2003.jpg)

### Architecture Change
The CustomerRepositoryToSqlServerCustomerRepositoryAdapter is extracted from the CustomerManagement component into a new CustomerMgmtToSqlServerClient Adapter component. CustomerManagement now contains only CustomerManager and ICustomerRepository. The adapter component sits between CustomerManagement and SqlServerClient, implementing the required interface and delegating to SqlServerCustomerRepository. SqlServerClient and the database remain unchanged.

#### Architecture Qualities
- Separation of concerns: the adapter is isolated from both the domain logic and the client implementation.
- Replaceability: the adapter component can be swapped without modifying CustomerManagement or SqlServerClient.

---

## Step 4 - Replace Adapter and Client with Salesforce

### Diagram
![Step 4](../Images/Tactical%20Roadmap%20-%2004.jpg)

### Architecture Change
The CustomerMgmtToSqlServerClient Adapter component is replaced with a new CustomerMgmtToSalesforceClient Adapter component containing a CustomerRepositoryToSalesforceCustomerClientAdapter. The SqlServerClient component is replaced with a new SalesforceClient component containing a SalesforceCustomerClient. The SalesforceClient communicates with Salesforce (CRM) instead of the SQL Server E-Commerce Database. CustomerManagement remains unchanged — CustomerManager still depends on ICustomerRepository with no awareness of the underlying implementation.

#### Architecture Qualities
- Interoperability: customer data is now managed through Salesforce CRM.
- Stability: CustomerManagement is unaffected by the infrastructure swap.
- Evolvability: the same pattern can be reused to swap any future data source behind ICustomerRepository.
