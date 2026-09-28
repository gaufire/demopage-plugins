# AtomsAI plugins

Plugins for AI coding tools, published by AtomsAI.

| Plugin | What it does |
| --- | --- |
| [DemoPage](demopage/README.md) | Builds a live, narrated demo of your product from its code. |

This repository is a plugin marketplace for Cursor, Claude Code, and Codex.

## Add it

Claude Code:

```bash
claude plugin marketplace add gaufire/demopage-plugins
claude plugin install demopage@atomsai
```

Codex:

```bash
codex plugin marketplace add gaufire/demopage-plugins
```

Then install DemoPage from the Plugins directory.

Cursor: install DemoPage from the Cursor Marketplace, or copy the `demopage` folder to `~/.cursor/plugins/local/demopage` and run **Developer: Reload Window**.

See the [DemoPage plugin README](demopage/README.md) for ChatGPT and for connecting the MCP server on its own.

## Layout

- `.cursor-plugin/marketplace.json` is read by Cursor.
- `.claude-plugin/marketplace.json` is read by Claude Code.
- `.agents/plugins/marketplace.json` is read by Codex and ChatGPT.
- Each plugin carries a portable `plugin.json` and `mcp.json` ([Agent Plugins 1.0](https://agent-plugins.org), read by Cursor and Codex), plus `.claude-plugin/plugin.json` and `.mcp.json` for Claude Code.

## License

MIT. See each plugin's `LICENSE`.
