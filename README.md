# AION Indian Market Intelligence MCP Server

Turn any Indian market headline into a signed sector-impact vector — the causal-context layer your LLM is missing.

**AION Analytics (India) — distinct from Polymathic's AION (astronomy), Aion Analytics LLC (United States), and aion-labs (Israel).**

**License: AGPL-3.0-or-later.** This MCP server (the wrapper in this repository) is open source and you can read every line of it. It calls a hosted API; the intelligence engine behind that API and the Python SDK (`aion-indian-market-intelligence`) are proprietary, and access to the API is by subscription.

---

The `analyze_news` tool gives any MCP-compatible agent structured sector-impact context for an Indian financial headline. Classification sits inside an auditable causal structure rather than a black box: every result carries the evidence behind it, a confidence score, and impacts that are signed rather than a single sentiment number. It also reads cultural and sovereign context, which conventional models underweight.

Fetch Indian market data with any MCP. Understand what it means with this one.

## Install

Run directly (no install required):

```bash
uvx aion-indian-market-intelligence-mcp
```

Or install permanently:

```bash
pip install aion-indian-market-intelligence-mcp
aion-indian-market-intelligence-mcp
```

## API Key

```bash
export AION_API_KEY="<your_api_key>"
```

Register: [dashboard.aiondashboard.site/access/register](https://dashboard.aiondashboard.site/access/register)

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

**Illustrative tool output shape:**

```json
{
  "sector_vector": {"example_sector": 0.0}
}
```

This is synthetic shape-only data, not an inference result or validation claim. The MCP wrapper returns only `sector_vector`; other SDK response fields are not passed through by this tool. Hosted analysis requires an API key.

## Compatible clients

Claude, ChatGPT, Gemini, Cursor, VS Code, Windsurf, Cline, and any MCP-compatible IDE or agent runtime.

## Links

- [Website model page](https://dashboard.aiondashboard.site/models/indian-market-intelligence)
- [API key registration](https://dashboard.aiondashboard.site/access/register)
- [MCP PyPI package](https://pypi.org/project/aion-indian-market-intelligence-mcp/)
- [Python client package](https://pypi.org/project/aion-indian-market-intelligence/)
- [HuggingFace Space demo](https://huggingface.co/spaces/AION-Analytics/aion-indian-market-intelligence)
