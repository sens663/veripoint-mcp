# Veripoint MCP

Research private and public company financials, inspect supporting evidence and retrieve saved workspace reports from an AI assistant.

Veripoint is a hosted MCP service. This repository contains its connection examples, public registry metadata and tool schemas. The service is operated at [veripoint.ai](https://veripoint.ai).

## Connect

- Transport: Streamable HTTP
- OAuth endpoint: `https://veripoint.sens663.chatgpt.site/mcp`
- Setup guide: [Veripoint MCP setup](https://veripoint.ai/api-docs/mcp-setup)
- Official registry name: `ai.veripoint/mcp`
- Metadata version: `1.1.0`

Create or sign in to your Veripoint workspace. Link an active workspace key at [MCP workspace linking](https://veripoint.sens663.chatgpt.site/mcp-link), then authorize the connection through your MCP client's OAuth flow. Revoking or expiring the linked key removes access.

For clients that read `mcpServers`, use:

```json
{
  "mcpServers": {
    "veripoint": {
      "url": "https://veripoint.sens663.chatgpt.site/mcp"
    }
  }
}
```

See [Cursor configuration](client-configs/cursor-mcp.json) and [VS Code configuration](client-configs/vscode-mcp.json) for client-specific formats. OAuth support is required; configuration examples do not certify every client or version.

API-key clients can instead use `https://veripoint.ai/api/mcp` with an `Authorization: Bearer` header as described in the setup guide. Keep keys in your client's secure credential storage; never commit them to a repository or publish them in a directory.

## Tools

| Tool | Purpose | Research allowance |
|---|---|---|
| `research_company` | Research a named company or compare companies; save the completed analysis with evidence | A completed analysis consumes a workspace search |
| `list_reports` | Find existing reports in the authorized workspace | Does not consume searches |
| `get_report` | Retrieve a saved report, evidence and financial-statement datasets | Does not consume searches |
| `get_usage` | Check the workspace plan, remaining searches and reset date | Does not consume searches |

See [tool-schemas.json](tool-schemas.json) for exact input schemas and annotations. Research can create saved reports; the other three tools read workspace information.

## Example questions

- Analyse Microsoft Corporation (MSFT), United States. Show available annual statements with reporting periods, currency, company scope and evidence.
- Compare two named suppliers in the same jurisdiction. Align reporting years and currencies and identify missing figures.
- Find my saved report about a company before running another analysis.

Financial coverage varies by company, jurisdiction and reporting period. Missing values remain unavailable. Identify the legal entity and country in your question; clarify ambiguous matches before relying on the analysis.

## Public metadata

- [Official MCP Registry entry](https://registry.modelcontextprotocol.io/v0.1/servers/ai.veripoint%2Fmcp/versions/latest)
- [Published registry manifest](server.json)
- [Server card](server-card.json)

The official registry entry is active. Registry registration and source schemas do not establish successful authentication in every external client. Follow the setup guide and verify your client connection before production use.

## Product and support

[Veripoint](https://veripoint.ai) · [MCP setup guide](https://veripoint.ai/api-docs/mcp-setup)
