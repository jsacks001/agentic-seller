# Salesforce MCP — Setup Guide

**What it unlocks:** CRM sync — read and write Salesforce records directly from Claude.
Claude can look up accounts, create tasks, log activities, and update opportunity stages.

**Repo:** `LokiMCPUniverse/mcp-servers`
**Use if:** Your CRM is Salesforce.

---

## What you need

- A Salesforce account (any edition: Essentials, Professional, Enterprise, or Unlimited)
- Your Salesforce username, password, and security token

---

## Step 1 — Get your security token

1. Log into Salesforce
2. Click your profile icon → **Settings**
3. In the left sidebar: **My Personal Information** → **Reset My Security Token**
4. Salesforce will email you a security token
5. Copy it — you'll need it in Step 3

---

## Step 2 — Get your Salesforce credentials

You need:
- **Username:** your Salesforce login email
- **Password:** your Salesforce login password
- **Security Token:** the token from Step 1

---

## Step 3 — Add to .claude/mcp.json

```json
"salesforce": {
  "command": "npx",
  "args": ["-y", "@loki-mcp-universe/salesforce-mcp"],
  "env": {
    "SALESFORCE_USERNAME": "your.email@company.com",
    "SALESFORCE_PASSWORD": "yourpassword",
    "SALESFORCE_TOKEN": "your-security-token"
  }
}
```

**⚠️ Security:** This file is already in `.gitignore`. Never share your `.claude/mcp.json`.

---

## Step 4 — During onboarding

When Claude asks "What CRM do you use?" → say "Salesforce".
Claude will use the Salesforce MCP to:
- Look up accounts and contacts
- Create tasks after call debriefs
- Log call activities
- Check for existing relationships before outreach

---

## Test it works

```
Look up [company name] in Salesforce
```

Claude should return the Account record.

---

## What Claude can do with Salesforce

- Look up Accounts, Contacts, Leads, Opportunities
- Create and update Tasks
- Log Activity (calls, emails)
- Update Opportunity stage
- Add Contacts from research

---

## Troubleshooting

**"Authentication failed":** Password + Security Token must be combined in some setups. Try `SALESFORCE_PASSWORD` = `yourpassword` + `securitytoken` (no space).

**"Object not found":** Salesforce object names vary by org (standard vs. custom). Ask your Salesforce admin if you have custom objects.

**IP restrictions:** Some Salesforce orgs restrict API access by IP. Ask your admin to whitelist your IP or use a connected app instead.

---

## Using a Connected App (more secure, for enterprises)

If your org has IP restrictions or you prefer OAuth:
1. In Salesforce Setup: create a Connected App with OAuth enabled
2. Get the Consumer Key and Consumer Secret
3. Use those instead of username/password/token

Ask your Salesforce admin for help with this setup if needed.
