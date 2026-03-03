# HubSpot MCP — Setup Guide

**What it unlocks:** CRM sync — read and write contacts, deals, tasks, and notes in HubSpot.
Claude can update deal stages, log call notes, and create follow-up tasks without you opening HubSpot.

**Repo:** `LokiMCPUniverse/mcp-servers`
**Use if:** Your CRM is HubSpot.

---

## Step 1 — Get your HubSpot API key

**Option A: Private App token (recommended)**
1. Log into HubSpot → click your profile icon → **Account Settings**
2. Go to **Integrations** → **Private Apps**
3. Click **Create a private app**
4. Name it "agentic-seller"
5. Under **Scopes**, select: `crm.objects.contacts.read/write`, `crm.objects.deals.read/write`, `crm.objects.notes.read/write`
6. Click **Create app** → copy the access token

**Option B: API Key (legacy)**
1. Go to **Settings** → **Account Setup** → **Integrations** → **API Key**
2. Click **Show Key** and copy it

---

## Step 2 — Add to .claude/mcp.json

```json
"hubspot": {
  "command": "npx",
  "args": ["-y", "@loki-mcp-universe/hubspot-mcp"],
  "env": {
    "HUBSPOT_ACCESS_TOKEN": "your-access-token-here"
  }
}
```

---

## Step 3 — During onboarding

When Claude asks "What CRM do you use?" → say "HubSpot".
Claude will use the HubSpot MCP to:
- Create tasks after call debriefs
- Log call notes to contact records
- Update deal stages

---

## Test it works

```
Look up [company name] in my CRM
```

Claude should return the HubSpot record for that company.

---

## What Claude can do with HubSpot

- Read contact and company records
- Create + update tasks (after call debrief or outreach)
- Log call notes to contact records
- Update deal stages
- Add contacts from research

---

## Troubleshooting

**"Contact not found":** The company might not be in HubSpot yet. Ask Claude to create the record first.

**Permission errors:** Make sure the private app has the required scopes (see Step 1).
