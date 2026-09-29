# HTTP/API Semantics Reference

Use as guidance, not an inflexible checklist.

## Resource URLs

Prefer stable nouns for resource-oriented APIs.

Potentially justified action/protocol paths include authentication operations or domain actions such as exports when they do not naturally map to ordinary resource manipulation.

## Methods

- GET — retrieve representations; safe and idempotent.
- POST — create a subordinate resource or invoke an operation that does not naturally map to replacement/update.
- PUT — replace a representation at a known URI; intended to be idempotent.
- PATCH — partial modification; define patch semantics explicitly.
- DELETE — apply documented deletion semantics; document soft-delete behavior if used.

## Status codes

Choose based on semantics. Common candidates include:
- 200 successful response with representation;
- 201 created;
- 202 accepted for incomplete asynchronous processing;
- 204 successful response with no representation;
- 400 malformed/invalid request where appropriate;
- 401 authentication missing/invalid;
- 403 authenticated but not permitted;
- 404 not found or intentionally indistinguishable from unauthorized access;
- 409 state/resource conflict;
- 412/428 precondition/concurrency controls;
- 422 semantic validation errors if deliberately used;
- 429 rate limited;
- 5xx server/dependency failures.

If both 400 and 422 are used, document the distinction.

## Representation consistency

Choose naming and envelope strategy intentionally. Do not mix unrelated collection/response shapes without a reason.

## Monetary values

Avoid binary floating point for currency without an explicit reason. Contract options include decimal strings plus currency or integer minor units plus currency when appropriate to the domain.
