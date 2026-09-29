# API Architect

Repository-aware, design-only API architecture planner for Claude Code.

## Invocation

```text
/api-architect:api-design
```

## What makes it different

The plugin is intentionally not an endpoint generator.

It uses a staged architecture process:

```text
Product
  ↓
Consumers
  ↓
Capabilities
  ↓
Actions
  ↓
Domain
  ↓
Resources
  ↓
Relationships
  ↓
Boundaries
  ↓
API style
  ↓
Interaction semantics
  ↓
Security / reliability / evolution
  ↓
Endpoint contract
  ↓
Adversarial review
  ↓
User confirmation
```

It maintains:

```text
docs/api-design/API_DESIGN.md
```

and never implements the API.

## Supported modes

- Greenfield
- Continue existing API + gap analysis
- Audit existing API
- Redesign existing API
- Refine an existing API design
