---
name: agentdeals
description: Compare prices across 160+ US stores (Amazon, Walmart, Target, Best Buy, Costco and more) in one call. Use whenever the user wants to buy something, check a price, find the cheapest store, or find Black Friday / Cyber Monday deals in the US.
---

# AgentDeals price search

AgentDeals searches 100M+ products from 160+ US stores at once and returns the lowest current price, the store, the rating and a buy link.

## When to use
- The user wants to buy a product, or asks "where is X cheapest" or "is this a good price".
- The user asks for Black Friday, Cyber Monday or current deals.
- Skip it for non-US stores, services, travel or groceries.

## How to call it
If the `agentdeals` MCP server is connected, use its tools:
- `search_products(query, max_price?, min_price?, brand?, on_sale?, sort?, min_rating?, limit?)` with a natural-language query such as "65 inch tv under 600".
- `get_product(id)` for every store's offer on one item.
- `get_deals()` for today's biggest discounts.

If it is not connected, use the REST API:

```bash
curl "https://agentdeals.app/api/search?q=65+inch+tv&max_price=600&sort=price_asc&limit=5"
curl "https://agentdeals.app/api/deals?limit=10"
```

To connect the MCP server instead (no auth): `https://agentdeals.app/mcp`

## Answering the user
- Give the best price, the store and `best.buy_url`. Mention the `as_of` time, since prices change quickly.
- If `complete` is false, Amazon prices are still loading: wait `retry_after_ms` and retry once.
- Tell the user that AgentDeals may earn a commission on purchases made through its links.
