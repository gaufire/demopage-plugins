# AtomsAI plugins

Plugins for AI coding tools, published by AtomsAI.

| Plugin | What it does |
| --- | --- |
| [DemoPage](demopage/README.md) | Builds a live, narrated demo of your product from its code. |

This folder is a marketplace for Cursor, Claude Code, and Codex:

- Cursor reads `.cursor-plugin/marketplace.json`.
- Claude Code reads `.claude-plugin/marketplace.json`.
- Codex and ChatGPT read `.agents/plugins/marketplace.json`.

Each plugin carries a portable `plugin.json` and `mcp.json` ([Agent Plugins 1.0](https://agent-plugins.org), read by Cursor and Codex), plus `.claude-plugin/plugin.json` and `.mcp.json` for Claude Code.

## Publishing

Marketplaces install from a public Git repository, so publish this folder as its own repository root. Then:

1. Cursor: submit the repository at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish).
2. Claude Code: users run `claude plugin marketplace add <owner>/<repo>`. To list it in Anthropic's directory, submit it there.
3. Codex and ChatGPT: users run `codex plugin marketplace add <owner>/<repo>`. To list it in OpenAI's plugin directory, submit it there.

Keep the `version` in `demopage/plugin.json` and `demopage/.claude-plugin/plugin.json` the same. The DemoPage app serves the skills as MCP prompts from a copy; after editing a `SKILL.md`, run `node scripts/sync-plugin-skills.mjs` in the app repository.
