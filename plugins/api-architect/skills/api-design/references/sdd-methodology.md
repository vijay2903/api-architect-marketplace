# Spec-Driven API Design Methodology

## Core cycle

1. Establish product and consumer requirements.
2. Investigate repository reality.
3. Model capabilities and domain concepts.
4. Model resources and boundaries.
5. Decide API style and interaction semantics.
6. Draft the specification.
7. Select relevant stakeholder reviewers.
8. Simulate concrete consumer scenarios.
9. Revise the specification.
10. Re-review/re-simulate affected areas.
11. Validate the six SDD constraints.
12. Obtain explicit user confirmation of major decisions.
13. Mark the specification validated.
14. Enter the machine-readable contract stage when appropriate.

A design problem discovered after validation returns to the design cycle. Do not silently fix it only in implementation.

## Decoupled resource architecture

When a resource-oriented API is selected, resource design is part of the specification rather than a naming exercise.

The API Architect must establish that each public resource is a stable consumer-facing concept decoupled from the actions performed on it and from backend implementation structure.

Review:
- noun-based resource naming for ordinary resources;
- collection/item structure where multiplicity is possible;
- justified singleton resources;
- action/protocol exceptions with explicit rationale;
- independence from database tables, classes, controllers, services, queues, vendors, and internal pipeline stages;
- representation independence;
- content handler/view renderer separation when multiple representations are required;
- caching implications of the resource/representation contract.

Run `resource-design-reviewer` when these concerns are material.

## Six constraints

### Standardized
Use a coherent, reusable specification structure and an appropriate machine-readable contract when the contract stage is reached.

### Consistent
Apply patterns consistently across resources, representations, methods, errors, identifiers, state transitions, and cross-cutting concerns. Exceptions require a reason.

### Tested
Test the specification through specialist review and concrete consumer scenario simulation. Material revisions require re-testing.

### Concrete
The specification is the blueprint. Important consumer-visible behavior must not exist only in implementation assumptions.

### Immutable
The validated specification is authoritative over implementation. Implementation drift is surfaced rather than silently becoming the new contract.

### Persistent
The specification can evolve. Material evolution is a new design/review/simulation cycle with history.

## Simulation

Initial simulation is scenario-based, not executable mocking. Walk concrete consumers through the proposed contract and record gaps.

An executable mock/contract-test layer is a future extension once a machine-readable contract is established.
