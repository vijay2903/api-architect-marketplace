# Standard API Design Requirements Interview

The interview establishes requirements before architecture.

## Rules
- Ask in small batches.
- Do not ask architecture questions prematurely.
- Record unknowns instead of inventing answers.
- Clarify answers that materially change architecture.
- Always ask the open-ended final question.
- Keep requirements separate from proposals.
- Add repository-derived follow-up questions after investigation.

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

## Do not decide during this interview
- REST vs GraphQL
- JWT vs sessions
- URL vs header versioning
- offset vs cursor pagination
- endpoint names
- database schema
- framework choice

Those are architecture decisions.
