---
name: discovery-prep
description: |
  Builds a complete Alignd prospect call prep sheet before any discovery, intro, or follow-up call.
  Uses the Challenger framework (Teach, Tailor, Take Control) and Alignd's governance/visibility/policy positioning.
  Use when: preparing for a discovery call, intro meeting, follow-up, or AE-led meeting.
  Includes: company overview, attendee intel, call objectives, Challenger-mapped discovery questions,
  demo structure (outcome-led), objections, proof points, and next steps.
  Triggers: prep, meeting prep, discovery prep, prepare for, call prep, before meeting,
  discovery call, intro meeting, meeting brief, what should I know, going into a call, prep me.
user-invocable: true
---

# Discovery Prep — Alignd Prospect Call Prep Sheet

**⚠️ DATA RULE:** The worst thing that can happen in a meeting is being surprised.
Pull everything. Find the latest news. Miss nothing.

**⚠️ DATE RULE:** Check `currentDate`. Output file named `YYYY-MM-DD-meeting-brief.md`.
Don't use training knowledge for "latest news" — always pull live data.

**⚠️ CHALLENGER RULE:** Every meeting brief must include a Commercial Insight — something the prospect doesn't know about their own business that reframes how they think about reward/remuneration governance.

---

## STEP 0 — Confirm Meeting Details

Ask if not provided:
1. Account name + type of meeting (intro / discovery / follow-up / AE-led)
2. Date and time
3. Who's on the call (their side + your side) — names, titles, emails, LinkedIn if available
4. How did this meeting get booked? What's the context? (Demo source / referral)
5. Seniority level of attendees (Operational / Head of / Exec / C-level)

---

## STEP 1 — Internal Knowledge Refresh

Check all existing intel before going to the web:

**Local files:**
- `accounts/{account}/account-brief.md` → full qualification status
- `accounts/{account}/research/` → most recent research file
- `accounts/{account}/discovery/` → all prior call notes
- `accounts/{account}/meetings/` → prior meeting briefs

**Build picture before Step 2:**
- What do we know vs. what are we guessing?
- Which Challenger elements are confirmed vs. blank?
- What was the goal of the last interaction?
- What is their likely HR tech stack?
- Any visible HR, governance, DEI, or people strategy priorities?

---

## STEP 2 — Fresh External Intel (Last 30 Days)

Search for anything published recently about the company or attendees:

**Full mode (Bright Data):**
```
mcp__brightdata__search_engine:
1. "{Company} news 2026"
2. "{Company} HR remuneration reward strategy 2026"
3. "{Company} restructuring growth acquisition 2026"
4. "{Attendee names} LinkedIn blog post conference 2026"
5. "{Company} DEI pay equity governance"
6. "{Company} HR tech stack HRIS"
7. "Alignd {Company industry} case study customer story"
```

**Lite mode (WebSearch):**
```
Same queries via WebSearch tool
```

**Goal:** Find at least 1 warm-up talking point from the last 30 days.
Find at least 1 insight about their reward/remuneration challenges.
Identify any news about growth, restructuring, acquisitions, or compliance changes.

---

## STEP 3 — Challenger Gap Analysis

Map current knowledge against the Challenger framework.
Mark each element: ✅ Confirmed | ⬜ Unknown | 🎯 Probe in this meeting | 🚫 Negative signal

| Element | Question | Status | What We Know | Goal for This Meeting |
|---------|----------|--------|--------------|----------------------|
| Commercial Insight | What can we teach them about reward governance they don't already know? | | | |
| Reframe | Have we challenged their assumptions about the status quo (Excel, manual processes)? | | | |
| Tailored Message | Is our message mapped to their specific business outcomes (governance / visibility / efficiency)? | | | |
| Constructive Tension | Have we created urgency by exposing cost of inaction (risk, errors, audit failures)? | | | |
| Economic Buyer | Who approves budget? Will they be in the room? | | | |
| Decision Process | What are the exact steps from here to signed? | | | |
| Champion | Who inside will fight for this? Who wants us to win? | | | |
| Competition | What else are they evaluating? (Workday, SAP, manual process, HRIS built-in) | | | |

**Goal for this meeting:** Fill at least 3 blank elements.
**Priority:** Establish the Commercial Insight and Reframe first — in Challenger, teaching precedes selling.

---

## STEP 4 — 3 Whys Status

| Why | Status | Evidence |
|-----|--------|----------|
| Why Anything (cost of status quo — what breaks if they keep using Excel/manual?) | ✅/⬜ | |
| Why Alignd (which specific capability matches their pain — governance, visibility, policy?) | ✅/⬜ | |
| Why Now (external event — compliance deadline, board pressure, restructure, new CHRO?) | ✅/⬜ | |

If any Why is ⬜ → it becomes a goal for this meeting.

---

## STEP 5 — Build the Meeting Brief

**Save as:** `accounts/{account}/meetings/{YYYY-MM-DD}-meeting-brief.md`

```markdown
# Alignd Prospect Call Prep Sheet — {Company}
**Date/Time:** {date and time}
**Duration:** {duration}
**Type:** Intro / Discovery / Follow-up / AE-led

---

## 1. Company Overview

| Field | Detail |
|-------|--------|
| Company Name | |
| Website URL | |
| Head Office Location | |
| Other Key Locations | |
| Number of Employees | |
| Annual Revenue (if known) | |
| Industry / Sector | |
| Ownership | Private / Public / PE-backed / Subsidiary |

**Notes / Context:**
- Recent news (growth, acquisitions, restructuring, expansion):
- Any visible HR or governance challenges:
- Known DEI or people strategy priorities:
- Existing HR tech stack (if known):

---

## 2. Call Participants

| Name | Title | Email | LinkedIn | Demo Source / Referral |
|------|-------|-------|----------|----------------------|
| | | | | |

**Seniority Level:** Operational / Head of / Exec / C-level
**Economic Buyer Identified?** Yes / No
**Decision Process Known?** Yes / No

**Internal Notes:**
- Influence level:
- Likely priorities (governance / visibility / risk / efficiency / culture):
- Previous conversations summary:

---

## 3. Call Objective

**Primary Objective:**
(e.g., Qualify governance pain + demonstrate visibility value)

**Secondary Objective:**
(e.g., Identify stakeholders + next step commitment)

**Ideal Outcome of Call:**
- Clear pain acknowledged
- Fit confirmed
- Agreed next step (demo with X, technical deep dive, commercial discussion, etc.)

---

## 4. Commercial Insight (Challenger — Teach)

**The insight we're bringing to this call:**
[What does the prospect NOT know about their own reward/remuneration risk that we can teach them?]

**Reframe:**
[How does this insight challenge their current thinking about Excel/manual/status quo?]

**Tailored to their world:**
[How does this connect to their specific industry, size, or recent news?]

---

## 5. Call Script Framework

### A) Introductions (5 mins)
- Thank them for their time
- Set context: "The goal today is to understand how you're currently managing reward cycles and see whether Alignd could help structure and de-risk that process."
- Confirm agenda:
  1. Understand current approach
  2. Explore challenges
  3. Share how Alignd approaches it
  4. Discuss fit + next steps

### B) Discovery Questions (15–25 mins)

#### Current State
- "Tell us about your current cycle management process."
- "How are increases/bonuses approved and tracked?"
- "What tools are you using today?" (Excel? HRIS? Manual approvals?)
- "How long does a full cycle typically take?"

#### Challenges (Constructive Tension)
- "Where does the process feel heavy or risky?"
- "What slows things down?"
- "Where do errors tend to happen?"
- "How confident are you in your audit trail?"
- "Is there governance oversight during or after cycles?"

#### Visibility & Leadership Questions
- "Are there questions from board/leadership that are difficult to answer?"
- "Can you quickly show: Pay equity by group? Budget tracking in real-time? Policy compliance?"
- "Do managers understand the reward framework clearly?"

#### Policy & Talent Alignment
- "How do you ensure HR policy (DEI, fairness, pay philosophy) is reflected in decisions?"
- "Is performance formally connected to reward?"
- "How do you communicate total reward to employees?"

### C) Introducing Alignd (10–15 mins)

**Positioning — Three Core Outcomes:**

1. **Aligning process with governance requirements**
   - Structured approvals
   - Audit trail
   - Risk mitigation

2. **Embedding HR policy into the process**
   - DEI & fairness guardrails
   - Pay philosophy reflected in workflows
   - Performance-to-reward linkage

3. **Creating visibility at every level**
   - Real-time budget tracking
   - Leadership dashboards
   - Clear management insight

### D) Demo Structure (Outcome-Led)

**⚠️ CRITICAL: Tailor demo to what they said — not feature dumping.**
Frame everything around outcomes.

**Show based on their pain:**

| If their pain is... | Show... |
|---------------------|---------|
| Governance risk | Parameter controls aligned to internal boundaries, structured approvals, audit logs |
| Performance alignment | Linking performance ratings to reward pools, guardrails within bands |
| Visibility | Real-time dashboards, budget tracking by department, leadership-level reporting |

**Always translate feature → business outcome:**
- "This reduces board risk because…"
- "This shortens your cycle by…"
- "This ensures policy isn't optional…"

---

## 6. End-of-Call Questions

- "What are your initial thoughts?"
- "Does this reflect what you were hoping to see?"
- "Who else on your team would need to be involved?"
- "Who do you envision using a platform like this day-to-day?"
- "What would be your biggest concern with implementing something like this?"
- "What would need to be true internally for this to move forward?"

---

## 7. Expected Objections

| Objection | Response |
|-----------|----------|
| "We manage fine with Excel / our HRIS" | "Most teams do — until the first audit question they can't answer in real-time. What does your board expect in terms of governance visibility?" |
| "Workday/SAP already does this" | "They handle payroll and HRIS brilliantly. The gap we see is in the governance layer — structured approvals, policy guardrails, and real-time visibility during cycles. Is that something you're getting today?" |
| "No budget right now" | "Understood — is this a timing question or a priority question? If the board asked tomorrow for a pay equity report, how quickly could you produce it?" |
| "We need to involve more stakeholders" | "Absolutely — who would need to see this, and what would matter most to them?" |
| [Add objections from research/prior calls] | |

---

## 8. Proof Points Ready

**Source priority:** Live search (Alignd case studies) → CRM proof points → references/proof-points.md

1. **[Customer]** — [metric] — use when: [moment in conversation] — Source: [URL]
2. **[Customer]** — [metric] — use when: [moment] — Source: [URL]

*Note: HiBob is a known customer. Search for published proof points before each call.*

---

## 9. Challenger Pre-Meeting Status

[Copy gap analysis table from Step 3]

## 3 Whys Status

[Copy 3 Whys table from Step 4]

---

## 10. Next Steps (fill after call)

| Field | Detail |
|-------|--------|
| Agreed Next Step | |
| Timeline | |
| Additional Stakeholders | |
| Information to Send | |
| Follow-up Owner (Alignd) | |

---

## After the Call
→ Run `/call-debrief` immediately while context is hot.
```

---

## STEP 6 — Log Prep Sheet to HubSpot

After saving the meeting brief locally, log it as a note in HubSpot against the company/contact record:

1. Find the company in HubSpot (search by account name)
2. Create an engagement note with the full prep sheet content (markdown formatted)
3. Associate the note with the relevant contact(s) attending the call
4. If HubSpot MCP is not connected: output a paste-ready block for manual entry

**Note title format:** `Call Prep — {Company} — {Date} — {Meeting Type}`

---

## STEP 7 — Day-of Checklist

Print or pin before the call:
- [ ] Commercial Insight to teach: ___
- [ ] Hot signal to open with: ___
- [ ] First discovery question (current state): ___
- [ ] Economic buyer name to confirm: ___
- [ ] Demo tailored to their pain (governance / visibility / policy): ___
- [ ] Proof point ready: ___
- [ ] CTA to close with: ___
- [ ] Next step to propose: ___

---

## Quality Gates

- [ ] All existing account files read before searching the web
- [ ] Fresh external intel checked (at least 1 thing from last 30 days)
- [ ] Commercial Insight prepared (Challenger — Teach)
- [ ] Challenger gap analysis complete with goals for each unknown
- [ ] Discovery questions cover: Current State, Challenges, Visibility, Policy
- [ ] Demo structure mapped to their specific pain (not generic)
- [ ] At least 2 objections prepared with responses
- [ ] At least 1 proof point from live search matched to their profile
- [ ] 3 Whys status assessed — any gaps become meeting goals
- [ ] Meeting brief saved to `meetings/` with today's date
- [ ] Prep sheet logged as note in HubSpot (or paste-ready block provided)
