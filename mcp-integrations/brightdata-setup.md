# Bright Data MCP — Setup Guide

**What it unlocks:** Full research mode — scrape complete LinkedIn profiles, company pages,
engineering blogs, job postings, Reddit threads, news articles, press releases.
Without it, you're in lite mode (search results only — no page content).

**Cost:** ~$10/month (pay-as-you-go). Free trial available.

---

## Step 1 — Create a Bright Data account

1. Go to [brightdata.com](https://brightdata.com)
2. Click "Start free trial" — no credit card required for trial
3. Complete signup

---

## Step 2 — Get your API token

1. Log into your Bright Data dashboard
2. Click your profile icon (top right) → **Settings**
3. Click **API Tokens** in the left sidebar
4. Click **Add Token**
5. Give it a name (e.g., "agentic-seller") and copy the token

Your token looks like: `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

---

## Step 3 — Add to your MCP config

1. If you haven't already, copy the template:
   ```bash
   cp .claude/mcp.json.template .claude/mcp.json
   ```

2. Open `.claude/mcp.json` in any text editor (TextEdit on Mac, Notepad on Windows)

3. Replace `YOUR_BRIGHTDATA_API_TOKEN_HERE` with your actual token:
   ```json
   {
     "mcpServers": {
       "brightdata": {
         "command": "npx",
         "args": ["-y", "@brightdata/mcp"],
         "env": {
           "API_TOKEN": "your-actual-token-here"
         }
       }
     }
   }
   ```

4. Save the file

---

## Step 4 — Test it works

Run Claude and type:
```
research brightdata.com
```

If Bright Data is working, you'll see Claude scraping full page content (not just search snippets).
If still in lite mode, you'll see "⚠️ Lite mode" in the research output.

---

## Troubleshooting

**"Lite mode" even after setup:** Check that `.claude/mcp.json` exists (not just the template). Verify the file has valid JSON (no extra commas or missing brackets).

**Token errors:** Make sure you copied the full token without extra spaces. Tokens are case-sensitive.

**Rate limiting:** Bright Data has usage limits. If you hit them, the research will fall back to lite mode automatically.

---

## What changes with Bright Data

| Task | Without Bright Data | With Bright Data |
|------|--------------------|--------------------|
| Research | Search snippets only | Full page content scraped |
| LinkedIn profiles | Name + title from search | Full profile with summary, experience, recent activity |
| Job postings | Title + company from search | Full job description with tech stack details |
| Company blog | URL from search | Full article text |
| Competitors' sites | URL from search | Full page content |
