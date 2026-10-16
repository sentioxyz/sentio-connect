# Sentio Connect — Codex plugin

Installs the hosted Sentio Connect MCP server (`https://connect.sentio.xyz/v1/mcp`) into Codex,
plus a skill describing when to use each tool. Auth is OAuth: Codex opens the Sentio Connect
consent page on first use.

```text
/plugin marketplace add sentioxyz/sentio-connect
/plugin install sentio-connector@sentio
```

Or, without the plugin, point Codex straight at the server:

```bash
codex mcp add sentio --url https://connect.sentio.xyz/v1/mcp
codex mcp login sentio
```

Layout:

- `.codex-plugin/plugin.json` — manifest (metadata + pointers below)
- `.mcp.json` — the remote MCP server entry
- `skills/sentio-connect/SKILL.md` — tool usage guidance for the model
- `assets/` — `app-icon.png` (1024×1024 plugin logo) and `sentio-icon.svg` (composer icon)

Codex does not render MCP Apps (`ui://`) widgets; tool results fall back to text and `structuredContent`.
