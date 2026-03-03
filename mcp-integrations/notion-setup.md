# Notion MCP — Setup Guide

**What it unlocks:** Pipeline management, task creation, contact tracking — all from Claude.
Claude can create tasks after calls, update deal stages, and add contacts without you ever opening Notion.

**Cost:** Free (Notion free plan is sufficient).
**Use if:** You want Claude to manage your pipeline and tasks. If you already use Salesforce or HubSpot, use those instead.

---

## Step 1 — Create a Notion workspace (if you don't have one)

Go to [notion.so](https://notion.so) and sign up. The free plan works.

---

## Step 2 — Create the 3 databases

You need 3 databases in Notion. Create them as full-page databases (not inline).

**Database 1: Pipeline**
Properties to add:
- Name (default) — account name
- Stage: Select — `Research / Outreach / Engaged / Discovery / Meeting Booked / Qualified / Closed`
- Value: Number — estimated deal value
- Next Action: Text
- Last Updated: Date

**Database 2: Tasks**
Properties to add:
- Name (default) — task description
- Status: Select — `To Do / In Progress / Done / Blocked`
- Priority: Select — `🔴 Urgent / 🟠 High / 🟡 Medium / 🟢 Low`
- Account: Text — which account this relates to
- Due Date: Date

**Database 3: Contacts**
Properties to add:
- Name (default) — contact name
- Title: Text
- Company: Text
- Email: Email
- LinkedIn: URL
- Status: Select — `Cold / Contacted / Warm / Champion`

---

## Step 3 — Get your database IDs

For each database:
1. Open the database in Notion
2. Click **Share** (top right) → **Copy link**
3. The link looks like: `https://notion.so/your-workspace/XXXXXXXXXXXXXXXX?v=...`
4. The database ID is the `XXXXXXXXXXXXXXXX` part (32 characters, no hyphens)

Save these 3 IDs — Claude will ask for them during onboarding.

---

## Step 4 — Create a Notion integration

1. Go to [notion.so/my-integrations](https://notion.so/my-integrations)
2. Click **New integration**
3. Name it "agentic-seller"
4. Select your workspace
5. Click **Submit**
6. Copy the **Internal Integration Token** (starts with `secret_...`)

---

## Step 5 — Connect your databases to the integration

For each of the 3 databases:
1. Open the database in Notion
2. Click **•••** (top right) → **Add connections**
3. Search for "agentic-seller" and click it

This gives Claude read/write access to those databases.

---

## Step 6 — Add to .claude/mcp.json

Add this to your `mcpServers` section in `.claude/mcp.json`:

```json
"notion": {
  "command": "npx",
  "args": ["-y", "@notionhq/notion-mcp-server"],
  "env": {
    "OPENAPI_MCP_HEADERS": "{\"Authorization\": \"Bearer secret_your_token_here\", \"Notion-Version\": \"2022-06-28\"}"
  }
}
```

Replace `secret_your_token_here` with your integration token.

---

## Step 7 — Complete onboarding

During onboarding, when Claude asks about your CRM, say "Notion".
Claude will ask for the 3 database IDs and fill them into `CLAUDE.md` automatically.

---

## Test it works

Ask Claude:
```
Create a task: "Research Acme Corp" due tomorrow, high priority
```

You should see the task appear in your Notion Tasks database.
