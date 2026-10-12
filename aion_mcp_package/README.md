# aion-indian-market-intelligence-mcp

mcp-name: io.github.AION-Analytics-India/aion-indian-market-intelligence

MCP server wrapper for AION Indian Market Intelligence.

**AION Analytics (India) — distinct from Polymathic's AION (astronomy), Aion Analytics LLC (United States), and aion-labs (Israel).**

**License:** AGPL-3.0-or-later (this MCP wrapper). The hosted IMI engine behind the API and the Python SDK are proprietary; no model weights are distributed.

---

The `analyze_news` MCP tool sends one Indian financial headline to the hosted AION API and returns the `sector_vector` from the API response: a signed impact for each sector. This package does not bundle a local engine, model weights, taxonomy files, rule files, or private inference logic.

Use it when an MCP-compatible agent already has a headline from another source and needs to know which Indian market sectors an event is likely to move, and in which direction. The full API response (which also carries a confidence score and further context) is available through the REST API and the Python client; see the API reference linked below.

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

Hosted API keys are issued with a plan, including a free plan. Choose one at: `https://aionanalytics.in/apis` (the page lists the current limits).

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
  "headline": "RBI hikes repo rate by 25 bps",
  "published_at": "2026-06-05T10:00:00+05:30"
}
```

**Output:** the tool returns one field, `sector_vector`, mapping each of the 32 AION taxonomy sectors to a signed impact. The example is abbreviated: a real response lists all 32 sectors, and sectors with no modelled impact are `0.0`. Values below are from a real response to the headline above.

```json
{
  "sector_vector": {
    "Banks": -0.5693,
    "Financial Services": -0.5693,
    "NBFC": -0.5693,
    "Automobile and Auto Components": -0.5693,
    "Realty": -0.6188,
    "FMCG": -0.4455,
    "IT": 0.3465,
    "...": 0.0
  }
}
```

Negative is adverse, positive is favourable, `0.0` is no modelled impact. This tool returns only `sector_vector`; the fuller response (confidence, macro signal, top-sector summaries, stakeholder views) comes from the REST API (`POST https://api.aionanalytics.in/v1/analyze`, see the API reference) or the Python client.

## Scope

- One text headline per request.
- The wrapper is request/response over MCP stdio by default.
- The caller supplies news, regulatory, or market headlines.
- This package does not ingest feeds, parse PDFs, parse filings, stream updates, or place orders.

## Discovery terms

Indian stock market news API, NSE sector impact API, headline-to-context, RBI policy impact API, event-driven market intelligence India, Nifty sector exposure context, sector exposure API India, cyclone/monsoon market impact, LLM tool for Indian equities, financial event intelligence, MCP server, Python SDK.

## Links

- Model page: `https://aionanalytics.in/models/indian-market-intelligence`
- API key (plans, including a free plan): `https://aionanalytics.in/apis`
- API reference: `https://aionanalytics.in/docs/api-reference.txt`
- PyPI client: `https://pypi.org/project/aion-indian-market-intelligence/`

## Not investment advice

The API provides market-intelligence context. Execution decisions remain with you.
