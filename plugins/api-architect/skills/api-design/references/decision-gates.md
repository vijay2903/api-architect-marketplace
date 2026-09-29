# Spec-Driven API Decision Gates

The planner must not advance merely because it can generate endpoints.

## Gate 1 — Requirements

Must establish:
- desired outcome;
- intended consumers;
- primary capabilities;
- non-goals;
- important constraints.

## Gate 2 — Repository evidence

Must establish:
- current architecture;
- existing API surface;
- relevant workflows;
- technical constraints;
- unknowns.

## Gate 3 — Domain

Must establish:
- important concepts;
- consumer-facing resources;
- identities/lifecycles;
- relationships.

## Gate 4 — Decoupled resources

When a resource-oriented API is being considered, establish:
- stable consumer-facing resource concepts;
- resource/action separation;
- noun-based naming for ordinary resources;
- coherent collection/item or justified singleton semantics;
- backend implementation independence;
- representation boundary;
- content handling/rendering separation when multiple representations are required;
- resource-related caching implications.

Action/protocol paths must have an explicit reason when they do not naturally represent resource manipulation.

## Gate 5 — Boundary

Must establish where relevant:
- ownership;
- sync/async;
- external dependencies;
- consistency;
- retries;
- idempotency;
- concurrency.

## Gate 6 — API style

Compare reasonable styles when the choice is non-obvious. Do not choose by ideology.

## Gate 7 — Contract

Must settle:
- methods/operations;
- representations;
- errors;
- status semantics;
- pagination/search where relevant;
- security semantics.

## Gate 8 — Specialist review

Relevant stakeholder findings must be resolved, explicitly accepted as open, or deferred with a reason.

## Gate 9 — Consumer simulation

Important success and failure journeys must be walked through the proposed specification.

## Gate 10 — SDD validation

All applicable six constraints must PASS.

## Gate 11 — User confirmation

Major architectural decisions must be explicitly confirmed by the user.

## Gate 12 — Contract stage

A machine-readable contract may be generated/maintained only after the design is validated and the contract stage is entered.
