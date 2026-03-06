---
name: call-debrief
description: |
  Post-call debrief for Alignd sales calls. Captures notes, maps to Challenger framework,
  flags gaps in Teach/Tailor/Take Control, drafts follow-up email.
  Use when: just got off a call, have call notes to process, need to capture discovery output,
  want to update qualification status, need a follow-up email, or want to update CRM notes.
  Triggers: debrief, call notes, just got off, post call, call recap, capture notes,
  what happened, follow up email after call, notes from meeting,
  call summary, discovery notes, I just spoke with.
user-invocable: true
---

# Call Debrief — Alignd

**TIMING RULE:** Do this immediately after the call. The best debrief is in the first 15 minutes.
Memory degrades fast. Don't wait.

**DATE RULE:** Check `currentDate`. Notes saved as `YYYY-MM-DD-{type}-notes.md`.

---

## STEP 1 — Raw Details

Ask if not provided:
1. Who was on the call? (names + titles)
2. What type of call was it? (intro / follow-up / pricing / discovery / demo / AE-led)
3. How long did it last?

---

## STEP 2 — Transcript or Notes Check

Ask the seller:

**"Do you have a call transcript?"**
- **Yes** → Ask them to upload/paste it. Use the transcript as source material for Step 4 questions.
- **No** → Ask: **"Do you have notes?"**
  - **Yes** → Ask them to upload/paste notes. Use the notes as source material for Step 4 questions.
  - **No** → Continue to Step 3. Step 4 will run in verbal download mode.

**Important:** Even when a transcript or notes are provided, still ask the Step 4 questions to the seller.
The transcript captures what was said — the seller's interpretation captures what it meant.

---

## STEP 3 — Read Prior Context

Before capturing notes, read what we knew BEFORE the call:
1. `accounts/{account}/account-brief.md` → current qualification status
2. `accounts/{account}/meetings/{last-brief}.md` → what were we trying to learn?
3. `accounts/{account}/discovery/` → any prior call notes

**Why this matters:** The debrief should highlight what CHANGED, not just what was said.
Compare before vs. after — that's the signal.

---

## STEP 4 — Capture Notes

Walk through each section below. If a transcript/notes were provided, reference them while asking — but still ask each question to get the seller's read.

### 4A — What Happened

- "What happened — in one sentence?"
- "Who spoke the most — them or you?"
- "What was the energy? Engaged / polite / skeptical / rushed?"

### 4B — Raw Details (Their World)

- "When do they run reward/remuneration cycles?"
- "What platforms are they currently using? (Excel, HRIS, Workday, SAP, manual?)"
- "How is their org structured? (centralised reward team, decentralised by BU, shared services?)"

### 4C — Challenges

- "What challenges did they bring up?"
- "What's this person's biggest pain?"
- "What are their current priorities and focuses?"

### 4D — Deeper Pain Understanding

- "Were we able to link their challenges to governance? (structured approvals, audit trail, risk)"
- "Were we able to link to visibility? (dashboards, board reporting, budget tracking)"
- "Were we able to link to fair pay / policy alignment? (DEI guardrails, pay philosophy, performance-to-reward)"
- "Did any other use cases come up beyond these three?"

### 4E — Deal Qualification & Momentum

- "Did anyone mention budget, cost, or cost reduction?"
- "Who else needs to be involved in a decision like this?"
- "Is there a timeline or upcoming deadline? (fiscal year, board review, restructure?)"
- "Is there someone internal who's clearly the champion?"
- "What else are they evaluating — Workday, SAP, staying with current process?"
- "Did they agree to a next step? What exactly?"
- "Was there a specific objection? How did it go?"
- "Any quote or thing they said that stood out?"

### 4F — Challenger Assessment

Map every piece of information to the Challenger qualification elements.

| Element | Question | Status | Evidence from Call |
|---------|----------|--------|--------------------|
| **Commercial Insight (Teach)** | Did we teach them something new about their reward governance risk? | // | What insight landed? |
| **Reframe** | Did we challenge their assumptions about the status quo (Excel/manual/HRIS)? | //// | How did they react? |
| **Tailored Message** | Was our message mapped to their specific outcomes (governance / visibility / efficiency)? | //// | Which outcome resonated? |
| **Constructive Tension** | Did we create urgency by exposing cost of inaction? | //// | Did they acknowledge the risk? |
| **Economic Buyer** | Who approves budget? Were they on the call? | //// | Name if known |
| **Decision Process** | What steps to get to yes? Timeline? | //// | Process described |
| **Champion** | Who advocates internally? | //// | Name + evidence |
| **Competition** | What else evaluating? (Workday, SAP, manual, HRIS built-in) | //// | Competitor(s) named |

**Status key:**
- Confirmed — we have evidence from the call
- Unknown — not yet discussed
- Negative — confirmed blocked or won't happen

**Challenger Score:** Count confirmed out of 8. Target: advance at least 2 per call.

### 4G — 3 Whys Assessment

| Why | Status | Evidence |
|-----|--------|----------|
| Why Anything (cost of status quo — what breaks if they keep using Excel/manual?) | | |
| Why Alignd (which capability matches: governance, visibility, or policy alignment?) | | |
| Why Now (external event: compliance deadline, board pressure, restructure, new CHRO?) | | |

**Analysis:**
- All 3 Unknown → Very early. Priority: establish pain first. What's broken in their cycle?
- Why Anything Confirmed, others Unknown → Next meeting: Why Alignd (demo tailored to their pain) and Why Now.
- All 3 Confirmed → Strong discovery. Advance to commercial discussion or technical deep-dive.
- Why Now Unknown → Create urgency in follow-up: find an external event (fiscal year, board review, audit, restructure, new CHRO appointment).

### 4H — Alignd Pain Map

Map what we learned about their specific pain to Alignd's three core outcomes:

| Alignd Outcome | Their Pain | Evidence | Demo Priority |
|----------------|-----------|----------|---------------|
| **Governance** (structured approvals, audit trail, risk mitigation) | | | High / Medium / Low / Unknown |
| **Policy Alignment** (DEI guardrails, pay philosophy, performance-to-reward) | | | High / Medium / Low / Unknown |
| **Visibility** (real-time dashboards, budget tracking, leadership reporting) | | | High / Medium / Low / Unknown |

**Primary value driver for this account:** Make Money / Save Money / Go Fast / Be Safe

---

## STEP 5 — Not used (reserved)

---

## STEP 6 — Add Call Debrief to HubSpot

Via HubSpot MCP (if configured) or as a paste-ready block.

Output this block formatted for HubSpot:

```
CRM Call Log — {Date}
Call type: {Intro / Follow-up / Pricing / Discovery / Demo}
Duration: {X min}
Attendees: {names + titles}

Summary:
[2-3 sentences: what happened, key finding, next step]

Challenger Updates:
- Commercial Insight: [what we taught / what landed]
- Pain Identified: [governance / visibility / policy — in their words]
- Economic Buyer: [identified as: ... / not yet identified]
- Champion: [identified as: ... / not yet identified]
- Competition: [Workday / SAP / manual / none mentioned]
- Next Step: [what was agreed]

Alignd Pain Map: Governance [H/M/L] | Policy [H/M/L] | Visibility [H/M/L]
Value Driver: [Make Money / Save Money / Go Fast / Be Safe]

Stage Recommendation: {Research / Outreach / Engaged / Discovery / Meeting Booked / Qualified}

---

DRAFT FOLLOW-UP EMAIL (review before sending):

[Email from Step 7 appended here]
```

**RULE: The draft email is appended to the end of the HubSpot notes. NEVER send the email automatically.**

---

## STEP 7 — Draft Follow-Up Email

Draft a follow-up email using this format:

```
Hi {First Name},

Thanks for your time today and your thoughtful feedback and questions. Quick summary of where we landed:

1. {Use case / topic discussed #1}
2. {Use case / topic discussed #2}
3. {Use case / topic discussed #3}

Confident we can help with this and more. From here:

1. {Next step #1 — e.g., sending relevant resources}
2. {Next step #2 — e.g., scheduling next meeting with date}
3. {Next step #3 — e.g., pricing if discussed}

Anything we've missed? Let me know.

{Sign off}
```

**Rules:**
- Use cases should reflect what was actually discussed on the call — not generic feature dumps.
- Next steps should be specific and actionable.
- If pricing was discussed, include it. If not, don't.
- Keep it concise. No fluff.
- Challenger tone — confident, consultative, not apologetic.
- **This email is appended to the HubSpot notes in Step 6. NEVER sent automatically.**

---

## STEP 8 — Save Call Notes

**File path:**
- Discovery/intro/follow-up call → `accounts/{account}/discovery/{YYYY-MM-DD}-{type}-notes.md`
  (types: cold-call, intro, discovery, follow-up, pricing, demo)
- AE-led meeting → `accounts/{account}/meetings/{YYYY-MM-DD}-meeting-summary.md`

### Call Notes File Structure

```markdown
# Call Notes — {Company} — {Date}
**Type:** {Intro / Follow-up / Pricing / Discovery / Demo}
**Duration:** {X min}
**Participants:** {Their names + titles} | Josh{, other Alignd attendees if present}
**Energy:** {Engaged / Polite / Skeptical / Rushed}

---

## What Happened (1-paragraph summary)
[Raw summary before analysis]

## Their World
- **Cycle timing:** [when they run reward cycles]
- **Platforms:** [what they currently use]
- **Org structure:** [how reward/rem team is structured]

## Challenges
[What they raised — in their words where possible]

## Deeper Pain
[How challenges connect to governance, visibility, fair pay, policy alignment]

## Key Quotes
1. "[Direct quote showing pain or buying signal]"
2. "[Direct quote showing objection or concern]"

## Challenger Status (Updated)
[Full table from Step 4F]

## 3 Whys Status
[Table from Step 4G]

## Alignd Pain Map
[Table from Step 4H]

## Gaps to Fill (Next Meeting)
1. [Missing element] → Questions to ask: [...]
2. [Missing element] → Questions to ask: [...]

## Next Step Agreed
[Exactly what was agreed on the call — the literal commitment]

## Follow-Up Email
[Draft from Step 7]

## Objections Logged
| Type | Verbatim Quote | Stage | Response Used | Outcome |
|------|---------------|-------|--------------|---------|
| [Timing/Budget/Authority/Trust/Fit/Competition] | "[quote]" | [stage] | [response approach] | [result] |
```

**Note:** The "Objections Logged" section is required — it feeds the `/objection-mining` skill.

---

## STEP 9 — Create Follow-Up Task

Via HubSpot MCP (if configured) or as a paste-ready block:

Create tasks for any commitments made on the call:
- Follow-up email (review and send the draft from Step 7)
- Resources to send (tailored to their pain — governance / visibility / policy)
- Next meeting to schedule
- Research needed for next interaction

Set: account name, due date, priority, assigned to Josh.

---

## Quality Gates

- [ ] Notes saved with today's date in filename
- [ ] Challenger table filled with call evidence (8 elements assessed)
- [ ] 3 Whys assessed (all 3 rows)
- [ ] Alignd Pain Map completed (governance / policy / visibility prioritised)
- [ ] At least 1 direct quote captured
- [ ] Next step documented (or flagged as missing with recovery plan)
- [ ] "## Objections Logged" section present in call notes file
- [ ] Follow-up email drafted and appended to HubSpot notes (NOT sent)
- [ ] account-brief.md updated (qualification status + last interaction)
- [ ] CRM log notes drafted (paste-ready or synced)
- [ ] CRM task created for any commitments made on call
