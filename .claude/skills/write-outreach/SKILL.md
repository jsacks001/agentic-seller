---
name: write-outreach
description: |
  Drafts hyper-personalized outreach across all 4 channels. Always reads research file first. Never generic.
  Use when: writing LinkedIn connection requests, InMail, cold emails, cold call scripts,
  follow-up messages, or any outreach for a specific contact at an account.
  Triggers: write outreach, draft message, cold call, cold email, LinkedIn message, InMail,
  email sequence, follow up, outreach for, message to, reach out to, contact script, call script, sequence.
version: 1.0.0
user-invocable: true
---

# Write Outreach

**⚠️ DATA RULE:** Do NOT write a single message without first reading the account's research file.
Every message must reference at least one research-confirmed signal. Generic = deleted.

**⚠️ BANNED:** See `references/banned-phrases.md`. If any banned phrase appears → rewrite from scratch.

**⚠️ METRICS RULE:** Never invent numbers. Only use verified proof points from `references/proof-points.md`
or a live search. Find the most specific match to this account before falling back to generic examples.

---

## STEP 0 — Gather Context

Ask if not provided:
1. Contact name + title + company
2. Channel(s) needed: LI connection / InMail / Email / Cold Call (default: all 4)
3. Any specific angle or signal to focus on?

---

## STEP 1 — Check CRM / DNC

If CRM MCP is configured:
- Search for this contact in CRM — is there an existing relationship or AE ownership?
- Check for any "do not contact" or AE-owned flags

**🛑 STOP if contact is AE-owned or has a DNC flag.** Inform seller: "This contact is owned/flagged in CRM. Coordinate before reaching out."

---

## STEP 2 — Read Research File

Find and read the most recent research file:
`accounts/{account}/research/` → read the latest dated file

Extract (these are the chain interface fields from prospect-research):
- **Tech Stack** → what they're running
- **Pain Signals** → confirmed, cited pains
- **Top 3 Outreach Hooks** → ready-to-use angles
- **Leadership Contacts** → this contact's role + relevance
- **Sales Motion Route** hypothesis
- **Value Driver** for their profile

If no research file exists → run `/prospect-research` first, then return here.

---

## STEP 2.5 — Live Proof Point Search

**Run EVERY time before writing. Never default to the first proof point you remember.**

Search priority — find the most specific match:
1. **Scrape your company's case study page** — filter by prospect's industry + use case
2. **Web search:** `"{{COMPANY_NAME}} [prospect's industry] case study"` and `"{{COMPANY_NAME}} [their tech stack] replaced migration"`
3. **CRM / internal knowledge:** search for industry + use case proof points
4. **Fall back to `references/proof-points.md`** only if no live match found

**Selection rule:**
| Priority | Match | Example |
|----------|-------|---------|
| 1st | Same industry + same use case | Best — most relevant |
| 2nd | Same use case, different industry | Medium relevance |
| 3rd | Same pain, different context | Usable |
| 4th | proof-points.md seed | Last resort only |

---

## STEP 3 — Select the Hook

**Hook selection rules (priority order):**
1. **Personal signal:** Did they publish a blog post, speak at a conference, post on LinkedIn?
   → Search: `"{Name} {Company} conference talk blog post 2026"`
2. **Company signal:** Recent product launch, funding, job posting, news
   → From research file or fresh search
3. **Technical signal:** A specific tool they use that has a known pain
   → From confirmed tech stack in research file
4. **Role signal:** What does someone in this title care about most?
   → Use `references/buyer-personas.md`

Never use a signal you haven't confirmed from research or live data.

---

## STEP 4 — Map to Framework

Before writing, confirm:
- **Sales Motion Route:** Classic / Sprint / Fast (determines CTA format)
- **Value Driver:** Make Money / Save Money / Go Fast / Be Safe
- **Pain:** 1 specific confirmed pain (not a guess)
- **Proof Point:** 1 relevant customer from live search or proof-points.md
- **3 Whys status:**
  - Why Anything: confirmed / missing
  - Why {{PRODUCT_NAME}}: confirmed / missing
  - Why Now: confirmed / missing (if missing → urgency must come from the hook)

---

## STEP 5 — Write All Variants

### A) LinkedIn Connection Request (≤300 chars — count every character)

**Pattern:**
```
[Name], [hot signal in 1 clause]. [pain as question or curiosity hook]. [1 proof point]. Worth connecting?
```

**Enforce:** Count characters. If over 300 → cut ruthlessly. Exec contacts: aim for ≤200.

---

### B) LinkedIn InMail (≤500 words, target 200–300)

**Subject line rules:**
- Pain hypothesis as a question ✓
- Competitor tech in the question ✓
- Never: product name, "introduction", "checking in" ✗

**Body structure:**
1. Hook (reference the research signal, 1 sentence)
2. Pain statement (what's the friction for someone in their role, 2 sentences)
3. Evidence (2–3 bullets: what peers at their stage did + metric)
4. CTA (one ask: 15–20 min call with {{AE_NAME}})

---

### C) Cold Email (≤400 words, target 200–250)

**Subject line:** `[quantified pain] at [company]?` or `[hook signal as question]?`
Never: product name, "checking in", "following up"

**Body:**
```
[Name],

[1 sentence: reference the signal — why you're writing NOW]

[Pain sentence: what breaks for them right now, in their language]

Two things relevant to [Company]:
1. [Specific insight/finding from research]
2. [Proof point: Customer + metric + why it's relevant]

{{AE_NAME}} works with [their type of] teams.
Would a 20-min call this week make sense?

[Your name + title + contact]
```

**P.S. line (optional but effective):** `"P.S. [Specific thing from research that shows you paid attention]."`

---

### D) Cold Call Script

Build from `references/cold-call-framework.md`:
- Pattern interrupt → Bridge (the specific signal) → Pain + outcome → Soft ask
- AAA objection handling for likely objections for their role/industry
- Voicemail variant (20-30 sec max)

---

## STEP 6 — Cadence File Header

Start every outreach file with:

```markdown
# Outreach — {Contact Name} @ {Company}
**Date started:** {YYYY-MM-DD}
**Seller:** {{SELLER_NAME}} | **AE:** {{AE_NAME}}
**Sales Motion Route:** {Classic/Sprint/Fast}
**Value Driver:** {Make Money/Save Money/Go Fast/Be Safe}
**Pain Hypothesis:** {1 sentence}
**Hook Signal:** {Signal used — with source URL or file}

## Cadence Schedule
- Day 1 ({date}): LI Connection + Email
- Day 3: Call
- Day 6: InMail
- Day 10: Email bump
- Day 14: Call
- Day 21: Final touch

## Status Tracker
| Touch | Date | Channel | Sent? | Response |
|-------|------|---------|-------|----------|
| 1 | {date} | LI + Email | [ ] | — |
```

---

## STEP 7 — Save, Update, Create CRM Tasks

**Save file:** `accounts/{account}/emails/{YYYY-MM-DD}-{contact-name}-outreach.md`
**Update:** `accounts/{account}/account-brief.md` → add to outreach log section

**Create 2 CRM tasks** (via {{CRM_SYSTEM}} MCP or output as paste-ready block):

**Task 1 — Day 1 Send:**
```
Task:      "Send outreach — {Contact Name} @ {Company} (Day 1: LI + Email)"
Due:       Today ({YYYY-MM-DD})
Priority:  🔴 Urgent (active deal) | 🟠 High (new outreach)
Notes:     File path + email + LinkedIn URL + LI connection ready to send
```

**Task 2 — Day 3 Call:**
```
Task:      "Call — {Contact Name} @ {Company} (Day 3 follow-up)"
Due:       {YYYY-MM-DD + 3 days}
Priority:  Same as Task 1
Notes:     Cold call script in same outreach file. Reference Day 1 LI + email sent.
```

---

## Quality Gates

- [ ] CRM/DNC checked — no AE-owned or do-not-contact flag
- [ ] Research file read — at least 1 confirmed signal used
- [ ] Live proof point searched — most specific match found
- [ ] LI connection ≤300 chars (counted)
- [ ] Email subject does NOT mention product name or "checking in"
- [ ] Cold call has pattern-interrupt opener (not "How are you?")
- [ ] At least 1 proof point referenced with metric and source
- [ ] No banned phrases (checked against references/banned-phrases.md)
- [ ] Sales Motion Route and Value Driver mapped
- [ ] Output file saved with today's date
- [ ] 2 CRM tasks created or output as paste-ready block
