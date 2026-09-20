# aion-indian-market-intelligence-mcp

mcp-name: io.github.AION-Analytics-India/aion-indian-market-intelligence

MCP server wrapper for AION Indian Market Intelligence.

**AION Analytics (India) — distinct from Polymathic's AION (astronomy), Aion Analytics LLC (United States), and aion-labs (Israel).**

**License:** AGPL-3.0-or-later (this MCP wrapper). The hosted IMI engine behind the API and the Python SDK are proprietary; no model weights are distributed.

---

The `analyze_news` MCP tool sends one Indian financial headline to the hosted AION API and returns the public API response. This package does not bundle a local engine, model weights, taxonomy files, rule files, or private inference logic.

Use it when an MCP-compatible agent already has a headline from another source and needs structured Indian market context: event metadata, confidence, market context, `sector_vector`, sector exposure summaries, stakeholder views, and assignment metadata when available.

## Install

Run directly with `uvx`:

```bash
uvx aion-indian-market-intelligence-mcp
```

Or install permanently:

```bash
pip install aion-indian-market-intelligence-mcp
aion-indian-market-intelligence-mcp
```

## API key

```bash
export AION_API_KEY="<your_api_key>"
```

Register at: `https://dashboard.aiondashboard.site/access/register`

## Claude Desktop

```json
{
  "mcpServers": {
    "aion-indian-market-intelligence": {
      "command": "uvx",
      "args": ["aion-indian-market-intelligence-mcp"],
      "env": {
        "AION_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

## Tool: analyze_news

**Input:**

```json
{
  "headline": "RBI MPC holds repo rate at 6.50% — June 2026",
  "published_at": "2026-06-05T10:00:00+05:30"
}
```

**Output shape:**

```json
{
  "headline": "RBI MPC holds repo rate at 6.50% — June 2026",
  "event": "monetary_policy",
  "confidence": 0.91,
  "macro_signal": "neutral",
  "vix_regime": "normal",
  "sector_vector": {
    "Banking & Financial Services": 0.38,
    "NBFCs": 0.14,
    "Real Estate": -0.44,
    "IT Services": -0.21,
    "FMCG": 0.09
  },
  "top_positive_sectors": ["Banking & Financial Services", "NBFCs"],
  "top_negative_sectors": ["Real Estate", "IT Services"],
  "stakeholder_views": {
    "producer_view": {},
    "trader_intermediary_view": {},
    "investor_view": {},
    "government_fiscal_view": {},
    "international_trade_view": {}
  }
}
```

`sector_vector` is the canonical sector-impact output. `top_positive_sectors` and `top_negative_sectors` provide compact sector exposure summaries for agent workflows.

## Scope

- One text headline per request.
- The wrapper is request/response over MCP stdio by default.
- The caller supplies news, regulatory, or market headlines.
- This package does not ingest feeds, parse PDFs, parse filings, stream updates, or place orders.

## Discovery terms

Indian stock market news API, NSE sector impact API, headline-to-context, RBI policy impact API, event-driven market intelligence India, Nifty sector exposure context, sector exposure API India, cyclone/monsoon market impact, LLM tool for Indian equities, financial event intelligence, MCP server, Python SDK.

## Links

- Model page: `https://dashboard.aiondashboard.site/models/indian-market-intelligence`
- API key: `https://dashboard.aiondashboard.site/access/register`
- PyPI client: `https://pypi.org/project/aion-indian-market-intelligence/`

## Not investment advice

The API provides market-intelligence context. Execution decisions remain with you.
