# Standard API Design Requirements Interview

The interview establishes requirements before architecture. Ask small batches and stop when equivalent reliable answers already exist.

## Rules

- Ask in small batches, never as a giant questionnaire.
- Do not ask architecture questions prematurely.
- Record unknowns instead of inventing answers.
- Clarify only answers that materially change architecture or product behavior.
- Preserve the user's terminology.
- Keep requirements separate from proposals.
- Always ask the open-ended final question unless already answered.
- After repository investigation, ask only repository-derived questions that can change the design.
- Respect the user-decision budget; classify technical questions as architect-owned instead.

## Questions

1. Application/system
2. API goal
3. Desired capability gap
4. Non-goals
5. Consumers and current/planned consumers
6. User/client capabilities
7. Constraints
8. Expected workload
9. User-facing domain concepts
10. Authentication/access requirements
11. Long-running operations
12. Client interaction needs
13. Sensitive/protected data
14. Compliance/security requirements
15. Consumer/backend deployment independence
16. Deployment/operations
17. Additional user context

For question 17, explicitly say:

> You can mention anything that wasn't covered above. You don't need to use API terminology.

## Do not decide during this interview

- REST vs GraphQL/RPC
- JWT vs sessions
- URL vs header versioning
- offset vs cursor pagination
- endpoint names
- database schema
- framework choice
- low-level HTTP status/header mechanics

Those are architecture decisions unless they change a product-level requirement.

## Interview output

Record:
- requirements;
- unknowns;
- constraints;
- non-goals;
- assumptions that must not become decisions;
- repository-derived questions.

Only request user correction when a material ambiguity remains.
