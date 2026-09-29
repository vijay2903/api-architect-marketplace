# API Architect Marketplace

Personal Claude Code marketplace for Spec-Driven API architecture planning.

## v1.4.0 — Decoupled Resource Architecture

This version extends the v1.3 Spec-Driven Development workflow with a dedicated **decoupled resource architecture** discipline based on the supplied REST chapter.

The planner now explicitly checks that API resources:

- represent stable consumer-facing concepts;
- are decoupled from actions and backend methods;
- use noun-based collection/item structures where appropriate;
- do not expose database, service, queue, or pipeline topology;
- remain meaningful when backend technologies evolve;
- separate resource semantics from wire representations;
- isolate content handling/rendering when multiple representations are actually required;
- consider caching as part of the resource contract.

The plugin remains design-only. It does not implement the API.

## Install

After pushing this repository to GitHub, add the marketplace in Claude Code:

```text
/plugin marketplace add YOUR_GITHUB_OWNER/api-architect-marketplace
```

Then install:

```text
/plugin install api-architect@api-architect-marketplace
```

## Use

```text
/api-architect:api-design
```

## Repository layout

```text
api-architect-marketplace/
├── .claude-plugin/
│   └── marketplace.json
├── plugins/
│   └── api-architect/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── agents/
│       ├── skills/
│       └── README.md
└── README.md
```
