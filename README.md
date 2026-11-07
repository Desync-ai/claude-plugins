# Desync plugins for Claude Code

Desync's official Claude Code plugin marketplace. One plugin, `desync`, adds both of Desync's MCP servers and a short
skill that tells Claude which server answers what.

| Server | Address | What it reaches |
|---|---|---|
| `desync` | `https://mcp.desync.ai/mcp` | Parishes, clergy and parish staff, bulletin advertisers and Notre Dame alumni, with your lookup history and saved lists |
| `desync-second-brain` | `https://crm.desync.ai/mcp` | Your own records in Desync Second Brain: people, companies, deals, tasks and notes |

## Install

In Claude Code:

```text
/plugin marketplace add Desync-ai/claude-plugins
/plugin install desync@desync
```

Then run `/mcp`, pick each server and sign in. Desync data takes the Google account on your Desync account; Second
Brain takes your Second Brain sign-in. No key to paste.

One server at a time, from a terminal:

```bash
claude mcp add --transport http --scope user desync https://mcp.desync.ai/mcp
```

```bash
claude mcp add --transport http --scope user desync-second-brain https://crm.desync.ai/mcp
```

## Claude, Claude Desktop and Cursor

Use the buttons on [desync.ai/mcp](https://www.desync.ai/mcp): **Add to Claude** opens Claude's Add custom connector
dialog with Desync filled in, and **Add to Cursor** opens Cursor's install prompt.

## Layout

```text
.claude-plugin/marketplace.json     the marketplace, named "desync"
plugins/desync/.claude-plugin/plugin.json
plugins/desync/.mcp.json            the two servers
plugins/desync/skills/desync/       which server answers what, and how to spend searches well
```

Check it before a push: `claude plugin validate .` and `claude plugin validate plugins/desync`.

## Help

Docs: [desync.ai/docs](https://www.desync.ai/docs#mcp). Questions: support@desync.ai.

## License

MIT. The Desync name and mark are Desync AI, Inc.'s trademarks and are not covered by the license.
