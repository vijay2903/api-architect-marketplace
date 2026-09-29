# API Architecture Methodology

Use this as the architectural reasoning reference. The main skill owns orchestration, budgets, state, and stop conditions.

## 1. Start with the product

Establish:
- system and desired outcome;
- API problem/capability gap;
- users/consumers;
- non-goals.

Do not choose technologies while gathering requirements.

## 2. Identify consumers and capabilities

Consumers may include the own web/mobile client, internal services, partners, or third parties. Consumer type affects stability, auth, documentation, limits, and evolution.

Identify what consumers need to accomplish before naming endpoints or exposing implementation structures.

## 3. Model concepts and resources

A resource is a meaningful consumer-facing concept, not automatically a database table, Python class, queue item, or internal pipeline stage.

For each resource establish:
- consumer reason;
- stable identity;
- lifecycle/state;
- ownership;
- relationships.

Analytics may be a representation/query, read model, subresource, or action depending on consumer needs.

## 4. Decide boundaries before paths

Resolve where the API boundary sits and whether work is:
- synchronous or asynchronous;
- request/response or event/webhook where required;
- owned by a user/tenant/system;
- subject to consistency, retry, idempotency, or concurrency constraints.

Do not design future infrastructure merely to keep hypothetical options open.

## 5. Evaluate API style

Evaluate REST first when appropriate, but compare RPC, GraphQL, gRPC, event-driven, or hybrid styles when actual requirements make the choice non-obvious.

Use client diversity, resource orientation, query flexibility, streaming, long-running work, internal communication, public stability, and operational complexity as evidence.

## 6. Design the contract last

Only after the architecture is coherent decide:
- URI/resource structure;
- methods;
- representations;
- errors/status semantics;
- pagination/filtering/search;
- auth/authorization details;
- evolution mechanics.

Technical contract mechanics are architect-owned unless they change product behavior.

## 7. Long-term concerns

Address only relevant:
- compatibility/versioning;
- rate limits/quotas;
- security/privacy;
- caching;
- observability;
- documentation;
- support/deprecation.

Use workload and deployment constraints as complexity guardrails.

## 8. Confirmation

A proposal is not a user decision. The architect should recommend technical choices. Ask the user only when a decision materially affects product behavior, scope, privacy, compatibility, or another meaningful product-level trade-off.

Confirmed decisions should be locked only when the user indicates they should not be revisited during the current design.
