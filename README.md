# Movoice AI for Claude

Use Movoice AI from Claude: create AI phone agents, place and review calls, read transcripts and call results, and manage contacts and bookings for your business, all by asking in plain words.

## Install (Claude Code)

```
/plugin marketplace add Movoiceai/claude-plugin
/plugin install movoice@movoice
```

When asked, paste a Movoice API key. Make one at https://app.movoice.ai/admin/developer and tick only what Claude may do (for example Agents and Calls). The key is stored by Claude Code as a secret and sent only to Movoice.

## What this plugin contains

- `.mcp.json`: connects Claude to Movoice's hosted MCP server at `https://app.movoice.ai/api/mcp/mcp` over HTTPS. Your API key is sent in the `Authorization` header to that address only.
- `skills/movoice/SKILL.md`: guidance for Claude on which tools only read and which act, and to ask you before any call, message, booking change or deletion.

It runs no scripts and no hooks, installs no packages, and sends nothing anywhere except Movoice's own server.

## What Movoice receives

The requests Claude makes on your behalf (for example "list my agents" or "call +91… with agent X"). Calls and messages use your Movoice balance and follow your plan, your key's permissions and India's calling rules. Privacy policy: https://movoice.ai/privacy-policy · Terms: https://movoice.ai/terms-of-service · Support: care@movoice.ai

## Requirements

A Movoice AI account on a paid plan with API access. Calls need the account's identity check to be complete.

## License

MIT
