# API Architect Marketplace

Personal Claude Code marketplace for repository-aware API architecture planning.

## Current release

**API Architect 1.4.1** is an orchestration/token-efficiency release. The architecture methodology remains requirements-first, but the workflow now uses:

- one bounded repository evidence pass plus targeted follow-ups;
- compact design state instead of repeatedly rereading the full design history;
- explicit `USER DECISION REQUIRED` / `ARCHITECT DECISION` / `IMPLEMENTATION DETAIL` ownership;
- decision and phase budgets;
- scoped specialist context and no-rediscovery protection;
- parallel validation with one consolidation/fix pass;
- dependency-aware incremental invalidation;
- explicit partial-stage placeholders;
- architecture freeze and hard stop conditions;
- authoritative current-state index that overrides historical review state;
- explicit artifact-consistency and release-readiness gates;
- implementation/architecture/contract abstraction boundaries;
- one packaged reviewer with bounded validation lenses rather than undocumented phantom agents.

The goal is **deep reasoning once, not repeated reasoning with unchanged inputs**.

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
│       │   ├── api-architect.md
│       │   ├── api-reviewer.md
│       │   └── repository-analyst.md
│       ├── skills/
│       │   └── api-design/
│       │       ├── SKILL.md
│       │       └── references/
│       └── README.md
└── README.md
```

## Install from GitHub

After pushing this repository to GitHub, add the marketplace in Claude Code:

```text
/plugin marketplace add YOUR_GITHUB_OWNER/api-architect-marketplace
```

Then install the plugin:

```text
/plugin install api-architect@api-architect-marketplace
```

The exact marketplace name is the `name` field in `.claude-plugin/marketplace.json`.

## Use

Open one of your projects in Claude Code and run:

```text
/api-architect:api-design
```

The plugin is design-only. It should not implement the API.

## Development

Edit files under:

```text
plugins/api-architect/
```

The supporting reference files are loaded only when their topic is needed; they are not intended to be copied wholesale into every agent context.

Then:

```bash
git add .
git commit -m "..."
git push
```

For testing a local checkout before pushing, Claude Code can load a local marketplace/plugin source; use the current Claude Code plugin documentation for the exact local-development invocation supported by your installed version.
