[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/onsecurity-onsecurity-mcp-server-badge.png)](https://mseep.ai/app/onsecurity-onsecurity-mcp-server)

# OnSecurity MCP

A Model Context Protocol (MCP) server for the OnSecurity API that allows Claude to query rounds, findings, prerequisites and notifications.

## Installation

### Installing via Smithery

To install the server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@onsecurity/onsecurity-mcp-server):

```bash
npx -y @smithery/cli install @onsecurity/onsecurity-mcp-server --client claude
```

### Manual Installation

```bash
cd onsecurity-mcp-server
npm run build

```


Add the following to your Claude Desktop configuration file (adjust the paths as needed) and choose UAT or Prod:
```bash
{
  "mcpServers": {
    "onsec-mcp": {
      "command": "node",
      "args": [
        "/path/to/onsecurity-mcp-server/build/index.js"
      ],
      "env": {
        "ONSECURITY_API_TOKEN": "your_api_token",
        "ONSECURITY_API_BASE": "https://app.onsecurity.io/api/v2"
      }
    }
  }
}
```

After adding this configuration, restart Claude Desktop, and you'll be able to access the OnSecurity tools through Claude.

## Usage

Once configured, Claude will have access to the following tools:

- `get-rounds`
- `get-findings`
- `get-blocks`
- `get-notifications`
- `get-prerequisites`

#### Example Questions
- Give me a summary of my most recent pentest/scan.
- Show me trends across my pentests as a graph.
- What can I address to make the most impact most quickly on my most recent pentest?
- I would like summaries for different types of stakeholders on the state of our recent pentest engagemenets - eg high level, technical, managerial etc
- Do I need to action anything to prevent test getting held up?
- Are there any new findings?
- What are the top 10 most common findings across pentests and scans.


*Note: It is useful sometimes to configure Claude to "Extended thinking" for some questions.*
