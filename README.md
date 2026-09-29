# API Architect Marketplace

Personal Claude Code marketplace for API architecture planning.

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

Then:

```bash
git add .
git commit -m "..."
git push
```

For testing a local checkout before pushing, Claude Code can load a local marketplace/plugin source; use the current Claude Code plugin documentation for the exact local-development invocation supported by your installed version.
