# MCP Integrations — What's Available and When to Use Each

MCP (Model Context Protocol) servers are plugins that give Claude Code access to external tools and data.
Without them, Claude can only read files and do basic web searches.
With them, Claude can read your CRM, search LinkedIn, pull call transcripts, scrape full pages, and more.

---

## Required vs. Optional

| MCP | Required? | What you lose without it |
|-----|-----------|--------------------------|
| **Bright Data** | Strongly recommended | Research drops to lite mode — search results only, no page content, no LinkedIn profiles |
| Notion | Optional | No pipeline/tasks/contacts management (use your existing CRM instead) |
| HubSpot / Salesforce | Optional | No CRM sync — Claude outputs paste-ready CRM update blocks instead |
| Apollo | Optional | No contact enrichment — find contacts manually |
| LinkedIn | Optional | No profile scraping — Bright Data handles most LinkedIn needs already |
| Gong | Optional | No auto-debrief from transcripts — paste notes manually |

---

## Setup Priority

**Do in this order:**

1. **Bright Data** — most impactful, affects every research session
2. **Your CRM** (HubSpot, Salesforce, or Notion) — needed for task creation and pipeline sync
3. **Gong** — if you record calls, this is powerful (auto-debrief from transcript)
4. **Apollo** — if you do contact enrichment
5. **LinkedIn** — usually covered by Bright Data already

---

## Quick Comparison

| MCP | Key capability | Stars / Repo |
|-----|---------------|-------------|
| Bright Data | Full web scraping — LinkedIn, job boards, news, Reddit | Official MCP |
| Notion | Pipeline + Tasks + Contacts databases | Official MCP |
| HubSpot | CRM contacts, deals, tasks | `LokiMCPUniverse/mcp-servers` |
| Salesforce | CRM contacts, opportunities, activities | `LokiMCPUniverse/mcp-servers` |
| Apollo.io | Contact search + enrichment + 45 tools | `Chainscore/apollo-io-mcp` |
| LinkedIn | Profile + company + job data | `stickerdaniel/linkedin-mcp-server` (★964) |
| Gong | Call transcript retrieval | `crmchattie/gong-mcp` |

---

## The onboarding auto-discovery

During onboarding (when you first run `claude`), Claude will ask you which sales tools you use.
For each one you mention, Claude searches for an MCP and reports back:

> "Found a Gong MCP (★X stars, Y tools available). Found an Apollo MCP (45 tools).
> No MCP exists yet for [tool] — you'll use it manually for now."

Claude then offers to add each found MCP to your `.claude/mcp.json` and walks you through adding the API key.
You don't need to read the setup guides below unless you want to do it manually.

---

## Setup Guides

| File | MCP |
|------|-----|
| `brightdata-setup.md` | Bright Data — start here |
| `notion-setup.md` | Notion pipeline + tasks |
| `apollo-setup.md` | Apollo contact enrichment |
| `linkedin-setup.md` | LinkedIn profiles |
| `gong-setup.md` | Gong call transcripts |
| `hubspot-setup.md` | HubSpot CRM sync |
| `salesforce-setup.md` | Salesforce CRM sync |

---

## Adding any MCP manually

All MCPs follow the same pattern in `.claude/mcp.json`:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "@package/name"],
      "env": {
        "API_KEY": "your-key-here"
      }
    }
  }
}
```

The exact config block for each MCP is in its setup guide.
Your `.claude/mcp.json` is already in `.gitignore` — your API keys won't be committed to GitHub.
