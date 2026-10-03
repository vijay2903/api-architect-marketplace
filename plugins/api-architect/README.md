# API Architect

A design-only Claude Code plugin for repository-aware, Spec-Driven API architecture.

## v1.4.0 focus

The API design workflow now treats **resource decoupling** as an explicit architecture gate when resource-oriented APIs are considered.

The plugin asks whether each resource is a stable consumer-facing concept rather than a backend method, class, database table, service, queue, or pipeline stage. It also checks noun-based naming, collection/item semantics, backend independence, representation boundaries, content handlers/renderers where needed, and caching implications.

Specialist review is adaptive. `resource-design-reviewer` is invoked when resource coupling, action-like paths, implementation leakage, representation flexibility, or resource-related caching are material concerns.

## Design-only boundary

The plugin does not implement routes, controllers, schemas, authentication, infrastructure, or application code. It produces and maintains design/specification artifacts only.
