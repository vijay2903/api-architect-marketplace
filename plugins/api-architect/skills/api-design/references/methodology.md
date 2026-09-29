# API Architecture Methodology

## 1. Start with the product

Ask:
- What is this system?
- What are we trying to achieve?
- Who is the user?
- What problem does the API solve?
- What is explicitly out of scope?

## 2. Identify API consumers

Possible consumers:
- own web frontend
- own mobile application
- internal services
- business partners
- third-party developers
- public developers

Consumer type changes requirements around stability, auth, documentation, rate limits, and versioning.

## 3. Identify capabilities before endpoints

Ask what users need to accomplish.

Do not begin with CRUD or existing Python functions.

Example:
- submit a reel
- inspect processing status
- retrieve summary
- search saved reels
- delete a reel

## 4. Identify resources

A resource is a meaningful thing exposed through the API.

Do not equate resource with database table or Python class.

Potential examples:
- User
- Reel
- Order
- Job
- Collection

An internal component is not automatically an API resource.

## 5. Identify relationships

Examples:

User -> Reels
Reel -> Processing Job
Reel -> Summary

Relationships may influence representations, nested resources, and links.

## 6. Evaluate API style

REST should be evaluated through:
- client-server separation
- statelessness
- cacheability
- uniform interface
- layered system
- optional code-on-demand

Also evaluate whether RPC, GraphQL, event-driven interfaces, gRPC, or another style better fits a specific requirement.

Do not force REST for ideological reasons.

## 7. Design the contract

Only after the domain model is understood:
- methods
- resource identifiers
- representations
- request/response shapes
- errors
- status transitions
- asynchronous behavior
- authentication
- authorization

## 8. Long-term concerns

Plan where relevant:
- backward compatibility
- versioning
- rate limiting
- security
- observability
- documentation
- support
- deprecation

## 9. User confirmation

A proposal is not a decision.

Keep unresolved items visible until the user confirms them.
