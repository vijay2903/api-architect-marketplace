# API Architecture Review Checklist

## Product
- Is the API purpose explicit?
- Are consumers identified?
- Are user capabilities explicit?
- Are non-goals explicit?

## Domain
- Are resources meaningful to consumers?
- Are resources confused with database tables?
- Are relationships clear?
- Are internal implementation details hidden?

## Interface
- Are operations understandable?
- Are resource identifiers stable?
- Are representations clear?
- Are errors consistent?
- Are asynchronous operations represented appropriately?
- Are idempotency requirements addressed?

## REST
- Is client/server separation clear?
- Are requests independently understandable?
- Is caching considered where useful?
- Is the interface uniform?
- Are layers/boundaries clear?
- Is REST actually appropriate?

## Security
- Authentication?
- Authorization?
- Sensitive data?
- Rate limits?
- Abuse protection?

## Evolution
- Backward compatibility?
- Versioning strategy?
- Deprecation?
- Documentation?

## Operations
- Observability?
- Failure handling?
- External dependencies?
- Support/ownership?

## Design quality
- Are decisions based on requirements rather than implementation convenience?
- Are assumptions clearly marked?
- Are open questions visible?
- Has the user explicitly confirmed major decisions?
