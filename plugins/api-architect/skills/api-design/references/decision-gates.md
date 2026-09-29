# API Design Decision Gates

A gate prevents the workflow from advancing because it merely has enough information to generate endpoints. Each gate has entry, exit, and stop conditions.

## Gate 1 — Product

Must establish:
- desired outcome;
- intended consumers;
- primary capabilities;
- non-goals.

**Exit:** no material product ambiguity remains.

**Stop:** do not ask architecture questions before this gate is satisfied.

## Gate 2 — Domain

Must establish:
- important concepts;
- consumer-facing resources;
- identities/lifecycles;
- relationships;
- ownership boundaries.

**Exit:** every confirmed capability has a justified domain representation.

**Stop:** do not turn database tables into endpoints merely because they exist.

## Gate 3 — Boundary

Must establish where relevant:
- ownership/tenancy;
- sync/async behavior;
- external dependencies;
- consistency;
- retry/idempotency;
- concurrency/conflict behavior.

**Exit:** interaction boundaries are coherent.

**Stop:** do not design hypothetical infrastructure.

## Gate 4 — API style

Compare reasonable styles only when the choice is non-obvious.

**Exit:** one style is recommended with evidence and meaningful trade-offs recorded.

**Stop:** do not reopen style because of preference alone after confirmation.

## Gate 5 — Contract

Settle:
- methods;
- representations;
- errors/status semantics;
- pagination/search where relevant;
- compatibility mechanics.

**Exit:** contract can be generated from the frozen architecture.

**Stop:** technical mechanics do not become user questions unless they change product behavior.

## Gate 6 — Production concerns

Address relevant:
- auth/authorization;
- security/privacy;
- rate limits/quotas;
- caching;
- observability;
- evolution.

**Exit:** no relevant concern is silently assumed.

## Gate 7 — Parallel review

Run independent review lenses with scoped context. The packaged `api-reviewer` may execute multiple lenses; do not invent separate agents that are not in the package. Findings must be classified and assigned one owner.

**Exit:** required lenses are complete or explicitly N/A, and findings are ready for one consolidation pass.

**Exit:** findings are resolved, auto-fixed, explicitly accepted, or deferred.

**Stop:** do not start another full review because a technical detail was corrected.

## Gate 8 — User confirmation / freeze

Major user-owned decisions must be explicitly confirmed.

Then:

```text
CONFIRMED → VALIDATED → LOCKED
```

A locked decision reopens only for a new requirement, actual contradiction, or security-critical issue.

## Gate 9 — Final validation

Run one scoped final validation after the consolidation pass.

If no critical defect, contradiction, or unresolved user decision remains, **STOP**.

## Gate 8 — Artifact consistency

Must reconcile current state, decision ledger, architecture revision, contract revision, historical findings, placeholders, and packaged review roles.

**Exit:** one authoritative current state exists and no stale historical material is presented as active.

## Gate 9 — Release readiness

Architectural completeness is not automatically release readiness. Mark release-ready only when required validation is complete, critical findings are resolved, current state is consistent, and any partial contract is explicitly authorized.

**Stop:** do not run additional review loops merely to increase confidence.
