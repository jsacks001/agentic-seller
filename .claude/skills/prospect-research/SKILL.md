---
name: prospect-research
description: |
  Full account research sweep. Uses internal knowledge + live web data to build research file and account-brief.
  Use when: researching a new account, refreshing intel before outreach, understanding tech stack,
  finding the right contacts, identifying buying signals, or building an account-brief.
  Triggers: research, scan, deep scan, intel, company overview, tech stack, who should I target,
  find contacts, what do we know about, prospect, account brief, initial research, new account,
  add account, what's the hook.
version: 1.0.0
user-invocable: true
---

# Prospect Research

**⚠️ DATA RULE:** Never trust pre-training knowledge for current company state. Always pull live data.
Pre-training is stale. Internal knowledge first → web research second → synthesize third.

**⚠️ DATE RULE:** Check `currentDate` from context before creating any file. All files named `YYYY-MM-DD-{topic}.md`.

---

## STEP 0 — Confirm Account and Goal

Before any research:
1. Confirm the account name (exact spelling — this becomes the folder path in kebab-case)
2. Is this initial research or a refresh?
3. Check if `accounts/{account-name}/` already exists
4. Check if `account-brief.md` already exists

If no folder exists → create the structure now:
```
accounts/{account-name}/
├── account-brief.md        ← Create skeleton from _TEMPLATE
├── research/
├── discovery/
├── meetings/
└── emails/
```

---

## STEP 1 — Internal Knowledge First

Check what already exists before going to the web:

**CRM (if MCP configured):**
- Search for existing relationship, open opportunities, past interactions
- Pull any contact records for the account

**Local files:**
- `accounts/{account-name}/` — prior research files, call notes, meeting briefs
- `knowledge/competitive/` — relevant battlecards
- `knowledge/personas/` — ICP persona guides

**What to look for:**
- [ ] Existing CRM relationship / opportunity status
- [ ] Known contacts + roles
- [ ] Previous engagement history
- [ ] Relevant prior research findings

---

## STEP 2 — Web Research

**Detect mode first:** Check if `mcp__brightdata__*` tools are available.

### FULL MODE (Bright Data available)

Run in parallel via `mcp__brightdata__search_engine_batch`:
```
Query 1: "{Company} tech stack {{SOLUTION_CATEGORY}} 2025 2026"
Query 2: "{Company} engineering hiring jobs 2026"
Query 3: "{Company} news funding announcement 2026"
Query 4: "{Company} CTO VP Engineering Chief Architect"
Query 5: "{Company} {{SOLUTION_CATEGORY}} challenge problem pain"
Query 6: "{Company} AI machine learning 2026"
Query 7: "{{COMPANY_NAME}} {Company industry} case study customer"

--- Deep Signal Layer (always run) ---
Query 8:  "{Company} engineering blog AI machine learning 2026"
Query 9:  "{Company} AI conference talk keynote 2025 2026"
Query 10: "{Company} hiring AI engineer vector LLM RAG embedding 2026"
Query 11: "{Company} {CTO/VP name} blog post LinkedIn article 2026"
```

Then scrape for depth:
- Company website → About, Engineering, Careers pages
- Recent blog posts (prioritize AI/engineering content)
- Press releases from last 90 days
- LinkedIn company page (if accessible)

### LITE MODE (no Bright Data — WebSearch fallback)

```
1. "{Company} tech stack 2026"
2. "{Company} CTO VP Engineering LinkedIn"
3. "{Company} news funding 2026"
4. "{Company} {{SOLUTION_CATEGORY}} use case"
5. "{Company} engineering blog AI"
```

**Note in output:** "⚠️ Lite mode — search results only, no page scraping. Lower signal quality."

**Key signals to find:**
- [ ] Confirmed tech stack (databases, cloud provider, languages, tools)
- [ ] Engineering headcount and growth trajectory
- [ ] AI/ML initiatives — what are they building specifically?
- [ ] Recent funding, product launches, leadership changes
- [ ] Engineering leadership names, titles, any recent changes
- [ ] People publishing publicly about AI, data, or {{SOLUTION_CATEGORY}}
- [ ] Job postings mentioning specific tools → reveals architecture decisions

---

## STEP 3 — FITS Scoring

Score the account before writing the research file:

| Dimension | Score (0–25) | What to assess |
|-----------|-------------|----------------|
| **F — Firmographic Fit** | /25 | Industry, company size, stage, headcount match {{ICP_DESCRIPTION}} |
| **I — Intent Signals** | /25 | Active hiring, product launch, funding, leadership change, competitor eval |
| **T — Timing** | /25 | Urgency window — is there a forcing function? Fiscal year end? Launch date? |
| **S — Solution Match** | /25 | Is their confirmed pain solvable by {{PRODUCT_NAME}}? |

**Total FITS Score:** /100
- 80+: Tier 1 — prioritize immediately
- 60–79: Tier 2 — strong, worth outreach
- 40–59: Tier 3 — possible, lower priority
- Below 40: Tier 4 — stretch, deprioritize

---

## STEP 4 — Synthesize and Save

**Output path:** `accounts/{account-name}/research/{YYYY-MM-DD}-initial-research.md`
(Refresh: `{YYYY-MM-DD}-research-update.md`)

### Required sections (chain interface — write-outreach reads these):

```markdown
# {Company} — Research
**Date:** {YYYY-MM-DD} | **Mode:** Full / Lite

---

## 2026 Key Signals
[Fresh, time-sensitive findings. Lead with the most recent.]

## Company Overview
[2-3 sentences: what they do, size, stage, HQ]

## Tech Stack (Confirmed)
| System | Technology | Source |
|--------|-----------|--------|

## Leadership Contacts
| Name | Title | Relevance | Source |
|------|-------|-----------|--------|

## People Publishing About AI / {{SOLUTION_CATEGORY}}
| Name | Title | Topic | Link | Why It Matters |
|------|-------|-------|------|----------------|

## AI / {{SOLUTION_CATEGORY}} Job Postings
| Role | Tools Mentioned | Posted | Implication |
|------|----------------|--------|-------------|

## Pain Signals (Research-Confirmed)
1. [Pain] → Source: [URL]

## The 3 Whys
**Why Anything:** [What breaks if they do nothing?]
**Why {{PRODUCT_NAME}}:** [Which capability matches their pain?]
**Why Now:** [What external event creates urgency?]

## Sources
- [URL or document with description]
```

---

## STEP 5 — Update account-brief.md

After saving the research file:
- Add/update FITS score and ICP tier
- Add any new confirmed contacts
- Update "Last Updated" date
- Update "Top Pain Signal" and "Top Hook" fields

---

## Quality Gates

- [ ] Internal knowledge checked before web research
- [ ] At least 5 web queries run (including deep signal layer in full mode)
- [ ] Tech stack confirmed from source (not assumed)
- [ ] At least 1 pain signal is research-confirmed with a cited source
- [ ] FITS score calculated
- [ ] Output file saved with today's date in name
- [ ] All required chain interface sections present (Company Overview, Tech Stack, Pain Signals, Leadership Contacts, The 3 Whys)
- [ ] account-brief.md updated
- [ ] No invented metrics — every number has a source
