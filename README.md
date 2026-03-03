# agentic-seller

> "The best AI tools are limited to software engineers while most knowledge workers only have ChatGPT."

> "Non-technical teams across sales, marketing, legal, and operations gain the ability to automate workflows and build tools with little or no engineering intervention." — Anthropic 2026 Agentic Coding Trends Report

---

**agentic-seller** turns Claude Code into a fully personalized B2B selling system.
Clone it, answer 9 questions, and run your first account research in under 30 minutes — no coding required.

---

## What you need

| Item | Required? | Cost |
|------|-----------|------|
| [Claude Code](https://claude.ai/code) | Yes | Free to install |
| Anthropic API key | Yes | ~$5–20/month |
| [Bright Data](https://brightdata.com) | Strongly recommended | ~$10/month (free trial) |
| Notion workspace | Optional | Free |

---

## 4-step setup

```bash
# 1. Install Claude Code
npm install -g @anthropic-ai/claude-code
export ANTHROPIC_API_KEY=your_key_here

# 2. Clone this repo
git clone https://github.com/YOUR_HANDLE/agentic-seller
cd agentic-seller

# 3. Set up Bright Data (see mcp-integrations/brightdata-setup.md)
cp .claude/mcp.json.template .claude/mcp.json
# Add your Bright Data API key to .claude/mcp.json

# 4. Run Claude
claude
```

---

## The onboarding experience

When you first run `claude`, it detects it hasn't been configured and asks you 9 questions in plain English:

1. Your name and role
2. Your company and what you sell
3. Your ideal customer
4. Your qualification framework (MEDDPICC, BANT, SPIN, SPICED, or custom)
5. Your CRM
6. Other sales tools you use → **Claude searches for MCPs for each one automatically**
7. Bright Data → **Claude explains full vs. lite mode and offers to set it up**
8. Your top competitors
9. Your proof points

After you answer, Claude fills in your personal workspace, connects your tools, and says:
> "You're set up. Ready to research your first account? Just say: `research [company name]`"

---

## Your first command

```
research [your first target company]
```

---

## The 8 skills

| Skill | Trigger | What it does |
|-------|---------|--------------|
| `/prospect-research` | "research [company]", "deep scan" | Internal knowledge + web research → research file + account-brief |
| `/write-outreach` | "write outreach for [contact]", "cold email" | Research file → SPARK framework → LI + InMail + email + cold call |
| `/discovery-prep` | "prep me for [company]", "meeting brief" | Prior intel + fresh search → meeting brief + qualification gap analysis |
| `/call-debrief` | "just got off a call with [company]" | Notes → qualification map → follow-up email → updated brief |
| `/objection-mining` | "objection library", "what are they pushing back on" | Aggregate call objections → build response library |
| `/social-selling` | "linkedin plan for [company]", "warm path" | Engagement ladder → weekly social plan |
| `/signal-scoring` | "territory health", "what's hot" | Scan territory → weight by ICP fit → prioritized action list |
| `/icp-matrix-builder` | "score [company] on ICP", "tier this account" | 5-dimension ICP scoring → tier assignment |

---

## MCP stack

| MCP | Required? | What it adds |
|-----|-----------|-------------|
| **Bright Data** | Strongly recommended | Full web scraping — LinkedIn, job boards, news, Reddit |
| Notion | Optional | Pipeline + tasks + contacts management |
| HubSpot | Optional | CRM sync — contacts, deals, tasks |
| Salesforce | Optional | CRM sync — enterprise |
| Apollo.io | Optional | Contact enrichment + sequences |
| LinkedIn | Optional | Profile + company data |
| Gong | Optional | Auto-debrief from call transcripts |

See `mcp-integrations/` for setup guides. Or let Claude find them during onboarding.

---

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        CLAUDE.md                            │
│  (your personalized brain — filled in by onboarding)        │
│  name, company, ICP, framework, CRM, competitors            │
└──────────────────────┬──────────────────────────────────────┘
                       │ loads context every session
                       ▼
┌─────────────────────────────────────────────────────────────┐
│                     .claude/skills/                         │
│                                                             │
│  prospect-research  →  write-outreach                       │
│  call-debrief      →  objection-mining                      │
│  icp-matrix-builder →  signal-scoring                       │
│  discovery-prep       social-selling                        │
└──────────────────────┬──────────────────────────────────────┘
                       │ reads/writes
                       ▼
┌─────────────────────────────────────────────────────────────┐
│                    File system                              │
│                                                             │
│  accounts/{company}/                                        │
│  ├── account-brief.md    ← living qualification state       │
│  ├── research/           ← dated research snapshots         │
│  ├── discovery/          ← call notes                       │
│  ├── meetings/           ← meeting briefs                   │
│  └── emails/             ← outreach (gitignored)            │
│                                                             │
│  memory/                                                    │
│  ├── account-intel.md    ← persistent cross-account intel   │
│  ├── objection-library.md                                   │
│  ├── territory-signals.md                                   │
│  └── icp-matrix.md                                          │
└──────────────────────┬──────────────────────────────────────┘
                       │ live data via MCPs
                       ▼
┌─────────────────────────────────────────────────────────────┐
│                    MCP servers                              │
│  Bright Data (web research)  │  CRM (Salesforce/HubSpot/    │
│  Notion (tasks/pipeline)     │    Notion)                   │
│  Apollo (contacts)           │  Gong (transcripts)          │
│  LinkedIn (profiles)         │  + auto-discovered tools     │
└─────────────────────────────────────────────────────────────┘
```

---

## Examples

See `examples/acme-corp/` for a complete worked example showing:
- `account-brief.md` — filled qualification table, deal stage, contacts, next actions
- `research/2026-01-15-initial-research.md` — full research output format

---

## Built on

[anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) (★8,482) — the meta-framework for AI-powered knowledge work.

`agentic-seller` is the opinionated B2B sales layer built on top.

---

## Contributing

This is an open-source project for sellers, built by sellers.
Issues, pull requests, and skill contributions welcome.

Skills are compatible with [agentskills.io](https://agentskills.io) — the open standard for agent skills across 37+ platforms.
