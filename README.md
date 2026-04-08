# Mixpanel MCP Marketplace

Open-source plugins and skills for [Mixpanel](https://mixpanel.com) MCP users. Turn your AI coding assistant into a product manager and analytics powerhouse.

Works with **Claude**, **Claude Code**, **Cursor**, and **Codex**.

---

## What's Inside

| Plugin                            | Description                                                                                                                                                               |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [mixpanel](./plugins/mixpanel/) | Reusable analysis and instrumentation skills covering reports, boards, experiments, session replays, data governance, and analytics tracking workflows |

---

## Mixpanel Plugin

The mixpanel plugin turns your AI assistant into an expert product analyst and instrumentation partner. Skills are organized into seven areas:

### Core Analytics

| Skill               | What it does                                                                 |
| ------------------- | ---------------------------------------------------------------------------- |
| `create-report`      | Creates Mixpanel reports (Insights, Funnels, Flows, etc.) from natural language descriptions                  |
| `create-board`  | Builds boards from requirements, organizing reports into logical sections |
| `analyze-report`     | Deep-dives a report to explain trends, anomalies, and likely drivers          |
| `analyze-board` | Reviews a board end-to-end, surfacing key takeaways and areas of concern |

### Product Insights

| Skill                    | What it does                                                                                   |
| ------------------------ | ---------------------------------------------------------------------------------------------- |
| `analyze-experiment`     | Designs A/B tests, monitors running experiments, and interprets results                        |
| `monitor-experiments`    | Triages all active and recently completed experiments by importance                            |
| `analyze-feedback`       | Synthesizes customer feedback into themes — feature requests, bugs, pain points, praise        |
| `discover-opportunities` | Finds product opportunities by cross-referencing analytics, experiments, replays, and feedback |
| `compare-user-journeys`  | Compares two user groups side-by-side to surface behavioral differences                        |

### Session Replay & Debugging

| Skill                 | What it does                                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------------------------------- |
| `debug-replay`        | Turns bug reports into numbered reproduction steps by extracting the interaction timeline from Session Replay |
| `replay-ux-audit`     | Watches multiple session replays for a flow and synthesizes a ranked friction map                             |

### Analytics Instrumentation

| Skill                           | What it does                                                                                                  |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `diff-intake`                   | Reads a PR or branch diff and outputs a structured `change_brief` YAML for downstream skills                  |
| `discover-event-surfaces`       | From a change brief, lists candidate analytics events for PM prioritization                                   |
| `discover-analytics-patterns`   | Maps how analytics is already implemented in the repo (SDK calls, naming, imports)                            |
| `instrument-events`             | From prioritized event candidates, builds a concrete instrumentation plan and JSON tracking plan              |
| `add-analytics-instrumentation` | End-to-end workflow — reads code, decides what to track, and produces a full instrumentation plan in one pass |

A typical flow: `diff-intake` → `discover-event-surfaces` → `instrument-events`, with `discover-analytics-patterns` ensuring new tracking matches existing conventions.

### Data Governance

| Skill          | What it does                                                                  |
| -------------- | ----------------------------------------------------------------------------- |
| `audit-lexicon`  | Reviews Lexicon for data quality issues, missing descriptions, and inconsistencies |
| `update-lexicon` | Bulk updates event/property descriptions and tags in Lexicon |

### Briefings

| Skill          | What it does                                                                  |
| -------------- | ----------------------------------------------------------------------------- |
| `daily-brief`  | Morning briefing of the most important changes across your Mixpanel instance |
| `weekly-brief` | Weekly recap of trends, wins, and risks to share with your team or leadership |

---

## Quick Start

### Claude Code

```bash
# Add the Mixpanel marketplace (one-time)
/plugin marketplace add rpatel05/mcp-marketplace

# Install the plugin
/plugin install mixpanel@mixpanel
```

### Cursor

1. Go to Cursor Settings > Plugins
2. Search for the **Mixpanel Analytics** plugin and install it
3. Verify the skills are available by typing `/`
4. Add the Mixpanel MCP server: Settings > Agent > Tools & MCP > Add MCP Server
5. Use this config:

```json
"mixpanel": {
    "command": "npx",
    "args": [
        "-y",
        "@mixpanel/mcp-server"
    ]
}
```

6. Complete the OAuth flow in the browser when prompted

---

## Repository Structure

```text
.claude-plugin/
  marketplace.json            # Marketplace catalog
plugins/
  mixpanel/
    .claude-plugin/
      plugin.json             # Plugin manifest
    skills/
      add-analytics-instrumentation/
      analyze-board/
      analyze-experiment/
      analyze-feedback/
      analyze-report/
      audit-lexicon/
      compare-user-journeys/
      create-board/
      create-report/
      daily-brief/
      debug-replay/
      diff-intake/
      discover-analytics-patterns/
      discover-event-surfaces/
      discover-opportunities/
      instrument-events/
      monitor-experiments/
      replay-ux-audit/
      update-lexicon/
      weekly-brief/
```

---

## Requirements

- **MCP-compatible client** – Claude Code, Cursor, Claude, and Codex
- **Mixpanel account** with API access
- **Node.js** – for the MCP server

---

## Contributing

We welcome contributions! Whether it's a new skill or improvement:

1. Fork this repo
2. Create a new branch for your feature
3. Follow the existing patterns in `plugins/` for structure
4. Submit a PR with a clear description

---

## Resources

- [Mixpanel Docs](https://docs.mixpanel.com)
- [MCP Protocol](https://modelcontextprotocol.io/)

---

## License

MIT

---

## Support

- **Issues**: [GitHub Issues](https://github.com/rpatel05/mcp-marketplace/issues)
- **Mixpanel**: [mixpanel.com](https://mixpanel.com)
