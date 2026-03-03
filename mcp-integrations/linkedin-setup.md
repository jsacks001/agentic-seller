# LinkedIn MCP — Setup Guide

**What it unlocks:** LinkedIn profile data, company data, and job postings directly in Claude.

**Repo:** `stickerdaniel/linkedin-mcp-server` (★964)

**Note:** If you have Bright Data set up, it already handles most LinkedIn scraping needs (company pages, profiles, job postings). The LinkedIn MCP adds structured profile data and is useful for systematic contact research at scale.

---

## Prerequisites

- A LinkedIn account (Sales Navigator recommended for full access)
- LinkedIn credentials (email + password)

---

## Step 1 — Add to .claude/mcp.json

```json
"linkedin": {
  "command": "npx",
  "args": ["-y", "linkedin-mcp-server"],
  "env": {
    "LINKEDIN_EMAIL": "your-linkedin-email@example.com",
    "LINKEDIN_PASSWORD": "your-linkedin-password"
  }
}
```

**⚠️ Security note:** Your LinkedIn credentials go in `.claude/mcp.json`, which is already in `.gitignore`. Never commit this file.

---

## Step 2 — Test it works

```
Look up the LinkedIn profile of [contact name] at [company]
```

---

## What it adds vs. Bright Data

| Capability | Bright Data | LinkedIn MCP |
|------------|------------|--------------|
| Company page scraping | ✅ Full content | ✅ Structured data |
| Profile scraping | ✅ Works for public profiles | ✅ Works for connections |
| Job postings | ✅ Full description | ✅ Structured listing |
| Sales Navigator data | ❌ | ✅ With Sales Nav account |
| Connection data | ❌ | ✅ |

**Recommendation:** Set up Bright Data first. Add the LinkedIn MCP if you need structured profile data or Sales Navigator access.

---

## Troubleshooting

**Login fails:** LinkedIn may flag automated logins. Use a dedicated account or a LinkedIn developer app if rate limits become an issue.

**"Profile not found":** LinkedIn blocks scraping for private profiles. Use Bright Data's search to find publicly available information.
