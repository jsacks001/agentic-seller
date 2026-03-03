# Apollo.io MCP — Setup Guide

**What it unlocks:** 45 tools for contact search, enrichment, and sequence management.
Find verified email addresses, enrich contact records, and manage outreach sequences directly from Claude.

**Repo:** `Chainscore/apollo-io-mcp`
**Use if:** You use Apollo for contact enrichment or prospecting.

---

## Prerequisites

- An Apollo.io account (free plan includes limited searches)

---

## Step 1 — Get your Apollo API key

1. Log into [apollo.io](https://apollo.io)
2. Click your profile icon → **Settings**
3. Click **Integrations** → **API**
4. Click **Create new API key**
5. Copy the key

---

## Step 2 — Add to .claude/mcp.json

```json
"apollo": {
  "command": "npx",
  "args": ["-y", "@chainscore/apollo-io-mcp"],
  "env": {
    "APOLLO_API_KEY": "your-api-key-here"
  }
}
```

---

## Step 3 — Test it works

```
Find the CTO at acmecorp.com
```

Claude should return contact results from Apollo's database.

---

## Key capabilities

- Contact search by company, title, location
- Email verification
- Company enrichment (employee count, tech stack, revenue)
- Sequence management (if you run sequences in Apollo)

---

## Troubleshooting

**"Rate limit exceeded":** Apollo free plan has limited API calls per month. Upgrade if you need more volume.

**"Contact not found":** Apollo's database doesn't have every contact. Use Bright Data as a fallback for contacts Apollo doesn't have.
