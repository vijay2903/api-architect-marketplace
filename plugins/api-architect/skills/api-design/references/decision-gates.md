# API Design Decision Gates

The planner should not advance merely because it has enough information to generate endpoints.

## Gate 1 — Product

Must know:
- desired outcome
- intended consumers
- primary capabilities

## Gate 2 — Domain

Must know:
- important concepts
- consumer-facing resources
- relationships

## Gate 3 — Boundary

Must know:
- ownership
- sync/async
- external dependencies
- consistency/retry implications

## Gate 4 — API style

Must compare reasonable styles where the choice is non-obvious.

## Gate 5 — Contract

Must settle:
- methods
- representations
- errors
- status semantics
- pagination/search where relevant

## Gate 6 — Production concerns

Must address relevant:
- auth
- authorization
- security
- rate limits
- caching
- observability
- evolution

## Gate 7 — Review

Reviewer findings must be:
- resolved
- explicitly accepted as open
- or deferred with a reason

## Gate 8 — User confirmation

Major decisions must be explicitly confirmed by the user.

A detailed document with only PROPOSED decisions is a draft, not a finalized architecture.
