# AION Indian Market Intelligence MCP Server — sector-impact analysis for AI agents

[![MCP package on PyPI](https://img.shields.io/pypi/v/aion-indian-market-intelligence-mcp)](https://pypi.org/project/aion-indian-market-intelligence-mcp/) [![License: AGPL-3.0-or-later](https://img.shields.io/badge/license-AGPL--3.0--or--later-blue.svg)](LICENSE)

**Canonical publisher:** [AION Analytics (India) GitHub organization](https://github.com/AION-Analytics-India). [Hosted API plans and free key](https://aionanalytics.in/apis) · [API specification](https://aionanalytics.in/docs/api-reference.txt) · [Source and issues](https://github.com/AION-Analytics-India/aion-mcp-server).

Turn any Indian market headline into a signed sector-impact vector — the causal-context layer your LLM is missing.

**AION Analytics (India) — distinct from Polymathic's AION (astronomy), Aion Analytics LLC (United States), and aion-labs (Israel).**

**License: AGPL-3.0-or-later.** This MCP server (the wrapper in this repository) is open source and you can read every line of it. It calls a hosted API; the intelligence engine behind that API and the Python SDK (`aion-indian-market-intelligence`) are proprietary. Inference requires an API key; a limited free API plan is offered with quotas, alongside paid subscriptions. [Current plans](https://aionanalytics.in/apis).

---

The `analyze_news` tool returns the `sector_vector` from the hosted API for an Indian financial headline. It provides signed sector-impact context. The fuller REST API response is documented at https://aionanalytics.in/docs/api-reference.txt. This open-source wrapper does not distribute the proprietary inference engine.

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

Obtain a model-scoped key through the [current API catalogue](https://aionanalytics.in/apis) (choose Indian Market Intelligence). Registration and passkey verification are required; the free API plan does not require a payment card. The separate `/access/register` referral route is not for hosted API key registration.

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

Works with MCP clients that support stdio servers. The stdio initialization and tool-discovery handshake was tested; the Claude Desktop configuration above is an example, not a certification of every client.

## Contributing

The MCP server source is public under AGPL-3.0-or-later. To report a tool-schema, stdio-handshake or documentation defect, file a reproducible [GitHub issue](https://github.com/AION-Analytics-India/aion-mcp-server/issues) and remove keys, private headlines and personal data. Read the [contribution guidance](CONTRIBUTING.md) before sending a pull request. Changes to the wrapper do not grant access to the proprietary inference engine.

## Links

- [Official website model page](https://aionanalytics.in/models/indian-market-intelligence)
- [Current API catalogue and free-tier registration](https://aionanalytics.in/apis)
- [MCP PyPI package](https://pypi.org/project/aion-indian-market-intelligence-mcp/)
- [Python client package](https://pypi.org/project/aion-indian-market-intelligence/)
- [HuggingFace Space demo](https://huggingface.co/spaces/AION-Analytics/aion-indian-market-intelligence)
