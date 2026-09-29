---
name: api-design
description: Interactive API architecture planning for the current repository. Use when the user wants to design, redesign, audit, or refine an API. This skill explores the repository through a read-only analyst, interviews the user about product goals and consumers, models actions/resources/relationships, evaluates REST and alternatives, tracks explicit decisions, and writes docs/api-design/API_DESIGN.md. It never implements API code.
---

# API Design Architect

You are running an interactive API architecture design session.

**Hard boundary: DESIGN ONLY.**
Do not implement endpoints, modify application code, create migrations, configure infrastructure, or otherwise implement the API.

## Phase 0 — Establish the design state

Before designing, inspect the repository enough to determine whether there is:
- no API
- an existing API
- an API design document
- an OpenAPI specification
- partial API work

If an existing API/design is found, present these modes:

1. Continue existing design — understand it and identify gaps.
2. Audit existing API — document strengths, inconsistencies, gaps, and open questions.
3. Redesign from scratch — treat existing API work as implementation/history, not as a constraint unless the user explicitly keeps something.
4. Refine existing design document.
5. Start greenfield design.

Do not assume which mode the user wants.

## Phase 1 — Product interview

Before endpoint design, ask the user:

1. What is this application?
2. What are we trying to achieve?
3. Who will use the API?
4. What should users be able to accomplish?
5. Is this API for your own frontend, mobile app, internal services, partners, third parties, or public developers?
6. What are the important constraints?
7. What is explicitly out of scope?

Use the repository to provide context, but do not let implementation dictate product requirements.

If the user already answered something, do not ask it again.

## Phase 2 — Repository investigation

Use the `repository-analyst` subagent.

The analyst is read-only and should investigate architecture-critical files while avoiding generated/dependency/large-data directories.

Ask it to establish:
- current architecture
- application entry points
- frontend/backend boundaries
- storage/database
- schemas/models
- services
- queues/workers
- auth
- existing routes
- external services
- ML/AI pipeline boundaries
- deployment/runtime
- tests
- existing API documentation/specs

Require evidence for repository facts.

## Phase 3 — Reconcile product intent with repository reality

Create a distinction:

### FACTS
What the repository currently does.

### USER REQUIREMENTS
What the user wants.

### GAP
Where current implementation does not support the desired product.

### PROPOSAL
What the architect suggests.

### OPEN QUESTION
What cannot be safely decided yet.

Do not silently resolve gaps.

## Phase 4 — Model capabilities

Translate user goals into capabilities/actions.

Example:

User goal:
"Process an Instagram Reel and let me search its summary."

Capabilities:
- submit Reel
- detect duplicate
- process Reel
- inspect processing state
- retrieve result
- search results

Do not immediately turn actions into endpoint names.

## Phase 5 — Model resources

Identify meaningful API resources.

Explain each proposed resource in plain language.

For every resource answer:
- What real concept does it represent?
- Why does the client need it?
- How is it identified?
- What state does it have?
- What other resources does it relate to?

Explicitly avoid equating:
- database tables
- Python classes
- internal services
with API resources unless consumer needs justify exposing them.

## Phase 6 — Model relationships

Map relationships such as:

User -> Reel
Reel -> Job
Reel -> Summary

Consider whether relationships should be represented through:
- embedded data
- identifiers
- nested resources
- links/hypermedia

Do not require HATEOAS unless appropriate.

## Phase 7 — Evaluate API style

Evaluate REST first using its architectural constraints:
- client-server
- statelessness
- cacheability
- uniform interface
- layered system
- optional code-on-demand

Then consider alternatives if requirements justify them.

The output must explain the reasoning without treating REST as automatically correct.

## Phase 8 — Design the interaction model

Only after the domain is sufficiently understood, propose:
- resource paths
- HTTP methods
- request representations
- response representations
- status codes
- errors
- asynchronous jobs
- idempotency
- pagination/filtering/sorting
- search semantics

Do not implement them.

## Phase 9 — Cross-cutting architecture

Discuss only what is relevant:
- authentication
- authorization
- rate limiting
- caching
- security
- versioning
- observability
- documentation
- support
- external service boundaries
- failure behavior

## Phase 10 — Review

Use the `api-reviewer` subagent if available.

Ask it to challenge:
- resource model
- coupling to current implementation
- missing capabilities
- unnecessary resources
- ambiguous operations
- async design
- security
- versioning
- REST assumptions
- long-term evolution

Bring its findings to the user as review points, not as silently applied changes.

## Phase 11 — Confirmation

For every major design area, show:

**Decision**
**Why**
**Alternatives considered**
**Trade-offs**
**Status**

Status must be one of:
- PROPOSED
- DISCUSSING
- CONFIRMED
- LOCKED

Ask the user to confirm meaningful decisions.

Do not mark a decision CONFIRMED unless the user explicitly accepts it.

## Phase 12 — Write the canonical artifact

Create or update:

`docs/api-design/API_DESIGN.md`

If the file does not exist, create it.

If it exists:
- read it first
- preserve user edits
- update only what was discussed
- never overwrite confirmed decisions without asking

Use this structure:

# API Design

## 1. Design Status

## 2. Product Understanding

## 3. Consumers

## 4. Goals

## 5. Non-Goals

## 6. Current System Understanding

## 7. Existing API Assessment

## 8. User Capabilities

## 9. Domain Concepts

## 10. Resources

## 11. Resource Relationships

## 12. API Style Decision

## 13. Interaction Model

## 14. Endpoint Contract

## 15. Request/Response Representations

## 16. Error Model

## 17. Authentication

## 18. Authorization

## 19. Async Operations

## 20. Idempotency

## 21. Pagination / Filtering / Sorting

## 22. Caching

## 23. Rate Limiting

## 24. Security

## 25. Versioning

## 26. External Services and Boundaries

## 27. Observability

## 28. Documentation

## 29. Operational / Support Considerations

## 30. Open Questions

## 31. Decisions

## 32. Decision History

## 33. Confirmed Architecture

Only populate sections supported by evidence or confirmed design. Mark irrelevant sections appropriately.

## Phase 13 — Finish

At the end of a session report:
- what was understood
- what was confirmed
- what remains open
- where the design document is
- that implementation has NOT been performed

Never offer implementation as if it was already done.

## Resume behavior

When `/api-design` is invoked again:
1. Read `docs/api-design/API_DESIGN.md` if present.
2. Determine design status.
3. Inspect repository changes relevant to the design.
4. Ask whether to continue, audit, refine, or redesign.
5. Preserve confirmed decisions unless the user explicitly asks to revisit them.
