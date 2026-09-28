# DemoPage plugin

Published by AtomsAI.

[DemoPage](https://demopage.io) gives your website visitors a live, narrated demo inside your real product. This plugin lets your AI coding tool build that demo from your code. It maps every screen from your routes, navigation, UI text, and end-to-end tests, writes what each page lets a customer do, and sends the pages to your DemoPage as candidates. You approve the ones buyers should see, and your demo link turns on.

It works in Cursor, Claude Code, Codex, and ChatGPT.

## What's inside

- **The DemoPage MCP server** at `https://app.demopage.io/mcp`. It acts for your DemoPage account only, after you choose "Sign in with DemoPage" and allow the tool.
- **`create-demopage` skill.** Maps the repo, imports the pages, asks you what to approve, then fixes pages that fail their check.
- **`demopage-results` skill.** Summarizes demo visits, leads, and what buyers asked, and suggests which screens to add next.

The same two guides are offered as prompts by the MCP server, so a tool connected without the plugin gets them too.

## What gets sent, and what doesn't

Your code stays on your machine. The tool sends DemoPage only a title, an https address, a short piece of text visible on the page, a one or two sentence description, and optional keywords for each page. It never sends source code, file contents, environment values, or secrets.

Nothing a tool sends goes into a demo by itself. Every page waits for your approval, then it's loaded in a demo browser. If the expected text isn't on the page, the page stays out. Demos never save, send, pay, or delete anything, and checkout, billing, API key, password, and sign-up screens are refused.

## Before you start

DemoPage is invite-only for now. You need a DemoPage account; [request an invite](https://demopage.io/early-access) if you don't have one. Signed-in pages also need a demo login for your product, which you add in the [portal](https://app.demopage.io/portal), step 5.

## Install

### Cursor

Once DemoPage is listed in the Cursor Marketplace, install it from **Customize**. Until then, copy the `demopage` folder to `~/.cursor/plugins/local/demopage` and run **Developer: Reload Window**.

For the MCP server alone, open the portal's step 6 and choose **Add to Cursor**, or add this to `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "demopage": { "url": "https://app.demopage.io/mcp" } } }
```

Then open **Settings → MCP** and choose **Connect** next to `demopage`.

### Claude Code

Add the AtomsAI marketplace, then install the plugin:

```bash
claude plugin marketplace add gaufire/demopage-plugins
claude plugin install demopage@atomsai
```

To try it from a local copy, run `claude --plugin-dir ./demopage`. Then run `/mcp`, pick `demopage`, and choose **Authenticate**.

For the MCP server alone: `claude mcp add --transport http demopage https://app.demopage.io/mcp`.

### Codex

Add the AtomsAI marketplace, then install DemoPage from the Plugins directory:

```bash
codex plugin marketplace add gaufire/demopage-plugins
```

For the MCP server alone:

```bash
codex mcp add demopage --url https://app.demopage.io/mcp
codex mcp login demopage
```

### ChatGPT

1. Open **Settings → Security and login** and turn on **Developer mode**.
2. Open **Plugins**, choose **+**, and enter `https://app.demopage.io/mcp` with OAuth.
3. Sign in with DemoPage and choose **Allow**.

## Use it

Open your product's repo and ask:

- "Build my DemoPage from this repo."
- "Which demo pages failed their check, and how do I fix them?"
- "What did buyers ask in DemoPage demos this month?"

You can see and disconnect every connected tool in the portal, step 6. Resetting your DemoPage password disconnects all of them.

## Tools

| Tool | What it does |
| --- | --- |
| `demopage_status` | Your website, whether the demo is live, page counts, the last page check, the demo link, and the next step. |
| `demopage_list_pages` | Every page, with its id, approval, and last check. |
| `demopage_import_pages` | Adds mapped pages as candidates, or corrects pages mapped earlier. Nothing goes live from this. |
| `demopage_approve_pages` | Approves or holds pages. Before go-live, this also turns the demo link on. |
| `demopage_check_pages` | Loads every approved page in a demo browser. |
| `demopage_read_site` | Reads your public website again (before go-live). |
| `demopage_get_link` | Your demo link and the embed snippet for your website. |
| `demopage_results` | The last 30 days of visits, demos, questions, pages kept out, and leads. |

## Privacy and terms

[Privacy Policy](https://demopage.io/privacy) · [Terms of Service](https://demopage.io/terms)

## License

MIT
