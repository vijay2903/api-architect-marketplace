# HTTP/API Semantics Reference

Use this as guidance, not as an inflexible checklist.

## Resource URLs

Prefer stable nouns for resource-oriented APIs.

Good:
- `/expenses`
- `/expenses/{expense_id}`
- `/users/{user_id}/expenses`

Potentially justified action/protocol paths:
- `/auth/login`
- `/auth/logout`
- `/expenses/{id}/export`

Do not mechanically ban all verbs; determine whether an operation is actually a resource manipulation, state transition, or protocol action.

## Methods

GET — retrieve representations; safe and idempotent.

POST — create a subordinate resource or invoke an operation that does not naturally map to replacement/update.

PUT — replace the representation at a known URI; intended to be idempotent.

PATCH — partial modification; define patch semantics explicitly.

DELETE — remove or otherwise apply deletion semantics to a resource; document soft-delete behavior if used.

## Status codes

Choose based on semantics, not a memorized list.

Common:
- 200 successful response with representation
- 201 created; consider Location when a new resource URI is created
- 202 accepted when processing is asynchronous and not complete
- 204 successful response with no representation
- 400 malformed/invalid request where appropriate
- 401 authentication missing/invalid
- 403 authenticated but not permitted
- 404 resource not found or intentionally indistinguishable from unauthorized access
- 409 state/resource conflict
- 412/428 when preconditions/concurrency controls are used
- 422 when the API deliberately uses semantic validation errors
- 429 rate limited
- 5xx server/dependency failures

Do not force both 400 and 422 without a documented distinction.

## Representation consistency

Choose naming conventions and envelope strategy intentionally.

Avoid response shapes like:
- raw array on one endpoint
- `{data: [...]}` on another
- `{expenses: [...]}` on a third

unless the difference has a reason.

## Monetary values

Do not represent currency with binary floating point in a financial API without an explicit reason.

Possible contract choices:
- decimal string + currency
- integer minor units + currency

Example:

```json
{
  "amount": 1550,
  "currency": "INR"
}
```

Only use this if minor-unit representation fits the domain.
