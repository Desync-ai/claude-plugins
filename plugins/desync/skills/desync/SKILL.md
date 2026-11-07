---
name: desync
description: Use when the user asks about Catholic parishes, clergy and parish staff, businesses that advertise in parish bulletins, or Notre Dame alumni, or about their own Desync Second Brain records (people, companies, deals, tasks, notes). Says which Desync MCP server answers what and how to use its tools well.
---

# Desync over MCP

This plugin adds two MCP servers. Each asks the user to sign in the first time: run `/mcp`, pick the server, and
follow the sign-in in the browser.

| Server | Address | What it reaches |
|---|---|---|
| `desync` | https://mcp.desync.ai/mcp | Desync's Catholic data, the user's lookup history and saved lists |
| `desync-second-brain` | https://crm.desync.ai/mcp | The user's own records in Desync Second Brain |

## Desync data (`desync`)

- `church_search`: parishes by name, place, diocese, language, school and more, with staff and contacts if asked. Up to
  100 a call.
- `church_people_search`: clergy and parish staff by name, place, role, title, or with an email or phone on record. Up
  to 200 a call.
- `church_sponsor_search`: businesses that advertise in parish bulletins, by place and keyword. Up to 200 a call.
- `nd_search`, `nd_batch_search`, `nd_mass_match`, `nd_similar`: Notre Dame alumni by name, many names at once, any
  field, or the graduates most like one you name.
- `lookup_history`: records the user already looked up, free to read again.
- `list_custom_tables`, `get_custom_table`, `create_custom_table`, `add_to_custom_table`, `update_custom_table_entry`:
  the user's saved lists, with each entry's outreach status, notes and draft email.

Searches count against the user's plan; history and saved lists are free. So:

1. Before a new search for something the user may have looked up already, read `lookup_history`.
2. Ask for the fields and the size you need. Do not page through a whole state when the user wants a few names.
3. When the user wants to keep results, save them to a list with `create_custom_table` and `add_to_custom_table`
   rather than pasting them into the chat. Duplicates are skipped.

Schools and hospitals are searched in the Desync app, not yet over MCP. If the user asks for them, say so.

## Second Brain (`desync-second-brain`)

The user's own records: people, companies, deals, tasks and notes, and any objects they added. Read freely; before
creating, updating or deleting a record, say what will change and wait for the user's yes.

## Help

Docs: https://www.desync.ai/docs#mcp. Install page: https://www.desync.ai/mcp. Questions: support@desync.ai.
