# API Specification Review Checklist

## Product and consumers
- API purpose explicit?
- Consumers identified?
- Capabilities explicit?
- Non-goals explicit?
- Consumer scenarios represented?

## Resource decoupling
- Does each resource represent a stable consumer-facing concept?
- Are ordinary resources named with nouns rather than actions?
- Can multiple legitimate operations use the same resource identity?
- Are action/protocol paths explicitly justified?
- Are collection/item semantics coherent?
- Are singleton resources genuinely singleton?
- Are database/service/queue/pipeline boundaries hidden?
- Would backend refactoring preserve the resource contract?
- Are resource semantics separated from wire representation?
- If multiple representations are needed, are content handlers/renderers separated from domain processing?
- Are resource-related caching semantics explicit?

## Domain
- Resources meaningful to consumers?
- Database tables avoided as automatic resources?
- Relationships clear?
- Internal implementation details hidden?
- Lifecycles/state transitions coherent?

## Interface
- Operations understandable?
- Identifiers stable?
- Representations clear and consistent?
- Errors consistent?
- Async operations represented appropriately?
- Idempotency addressed?
- Concurrency/conflict behavior addressed?

## HTTP/REST
- REST actually appropriate?
- Client/server separation clear?
- Requests independently understandable?
- Uniform interface semantics coherent?
- Caching considered where useful and safe?
- Methods semantically correct?
- Status code policy coherent?

## Security
- Authentication fits clients?
- Authorization/ownership explicit?
- Browser CSRF/XSS risks considered where relevant?
- Sensitive data protected?
- Tenant isolation considered?
- Abuse/rate limits justified?

## Reliability
- Long-running work modeled?
- Retry semantics safe?
- Idempotency explicit?
- Concurrency explicit?
- External failures represented?

## Evolution
- Backward compatibility addressed?
- Versioning justified?
- Deprecation addressed where relevant?
- Extensibility considered?
- Specification evolution process defined?

## Operations
- Observability?
- Failure handling?
- External dependencies?
- Operational ownership?
- Health/status endpoints have actual consumers?
- Infrastructure recommendations justified by requirements?

## SDD constraints
- Standardized?
- Consistent?
- Tested through review + scenario simulation?
- Concrete?
- Immutable against silent implementation drift?
- Persistent/evolvable through a deliberate cycle?

## Decision quality
- Requirements rather than implementation convenience drive decisions?
- Assumptions clearly marked?
- Open questions visible?
- Findings dispositioned?
- Major decisions explicitly user-confirmed?
