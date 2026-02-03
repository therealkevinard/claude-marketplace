# Claude Plugin Marketplace

A personal collection of Claude Code plugins.

## Adding This Marketplace

Register this marketplace with Claude Code:

```bash
claude plugins add-marketplace https://github.com/therealkevinard/claude-marketplace
```

This adds the marketplace to your Claude Code configuration, making its plugins available for installation.

## Installing Plugins

Once the marketplace is registered, list available plugins:

```bash
claude plugins list
```

Install a plugin by name:

```bash
claude plugins install kevins-okay-workflow
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| `kevins-okay-workflow` | A deliberate, phased workflow for collaborative planning and execution |

## Plugin Structure

Each plugin in this marketplace follows the standard Claude plugin format:

```
plugins/
└── plugin-name/
    ├── .claude-plugin/
    │   └── plugin.json      # Plugin metadata
    ├── skills/              # Skill definitions
    │   └── skill-name/
    │       └── SKILL.md
    └── README.md
```

## Creating Your Own Marketplace

To create your own plugin marketplace:

1. Create a repository with a `.claude-plugin/marketplace.json` at the root:

```json
{
  "name": "your-marketplace-name",
  "owner": {
    "name": "your-username"
  },
  "metadata": {
    "description": "Your marketplace description"
  },
  "plugins": [
    {
      "name": "plugin-name",
      "source": "./plugins/plugin-name",
      "description": "Plugin description"
    }
  ]
}
```

2. Add plugins under the `plugins/` directory, each with its own `.claude-plugin/plugin.json`

3. Push to GitHub and register with `claude plugins add-marketplace`
