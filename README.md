# AgentDeals: one-stop US price search for AI agents

One call compares 100M+ products across Amazon, Walmart, Target, Best Buy, Costco, Lowe's, Newegg, B&H and 150+ more US stores, and returns the lowest current price, the store, the rating and a buy link.

- **MCP server (streamable HTTP, no auth):** `https://agentdeals.app/mcp`
- **Website:** https://agentdeals.app · **Black Friday deals:** https://agentdeals.app/black-friday
- **Docs for agents:** https://agentdeals.app/llms.txt · **OpenAPI:** https://agentdeals.app/openapi.json
- **Official MCP Registry:** `app.agentdeals/agentdeals`

## Connect your agent

| Client | Setup |
|---|---|
| Claude Code | `claude mcp add --transport http agentdeals https://agentdeals.app/mcp` |
| Claude (claude.ai, Desktop) | Settings → Connectors → Add custom connector → `https://agentdeals.app/mcp` |
| ChatGPT | Settings → Apps & Connectors → Advanced → Developer mode → Create connector → `https://agentdeals.app/mcp` |
| Cursor | `~/.cursor/mcp.json`: `{"mcpServers":{"agentdeals":{"url":"https://agentdeals.app/mcp"}}}` |
| VS Code (Copilot) | `.vscode/mcp.json`: `{"servers":{"agentdeals":{"type":"http","url":"https://agentdeals.app/mcp"}}}` |
| Codex CLI | `~/.codex/config.toml`: `[mcp_servers.agentdeals]` then `url = "https://agentdeals.app/mcp"` |
| Gemini CLI | `~/.gemini/settings.json`: `{"mcpServers":{"agentdeals":{"httpUrl":"https://agentdeals.app/mcp"}}}` |
| Anything else | `curl "https://agentdeals.app/api/search?q=65+inch+tv&max_price=600"` |

Add the agent skill so your agent knows when to use it:

```bash
npx skills add misbahsy/agentdeals
```

## Tools

| Tool | What it does |
|---|---|
| `search_products` | Natural-language product search ("65 inch tv under 600") across all stores; lowest price per product with buy link, rating and deal label. |
| `get_product` | Every store's offer for one product, cheapest first. |
| `get_comparison` | Curated, regularly refreshed comparison for a popular category. |
| `get_deals` | Today's biggest discounts across categories and stores. |

Coverage is US retailers only. Prices are USD and each result says how fresh it is (`as_of`).

## Disclosure

AgentDeals may earn a commission when you buy through its links. As an Amazon Associate we earn from qualifying purchases.
