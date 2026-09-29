# API Architecture Review Checklist

Use this as a scoped validation checklist. Reviewers should not reread unrelated history or restart the workflow.

## Product
- API purpose explicit?
- Consumers identified?
- Capabilities and non-goals explicit?
- Every endpoint/resource has a consumer reason?

## Domain
- Resources meaningful to consumers?
- Database tables/internal pipeline stages hidden unless genuinely consumer-facing?
- Identities, lifecycles, ownership, and relationships clear?

## Interface
- Operations understandable?
- Methods semantically correct?
- Identifiers stable?
- Representations consistent?
- Errors/status semantics coherent?
- Async operations represented appropriately?
- Idempotency/concurrency addressed where relevant?

## REST / style
- Chosen style actually fits requirements?
- Client/server boundary clear?
- Uniform interface and cacheability considered where relevant?
- No REST cargo-culting?

## Security
- Authentication fits actual clients?
- Authorization/tenant isolation explicit?
- Sensitive data protected?
- Browser CSRF/XSS implications considered where relevant?
- Rate limits/abuse controls justified rather than invented?

## Evolution
- Compatibility strategy clear?
- Breaking changes identified?
- Deprecation/documentation behavior addressed where relevant?

## Operations
- Long-running/failure behavior clear?
- External dependencies represented appropriately?
- Observability relevant to support/diagnosis?
- Workload/deployment constraints respected?

## Orchestration quality
- Only changed/dependent areas reviewed?
- Findings classified by owner?
- Technical findings auto-fixable without user involvement?
- Confirmed/locked decisions not reopened without evidence?
- No new review loop needed after this pass?

## Artifact consistency
- Is the authoritative current-state block present and internally consistent?
- Do current open decisions agree with the decision ledger?
- Are historical findings clearly inactive?
- Do architecture and contract revisions agree?
- Does the packaged agent/review-role graph match the documented workflow?
- Are user-authored edits preserved?

## Contract / architecture boundary
- Are externally observable guarantees separated from implementation mechanisms?
- Are locks, tables, queue mechanics, workers, indexes, and provider details excluded unless architecturally necessary?

## Completion
- Assumptions and open questions visible?
- User explicitly confirmed major user-owned decisions?
- Authorized placeholders explicit?
- No critical finding remains?
