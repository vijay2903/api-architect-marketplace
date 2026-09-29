# Resource Design Methodology

Use this as a practical procedure before endpoint design.

## 1. Start with the consumer concept

Describe the thing the consumer needs to interact with in domain language.

## 2. Separate concept from action

List the actions the consumer needs. Do not create a new resource for each action.

Ask whether one stable resource identity can support the operations through methods, representations, or a justified domain action.

## 3. Separate concept from implementation

Do not derive public resource names from:
- database tables;
- ORM models;
- controller names;
- service names;
- queues;
- internal jobs;
- vendor APIs;
- pipeline stages.

Implementation evidence can constrain the design, but does not define the public resource by itself.

## 4. Choose URI shape

Prefer stable nouns and coherent collection/item patterns.

```text
/orders
/orders/{order_id}
```

Use action/protocol paths only when a resource-oriented representation would be misleading.

## 5. Test backend independence

Imagine replacing:
- the database;
- framework;
- service decomposition;
- provider;
- queue;
- internal domain classes.

If the consumer contract should remain the same, the resource should remain meaningful after those changes.

## 6. Separate representation

The resource is a conceptual API object. JSON/XML/etc. are representations.

When multiple representations are required, keep content handling and rendering at the interface boundary.

```text
wire format → handler → normalized input → domain/application → representation → renderer → wire format
```

Do not create representation-specific domain logic without a semantic reason.

## 7. Evaluate caching with the resource

For each cacheable representation determine:
- visibility: public/private;
- freshness tolerance;
- invalidation/update behavior;
- authorization variation;
- representation variation.

Caching is a contract property, not merely an infrastructure optimization.

## 8. Review future extensibility

Ask:
- Could this concept naturally gain another operation later?
- Would that require creating `/doSomething` as a new resource?
- Would a current singleton become plural later?
- Would backend decomposition force a URI change?

Do not over-design hypothetical future features, but avoid coupling the contract to today's accidental implementation limits.
