# Installing Sentio Connect (for AI agents)

Sentio Connect is a **hosted** remote MCP server. There is nothing to clone, build, install or run locally, and no API key or environment variable to set.

- Server URL: `https://connect.sentio.xyz/v1/mcp`
- Transport: Streamable HTTP
- Auth: OAuth 2.1 with dynamic client registration and PKCE, done in the browser

## Steps (Cline)

1. Add this entry to the `mcpServers` object in `cline_mcp_settings.json`, keeping any servers already there:

   ```json
   "sentio": {
     "type": "streamableHttp",
     "url": "https://connect.sentio.xyz/v1/mcp",
     "disabled": false,
     "autoApprove": []
   }
   ```

   Set `"type": "streamableHttp"` explicitly; without it Cline falls back to the legacy SSE transport, which this server does not serve. Do not add an `Authorization` header.

2. When Cline connects, the server answers `401` with OAuth metadata. Ask the user to complete the browser sign-in and consent on the Sentio Connect page that opens. If no browser opens, use Cline's **Authorize OAuth** action for the `sentio` server.

3. Verify the connection by calling `get_token_price` with `{"symbol": "ETH"}`. It should return a USD price.

4. Optionally try `get_wallet_balances` with `{"address": "vitalik.eth", "chain": 1}`.

## Tools

Read: `get_wallet_balances`, `get_token_price`, `get_portfolio_value`, `list_wallet_addresses`, `get_defi_positions`, `get_token_balance_history`, `get_defi_position_history`.
Write (only the user's own tracked-address list): `add_wallet_address`, `remove_wallet_address`. Confirm with the user before calling `remove_wallet_address`.

Supported chains: Ethereum `1`, BNB Chain `56`, Base `8453`, Arbitrum `42161`, Sui `sui_mainnet`.

## Troubleshooting

- `401` after sign-in: delete the `sentio` server and add it again to start a fresh OAuth flow.
- "capability disabled": the user turned that data type off at https://connect.sentio.xyz; tell them rather than retrying.
