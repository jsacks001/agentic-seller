# Gong MCP — Setup Guide

**What it unlocks:** Claude can pull your call transcripts directly from Gong and auto-debrief them.
Instead of pasting notes, just say "debrief my last call with [company]" and Claude reads the transcript.

**Repo:** `crmchattie/gong-mcp`
**Use if:** You record calls in Gong and want automatic call debriefs.

---

## Prerequisites

- A Gong account with API access enabled
- You must have an Admin or API user role in Gong

---

## Step 1 — Get your Gong API credentials

1. Log into Gong
2. Go to **Settings** → **API** (or ask your Gong admin to enable API access)
3. Create an API key pair: Access Key + Secret Key
4. Copy both — you'll need them in Step 3

---

## Step 2 — Add to .claude/mcp.json

Add this to your `mcpServers` section:

```json
"gong": {
  "command": "npx",
  "args": ["-y", "@crmchattie/gong-mcp"],
  "env": {
    "GONG_ACCESS_KEY": "your-access-key",
    "GONG_SECRET_KEY": "your-secret-key"
  }
}
```

---

## Step 3 — Test it works

Run Claude and type:
```
Pull transcript from my last call with [any company name from Gong]
```

Claude should return the transcript summary and offer to run a full call debrief.

---

## How it improves call-debrief

Without Gong MCP:
- You paste your notes into Claude
- Claude extracts qualification info from your notes

With Gong MCP:
- Claude pulls the full transcript directly
- No notes needed — just say "debrief my call with [company]"
- More complete capture — nothing gets lost

---

## Troubleshooting

**"No calls found":** Make sure the company name matches how Gong names the call. Try the contact's name instead.

**Authentication errors:** Verify both Access Key and Secret Key are correct. API access may need to be enabled by your Gong admin.
