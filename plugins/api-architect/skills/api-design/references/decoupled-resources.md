# Decoupled Resource Architecture

This reference adapts the resource-design guidance from the supplied REST chapter into the plugin's Spec-Driven Development workflow.

## 1. Core idea

A REST resource should be a stable interface concept that is decoupled from the actions performed on it and from the server-side implementation that realizes it.

The resource is the consumer-facing identity. HTTP methods, representations, and justified domain/protocol actions describe how the consumer interacts with that identity.

The public resource should not be a mirror of:
- a class;
- a controller method;
- a database table;
- a microservice;
- a queue/topic;
- an internal pipeline stage;
- a vendor/provider boundary.

The chapter emphasizes that decoupling resources from application architecture allows server-side services and technologies to evolve without forcing corresponding client changes.

## 2. Resource design procedure

For every candidate resource, perform this sequence before approving its URI:

### Step 1 — Identify the consumer concept

State the real concept the consumer needs to interact with.

Do not start with the implementation object.

### Step 2 — Identify stable identity

Define what makes one resource distinguishable from another and whether that identity can survive backend refactoring.

### Step 3 — Separate resource from actions

List the legitimate operations the consumer needs.

Ask whether those operations can share one resource identity.

Bad:

```text
/getUsers
/createUser
/updateUser
/deleteUser
```

Prefer a resource-oriented design where the same resource supports the appropriate operations.

### Step 4 — Choose collection/item structure

When multiple instances are possible, prefer a collection and item pattern:

```text
/users
/users/{user_id}
```

Use a singleton only when the domain genuinely has one conceptual instance for the relevant scope. Record why it is a singleton and whether future multiplicity is plausible.

### Step 5 — Check implementation independence

Ask:

> If the database, framework, service decomposition, queue topology, or internal classes changed while consumer requirements stayed the same, would this resource still make sense?

If not, the resource is probably too tightly coupled.

### Step 6 — Check relationships

Model relationships between consumer concepts, not arbitrary foreign-key relationships.

A relationship can affect nesting, links, representations, or query capabilities, but should not automatically expose database joins.

### Step 7 — Separate representation from resource identity

The resource concept is not identical to JSON, XML, YAML, or another wire format.

If multiple representations are actually required, keep parsing/rendering at the interface boundary:

```text
request
  ↓
content handler / deserializer
  ↓
normalized input
  ↓
application/domain logic
  ↓
resource representation
  ↓
view / representation renderer
  ↓
response
```

Do not create multiple domain models merely because multiple wire representations exist unless the domain genuinely requires different semantics.

## 3. Noun-based naming

Prefer stable nouns for resource-oriented interfaces.

Good examples:

```text
/users
/clients
/orders
/tickets
```

Potentially problematic examples when used as resources:

```text
/getUsers
/createOrder
/processTicket
/calculateSummary
```

Action/protocol paths can still be justified when the operation is genuinely a domain/protocol action that does not naturally correspond to manipulation of a resource. Document the exception and why a resource-oriented form would be misleading.

## 4. Plural versus singular

The chapter recommends plural resource names because a plural collection can naturally accommodate collection and item interactions and future multiplicity.

The plugin should treat this as a strong default, not an absolute law.

Use a singleton when the domain genuinely has one conceptual instance in the relevant scope, for example a current profile or cart. Do not create both singular and plural forms for the same concept without a clearly distinct meaning.

## 5. Good practices

- Stable consumer-facing nouns.
- Collection/item consistency.
- One resource identity supporting multiple legitimate operations.
- Backend implementation hidden behind the resource boundary.
- Consistent relationship modeling.
- Representation handling separated from domain processing.
- Content negotiation introduced only when requirements justify it.
- Cacheability and visibility specified explicitly.
- Exceptions to conventions documented with rationale.
- Resource design reviewed against future backend evolution.

## 6. Bad practices

- One endpoint/resource per backend method.
- Verb-based resource names for ordinary CRUD/resource manipulation.
- Public URIs derived directly from database tables.
- Public URIs derived from microservice names.
- Public exposure of internal processing stages.
- Duplicate singular/plural representations of one concept.
- Different resource names for the same concept in different parts of the API.
- Representation-specific business logic scattered through domain code.
- Supporting many media types without consumer requirements.
- Declaring responses cacheable without defining visibility, freshness, and invalidation behavior.

## 7. Decoupling review questions

Before Gate: Contract, answer:

1. What consumer concept does each resource represent?
2. What implementation detail could change without changing the resource?
3. Can multiple operations use this resource identity?
4. Is the URI named after a noun/concept rather than an action?
5. Is collection/item structure coherent?
6. Is this a real singleton or merely a current implementation restriction?
7. Does the resource expose a database/service/pipeline boundary accidentally?
8. Are relationships consumer-facing rather than storage-facing?
9. Is representation independent from domain semantics?
10. If multiple representations are needed, are parsing/rendering separated from domain processing?
11. Are caching semantics defined where relevant?
12. Would adding a new capability require inventing another action-specific resource unnecessarily?

## 8. Source-derived caution

The supplied chapter strongly advocates resource decoupling, noun-based resources, plural collections, representation flexibility, layered content handlers/renderers, and explicit caching/versioning considerations.

The plugin should preserve the architectural principle while avoiding cargo-cult rules. In particular, multiple media types, singular/plural conventions, caching policies, and versioning mechanisms must still be justified by actual consumer and evolution requirements.
