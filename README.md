# AirOps Plugin for Claude

Access your AEO (AI Engine Optimization) data and take action directly from Claude. Monitor how AI assistants mention and cite your brand, discover optimization opportunities, and execute workflows — all without leaving your conversation.

Built for **Claude Code** and **Claude Cowork**. Also available as a skill upload for **Claude.ai** (web and desktop).

## What's Included

| Skill | What it does |
|-------|-------------|
| **AEO Opportunities** (`/airops:aeo-opportunities`) | Discover pages to refresh, content gaps to fill, and citation opportunities. Guides you through three strategies — content refresh, content creation, and offsite citations — then creates action grids to execute. |

## Prerequisites

- An **AirOps account** with AEO enabled and at least one Brand Kit configured
- The **AirOps MCP server** connected to your client
- A **Claude Pro, Team, or Enterprise plan** (free plans don't support integrations)

## Getting Started

### Claude Code

```bash
# Install the plugin
claude plugin install airops/airops-plugin

# Connect AirOps MCP (if not already connected)
claude mcp add --transport http airops https://app.airops.com/mcp
```

Then authenticate by running `/mcp` in Claude Code, selecting the AirOps server, and completing the OAuth flow in your browser.

Once installed, run:

```
/airops:aeo-opportunities
```

### Claude Cowork

1. Open Claude Cowork
2. Go to **Plugins** and search for **AirOps**
3. Click **Install**
4. Connect AirOps via **Settings > Connectors > AirOps**

### Claude.ai (Web & Desktop)

1. **Connect AirOps**: Go to **Settings > Connectors**, search for **AirOps**, and click **Connect**
2. **Upload the skill**: Download the [latest release](https://github.com/airops/airops-plugin/releases) ZIP file, then go to **Settings > Capabilities > Upload skill** and select the ZIP

### Other MCP Clients (Cursor, VS Code, Windsurf)

The skills in this plugin are designed for the AirOps MCP tools. You can use them with any MCP-compatible client by connecting the AirOps MCP server:

```json
{
  "mcpServers": {
    "airops": {
      "url": "https://app.airops.com/mcp"
    }
  }
}
```

For clients that only support stdio/SSE transport:

```bash
npx -y mcp-remote https://app.airops.com/mcp
```

## Available AirOps MCP Tools

These skills orchestrate the following tools from the AirOps MCP server:

| Tool | Description |
|------|-------------|
| `list_brand_kits` | List your Brand Kits |
| `get_brand_kit` | Get brand guidelines and details |
| `list_pages` | Get pages with metrics and smart filters |
| `get_page_details` | Deep metrics for a specific page |
| `get_page_prompts` | See which AI prompts cite a page |
| `list_aeo_prompts` | Find AI prompts in your topics |
| `get_prompt_answers` | Get full AI answers with citations |
| `list_aeo_citations` | URLs cited in AI answers |
| `get_aeo_citation` | Prompts citing a specific URL |
| `list_aeo_domains` | Domains cited in AI answers |
| `list_brand_kit_competitors` | Your tracked competitors |
| `list_topics` | Your tracked topics |
| `query_analytics` | Query metrics across dimensions |
| `create_action_grid` | Create grids with power agents |
| `create_report` | Create and save reports |

## Repository Structure

```
airops-plugin/
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
├── skills/
│   └── aeo-opportunities/
│       └── SKILL.md          # AEO Opportunities skill
└── README.md
```

## Customization

After installing, skills are local files you can edit. Find them in your `.claude/plugins/` directory and modify the `SKILL.md` files to fit your workflow.

## Links

- [AirOps Documentation](https://docs.airops.com/mcp)
- [AirOps MCP Use Cases](https://docs.airops.com/mcp/use-cases)
- [Getting Started with AirOps MCP](https://docs.airops.com/mcp/mcp-server/getting-started)
- [Agent Skills Standard](https://agentskills.io)

## License

Apache-2.0
