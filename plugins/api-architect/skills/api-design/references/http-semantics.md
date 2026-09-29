# HTTP/API Semantics Reference

Use this as guidance, not as an inflexible checklist. Technical HTTP mechanics are normally architect-owned.

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

Do not mechanically ban verbs; distinguish resource manipulation, state transitions, and protocol actions.

## Methods

- `GET` — retrieve representations; safe and idempotent.
- `POST` — create a subordinate resource or invoke an operation that does not naturally map to replacement/update.
- `PUT` — replace the representation at a known URI; intended to be idempotent.
- `PATCH` — partial modification; define patch semantics explicitly.
- `DELETE` — deletion semantics; document soft-delete behavior if used.

## Status codes

Choose by semantics, not memorized lists. Common choices include:

- `200` successful response with representation;
- `201` created; consider `Location`;
- `202` accepted for asynchronous processing;
- `204` successful response without representation;
- `400` malformed/invalid request where appropriate;
- `401` missing/invalid authentication;
- `403` authenticated but not permitted;
- `404` missing resource or intentionally indistinguishable authorization case;
- `409` state/resource conflict;
- `412`/`428` when preconditions/concurrency controls are used;
- `422` when the API deliberately uses semantic validation errors;
- `429` rate limited;
- `5xx` server/dependency failures.

Do not force both `400` and `422` without a documented distinction.

## Representation consistency

Choose naming conventions and envelope strategy intentionally. Avoid unexplained variation such as raw arrays, `{data: [...]}`, and resource-specific envelopes across similar endpoints.

## Monetary values

Do not use binary floating point for financial values without an explicit reason. Possible contract representations include decimal strings + currency or integer minor units + currency when the domain supports it.
