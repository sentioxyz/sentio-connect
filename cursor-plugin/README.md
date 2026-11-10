# Sentio Connect — Cursor plugin

Adds the hosted Sentio Connect MCP server (`https://connect.sentio.xyz/v1/mcp`) to Cursor,
plus a skill describing when to use each tool. Ask about wallet balances, token prices,
portfolio value, DeFi positions and 24h/7d holding history.

## Install

Install **Sentio Connect** from the Cursor Marketplace. There is nothing to run locally and
nothing to configure: no API keys or environment variables.

Or, without the plugin, add the server to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "sentio": { "url": "https://connect.sentio.xyz/v1/mcp" }
  }
}
```

## Sign in

Auth is OAuth. On first use Cursor opens the Sentio Connect consent page; sign in and approve.
If a tool later returns an authorization error, re-authorize the `sentio` server in
Cursor Settings → MCP.

## Usage

Ask in chat, for example:

- "What is in my wallets?"
- "Track vitalik.eth"
- "What is my total portfolio value?"
- "Show my DeFi positions"
- "How did my ETH balance change over the last 7 days?"

Tools can be enabled or disabled per account at <https://connect.sentio.xyz>.

## Layout

- `.cursor-plugin/plugin.json` — manifest (metadata + pointers below)
- `mcp.json` — the remote MCP server entry
- `skills/sentio-connect/SKILL.md` — tool usage guidance for the model
- `assets/logo.png` — plugin logo
