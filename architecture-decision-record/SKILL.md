

---
name: architecture-decision-record
description: A skill for creating and managing Architecture Decision Records (ADRs) to document significant architectural choices.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Architecture Decision Record (ADR)

## Overview

This skill empowers Manus to understand, create, and manage Architecture Decision Records (ADRs). An ADR is a document that captures an important architectural decision made along with its context and consequences. The goal is to create a clear and lasting record of the key architectural choices that have shaped the system. By using this skill, you can ensure that the rationale behind significant design decisions is not lost over time, facilitating better communication, onboarding of new team members, and more consistent architectural evolution.

ADRs are particularly valuable in agile and evolving projects where design decisions are made incrementally. They provide a lightweight yet powerful way to document the "why" behind the "what," preventing the need for future architectural archaeology. This skill provides the structure, templates, and workflow to seamlessly integrate ADRs into your development process.

By leveraging this skill, teams can cultivate a culture of thoughtful architectural practice. It encourages deliberate decision-making and provides a mechanism for knowledge sharing that scales with the team and the complexity of the system. The result is a more robust, maintainable, and understandable architecture that can evolve gracefully over time.

_content_
## When to Use This Skill

This skill is most effective in the following scenarios:

*   **Making Significant Technology Choices:** When you need to decide on a new database, programming language, framework, or any other significant piece of technology.
*   **Defining Architectural Patterns:** When establishing a new pattern for the system, such as microservices, event-driven architecture, or a specific layering strategy.
*   **Changing Core Component Interfaces:** When a proposed change to a fundamental API or component interface will have a widespread impact.
*   **Addressing Critical Non-Functional Requirements:** When making a decision to meet a specific performance, security, scalability, or availability requirement.
*   **Adopting a New Standard or Protocol:** When introducing a new standard for communication, data format, or integration.
*   **Deprecating an Existing Solution:** When a decision is made to retire a legacy component or service, and the reasoning needs to be documented.
*   **Onboarding New Team Members:** To provide new developers with a clear history of the architectural evolution of the project.
*   **Resolving Architectural Debates:** To formally document the outcome of a debate and the reasons for the chosen path, even if there was no complete consensus.

## Core Capabilities

This skill provides a comprehensive toolkit for working with Architecture Decision Records.

### 1. ADR Creation

The skill can generate a new, pre-populated ADR file based on a standardized template. This ensures consistency across all records and guides the user to provide all necessary information.

**Example Interaction:**

```
User: Create a new ADR for 'Adopt PostgreSQL as the primary database'.
Manus: (Creates a new file named '0001-adopt-postgresql-as-the-primary-database.md' with the standard template)
```

### 2. ADR Template

The skill uses a default Markdown template for all new ADRs. This template is based on the format proposed by Michael Nygard, one of the early proponents of ADRs.

**Default Template:**

```markdown
# 1. Title of the decision

*   **Status:** [Proposed | Accepted | Deprecated | Superseded]
*   **Date:** [YYYY-MM-DD]

## Context

[Describe the context and problem that this decision addresses. This section should include the forces at play, including technological, political, social, and project local. It should also describe the problem that the decision is trying to solve.]

## Decision

[Describe our decision. This section should be a clear and concise statement of the decision that was made.]

## Consequences

[Describe the results of this decision. All consequences should be listed here, not just the positive ones. This includes any trade-offs that were made, any risks that were accepted, and any follow-up work that is now required.]
```

### 3. ADR Management

The skill can help you manage the lifecycle of your ADRs.

*   **List ADRs:** View a list of all existing ADRs, along with their status.
*   **View an ADR:** Display the content of a specific ADR.
*   **Update an ADR's Status:** Change the status of an ADR (e.g., from 'Proposed' to 'Accepted').

### 4. Knowledge Synthesis

The skill can analyze and synthesize information from multiple ADRs to provide a high-level overview of the system's architecture. For example, you can ask for a summary of all technology choices or a timeline of key architectural decisions.

**Example Interaction:**

```
User: Summarize the technology stack based on our ADRs.
Manus: (Analyzes all accepted ADRs and extracts the technologies mentioned in the 'Decision' section)

Based on the existing ADRs, here is a summary of the current technology stack:

*   **Database:** PostgreSQL (from ADR-0001)
*   **Inter-service Communication:** gRPC (from ADR-0002)
*   **Asynchronous Messaging:** RabbitMQ (from ADR-0003)
```

### 5. ADR Validation

The skill can perform validation checks on ADR files to ensure they conform to the expected format and contain all the necessary sections. This helps maintain the quality and consistency of the documentation.

**Example Interaction:**

```
User: Validate the ADR file '0004-use-react-for-frontend.md'.
Manus: (Checks the file for the required sections: Status, Date, Context, Decision, Consequences)

The ADR file '0004-use-react-for-frontend.md' is missing the 'Consequences' section. Please add it to complete the record.
```

## Step-by-Step Workflow

Here is a typical workflow for using this skill to create and manage ADRs:

1.  **Identify the Need for a Decision:** The process begins when a significant architectural decision needs to be made. This could be triggered by a new feature, a performance issue, or a desire to improve the existing architecture.

2.  **Initiate the ADR Process:** Use the skill to create a new ADR. Provide a descriptive title that summarizes the proposed decision.

    *   **Action:** `manus: adr new "Use gRPC for inter-service communication"`
    *   **Result:** Manus creates a new file, such as `0002-use-grpc-for-inter-service-communication.md`, with the status set to "Proposed".

3.  **Flesh out the Context:** Edit the newly created ADR file to provide detailed context. Describe the problem, the constraints, and the alternatives that were considered. This is a critical step for ensuring the decision is well-understood in the future.

    *   **Action:** Open the generated Markdown file and fill in the "Context" section.

4.  **Discuss and Debate:** Share the proposed ADR with the team. This can be done through a pull request, a team meeting, or any other collaborative forum. The goal is to gather feedback, identify potential issues, and build consensus.

5.  **Make the Decision:** Based on the discussion, make a final decision. This might be to accept the proposal, reject it, or choose an alternative.

6.  **Document the Decision and Consequences:** Update the ADR to reflect the final decision. Clearly state what was decided in the "Decision" section. In the "Consequences" section, document the expected outcomes, both positive and negative. This includes any new risks, trade-offs, or required follow-up work.

7.  **Update the Status:** Change the status of the ADR to "Accepted". If the proposal was rejected, you can either delete the ADR or move it to a "Rejected" or "Deprecated" status.

    *   **Action:** `manus: adr update-status 0002 Accepted`

8.  **Implement the Decision:** With the decision formally documented, the team can now proceed with implementation.

9.  **Revisit and Revise:** ADRs are not set in stone. If a past decision is no longer valid, create a new ADR to supersede it. The new ADR should reference the old one and explain why the decision is being changed. This creates a clear audit trail of architectural evolution.

## Best Practices

To get the most out of using Architecture Decision Records, follow these best practices:

*   **Keep it Lightweight:** The goal of ADRs is not to create a heavy, bureaucratic process. The process should be as simple and unobtrusive as possible. The focus is on the value of the documentation, not the ceremony of creating it.
*   **One Decision per ADR:** Each ADR should focus on a single, atomic decision. If you have multiple related decisions, create a separate ADR for each one and link them together.
*   **Write for the Future:** When writing an ADR, imagine you are writing it for a new team member who will join the project two years from now. Provide enough context and rationale for them to understand the decision without needing to ask anyone.
*   **Store ADRs with the Code:** ADRs should be stored in the same version control repository as the code they relate to. This makes them easy to find, and it ensures that the architectural documentation evolves along with the codebase. A common practice is to store them in a `doc/adr` or `docs/architecture/decisions` directory.
*   **Use a Clear Naming Convention:** Adopt a consistent naming convention for your ADR files. A simple and effective approach is to use a sequential number followed by a short, descriptive title (e.g., `0001-adopt-postgresql.md`).
*   **Automate Where Possible:** Use scripts or tools to automate the creation and management of ADRs. This can help to enforce consistency and reduce the friction of the process.
*   **Socialize the Process:** Make sure the entire team understands the purpose and value of ADRs. Encourage everyone to participate in the process, not just the senior architects.
*   **Don't Retrofit Everything:** While it can be tempting to go back and document all past decisions, it's often not a good use of time. Start by documenting new decisions as they are made. You can selectively document past decisions if they are particularly important or poorly understood.
*   **Use Plain Language:** Write ADRs in a clear and concise way that is easy for everyone to understand, regardless of their technical expertise. Avoid jargon where possible, or explain it if it's necessary.
*   **Focus on the Why, Not Just the What:** The most important part of an ADR is the "Context" section. It should clearly explain the problem and the reasons for the decision. The "what" is important, but the "why" is essential for long-term understanding.
*   **Embrace Asynchronicity:** The ADR process doesn't have to be synchronous. A pull request-based workflow is a great way to allow for asynchronous discussion and feedback from the entire team.
*   **Link to Other Documents:** If your decision is influenced by other documents, such as a business requirements document or a technical whitepaper, link to them from the ADR. This provides additional context for future readers.

## Examples

Here are a few examples of how this skill can be used in practice.

### Example 1: Creating a New ADR

**User Request:**

> "Manus, we need to decide on a message broker. Create an ADR for using RabbitMQ."

**Manus Action:**

1.  Creates a new file: `doc/adr/0003-use-rabbitmq-for-asynchronous-messaging.md`
2.  Populates the file with the standard ADR template.

**Generated ADR:**

```markdown
# 3. Use RabbitMQ for Asynchronous Messaging

*   **Status:** Proposed
*   **Date:** 2026-02-02

## Context

We have a growing need for asynchronous communication between our services. For example, when a new user signs up, we need to send them a welcome email, provision their account, and notify the analytics service. Currently, these actions are performed synchronously, which leads to long response times and tight coupling between services. We need a reliable and scalable message broker to decouple our services and improve performance.

We considered the following options:

*   **RabbitMQ:** A mature, feature-rich message broker with broad community support and client libraries for all our languages.
*   **Apache Kafka:** A high-throughput, distributed streaming platform. It is more complex to set up and manage than RabbitMQ, but it offers superior performance for high-volume streaming data.
*   **AWS SQS:** A fully managed message queuing service. It is easy to use and integrates well with other AWS services, but it offers less flexibility than a self-hosted solution.

## Decision

We will use RabbitMQ as our primary message broker for asynchronous communication between services. We will start with a single, non-clustered instance for development and staging environments, and a three-node cluster for production.

## Consequences

*   **Positive:**
    *   Services will be more loosely coupled, improving resilience and maintainability.
    *   User-facing response times will be reduced for operations that can be performed asynchronously.
    *   We will have a flexible and scalable platform for future event-driven features.
*   **Negative:**
    *   We will need to take on the operational overhead of managing a RabbitMQ cluster.
    *   Developers will need to be trained on how to use RabbitMQ and the principles of message-based communication.
*   **Risks:**
    *   If not configured correctly, RabbitMQ can become a single point of failure.
    *   Message loss is possible in certain failure scenarios if not properly handled.
*   **Follow-up:**
    *   Create a set of best practice guidelines for using RabbitMQ.
    *   Develop a standard library for our services to interact with RabbitMQ.
    *   Set up monitoring and alerting for the RabbitMQ cluster.

```

### Example 2: Listing Existing ADRs

**User Request:**

> "Manus, show me all the architectural decisions we have made."

**Manus Action:**

1.  Scans the `doc/adr` directory for Markdown files.
2.  Parses the title and status from each file.
3.  Presents a summary to the user.

**Manus Response:**

> Here are the current Architecture Decision Records:
>
> *   **0001: Adopt PostgreSQL as the primary database** (Accepted)
> *   **0002: Use gRPC for inter-service communication** (Accepted)
> *   **0003: Use RabbitMQ for asynchronous messaging** (Proposed)

### Example 3: Superseding an ADR

**User Request:**

> "Manus, our needs have changed, and gRPC is no longer the best fit for inter-service communication. Create a new ADR to supersede ADR-0002 and adopt REST APIs with OpenAPI."

**Manus Action:**

1.  Creates a new file: `doc/adr/0005-use-rest-apis-with-openapi.md`
2.  Populates the file with the standard ADR template, noting that it supersedes a previous ADR.
3.  Updates the status of the old ADR.

**Generated ADR:**

```markdown
# 5. Use REST APIs with OpenAPI for Inter-Service Communication

*   **Status:** Proposed
*   **Date:** 2026-08-15
*   **Supersedes:** [ADR-0002: Use gRPC for inter-service communication](0002-use-grpc-for-inter-service-communication.md)

## Context

Our initial decision to use gRPC (documented in ADR-0002) was based on the need for high performance and a strongly-typed contract between services. However, our team has grown, and we now have a more diverse set of client applications, including a web-based administrative UI and several third-party integrations. gRPC's reliance on HTTP/2 and Protobuf makes it challenging to use directly from a browser and requires more specialized tooling for external partners.

We need a communication protocol that is more universally accessible and easier to debug with standard tools. The performance benefits of gRPC are no longer as critical as the need for broad compatibility and ease of use.

## Decision

We will adopt RESTful APIs with OpenAPI v3 for all inter-service communication. All new services will expose a REST API, and existing gRPC-based services will be migrated over time. We will use the OpenAPI specification to define our API contracts, and we will use tools like Swagger UI to provide interactive documentation.

## Consequences

*   **Positive:**
    *   Our APIs will be easily consumable by a wide range of clients, including web browsers and third-party applications.
    *   The learning curve for new developers will be lower, as REST and JSON are more familiar than gRPC and Protobuf.
    *   We can leverage a mature ecosystem of tools for API design, documentation, and testing.
*   **Negative:**
    *   We will likely see a decrease in performance compared to gRPC.
    *   We will lose the benefits of a strongly-typed, contract-first workflow that gRPC enforces.
*   **Follow-up:**
    *   Update ADR-0002 to a status of "Superseded".
    *   Develop a migration plan for existing gRPC services.
    *   Establish a new set of standards and best practices for designing REST APIs.

```

## References

*   [Documenting Architecture Decisions - Michael Nygard](http://thinkrelevance.com/blog/2011/11/15/documenting-architecture-decisions)
*   [Architecture Decision Record (ADR) - GitHub Repository by Joel Parker Henderson](https://github.com/joelparkerhenderson/architecture-decision-record)
*   [ADR GitHub Organization](https://adr.github.io/)
*   [Markdown Architectural Decision Records (MADR)](https://adr.github.io/madr/)
*   [Cognitect's ADRs](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions)
*   [ADR Tools - A CLI tool for working with ADRs](https://github.com/npryce/adr-tools)
*   [Sustainable Architectural Design Decisions](https://www.infoq.com/articles/sustainable-architectural-design-decisions/)
*   [When and How to Write an Architecture Decision Record](https://engineering.atspotify.com/2020/04/14/when-and-how-to-write-an-architecture-decision-record/)
*   [Architecture Decision Records in Action](https://www.youtube.com/watch?v=Wjja_n_0_iE)
*   [Lightweight Architecture Decision Records](https://www.thoughtworks.com/radar/techniques/lightweight-architecture-decision-records)
*   [A Practical Guide to Writing ADRs](https://www.freecodecamp.org/news/a-practical-guide-to-writing-adrs/)
*   [ADRs: A Lightweight and Effective Way to Document Architectural Decisions](https://www.youtube.com/watch?v=7Gqn2dbt_JY)
*   [How to Use ADRs to Make Your Architecture More Understandable](https://itnext.io/how-to-use-adrs-to-make-your-architecture-more-understandable-e0e6b54499f3)
*   [The Power of Architecture Decision Records (ADRs)](https://www.youtube.com/watch?v=h93f2fna2tM)
*   [ADR: The Best Way to Document Your Architecture Decisions](https://www.youtube.com/watch?v=Y-d2z_j3i5A)
_content_
