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

**⚠️ TIMING RULE:** Do this immediately after the call. The best debrief is in the first 15 minutes.
Memory degrades fast. Don't wait.

**⚠️ DATE RULE:** Check `currentDate`. Notes saved as `YYYY-MM-DD-{type}-notes.md`.

---

## STEP 0 — Confirm Context

Ask if not provided:
1. Which account + which contact(s) were on the call?
2. Call type: cold call / intro / discovery / follow-up / AE-led
3. How long did it last?
4. Do you have notes, or should I ask you questions to capture them?

If no notes → run the verbal download guide in Step 2.

---

## STEP 1 — Read Prior Context

Before capturing notes, read what we knew BEFORE the call:
1. `accounts/{account}/account-brief.md` → current qualification status
2. `accounts/{account}/meetings/{last-brief}.md` → what were we trying to learn?
3. `accounts/{account}/discovery/` → any prior call notes

**Why this matters:** The debrief should highlight what CHANGED, not just what was said.
Compare before vs. after — that's the signal.

---

## STEP 2 — Capture Notes (verbal download mode)

If seller is giving notes verbally, guide them through these in order:

**Quick Context**
- "What happened — in one sentence?"
- "Who spoke the most — them or you?"
- "What was the energy? Engaged / polite / skeptical / rushed?"

**Challenger Assessment**
- "Did you get to teach them something new — a commercial insight they didn't know?"
- "Did they push back on the status quo, or are they still comfortable with how things are?"
- "Did you tailor the message to their specific world — or was it more generic?"
- "Did you take control of next steps — or did they say 'we'll get back to you'?"

**Pain Discovery — Alignd-Specific**
- "Did they describe how they currently manage reward cycles? (Excel, HRIS, manual?)"
- "Did they mention governance risk, audit trail gaps, or compliance concerns?"
- "Did they talk about visibility problems — board questions they can't answer quickly?"
- "Did they mention policy alignment — DEI guardrails, pay philosophy, performance-to-reward?"
- "What's their biggest frustration with the current process?"
- "What have they tried before? What didn't work?"

**Deal Qualification**
- "Did anyone mention budget, cost, or cost reduction?"
- "Who else needs to be involved in a decision like this?"
- "Is there a timeline or upcoming deadline? (fiscal year, board review, restructure?)"
- "Is there someone internal who's clearly the champion?"
- "What else are they evaluating — Workday, SAP, staying with current process?"

**Momentum**
- "Did they agree to a next step? What exactly?"
- "Was there a specific objection? How did it go?"
- "Any quote or thing they said that stood out?"

---

## STEP 3 — Map to Challenger Framework

Map every piece of information to the Challenger qualification elements.

| Element | Question | Status | Evidence from Call |
|---------|----------|--------|--------------------|
| **Commercial Insight (Teach)** | Did we teach them something new about their reward governance risk? | ✅/⬜/🚫 | What insight landed? |
| **Reframe** | Did we challenge their assumptions about the status quo (Excel/manual/HRIS)? | ✅/⬜/🚫 | How did they react? |
| **Tailored Message** | Was our message mapped to their specific outcomes (governance / visibility / efficiency)? | ✅/⬜/🚫 | Which outcome resonated? |
| **Constructive Tension** | Did we create urgency by exposing cost of inaction? | ✅/⬜/🚫 | Did they acknowledge the risk? |
| **Economic Buyer** | Who approves budget? Were they on the call? | ✅/⬜/🚫 | Name if known |
| **Decision Process** | What steps to get to yes? Timeline? | ✅/⬜/🚫 | Process described |
| **Champion** | Who advocates internally? | ✅/⬜/🚫 | Name + evidence |
| **Competition** | What else evaluating? (Workday, SAP, manual, HRIS built-in) | ✅/⬜/🚫 | Competitor(s) named |

**Status key:**
- ✅ Confirmed — we have evidence from the call
- ⬜ Unknown — not yet discussed
- 🚫 Negative — confirmed blocked or won't happen

**Challenger Score:** Count ✅ out of 8. Target: advance at least 2 per call.

---

## STEP 4 — 3 Whys Assessment

| Why | Status | Evidence |
|-----|--------|----------|
| Why Anything (cost of status quo — what breaks if they keep using Excel/manual?) | ✅/⬜ | |
| Why Alignd (which capability matches: governance, visibility, or policy alignment?) | ✅/⬜ | |
| Why Now (external event: compliance deadline, board pressure, restructure, new CHRO?) | ✅/⬜ | |

**Analysis:**
- All 3 ⬜ → Very early. Priority: establish pain first. What's broken in their cycle?
- Why Anything ✅, others ⬜ → Next meeting: Why Alignd (demo tailored to their pain) and Why Now.
- All 3 ✅ → Strong discovery. Advance to commercial discussion or technical deep-dive.
- Why Now ⬜ → Create urgency in follow-up: find an external event (fiscal year, board review, audit, restructure, new CHRO appointment).

---

## STEP 5 — Alignd Pain Map

Map what we learned about their specific pain to Alignd's three core outcomes:

| Alignd Outcome | Their Pain | Evidence | Demo Priority |
|----------------|-----------|----------|---------------|
| **Governance** (structured approvals, audit trail, risk mitigation) | | | High / Medium / Low / Unknown |
| **Policy Alignment** (DEI guardrails, pay philosophy, performance-to-reward) | | | High / Medium / Low / Unknown |
| **Visibility** (real-time dashboards, budget tracking, leadership reporting) | | | High / Medium / Low / Unknown |

**Primary value driver for this account:** Make Money / Save Money / Go Fast / Be Safe

---

## STEP 6 — Draft Follow-Up Email

Draft a follow-up email that:
1. Thanks them and references a specific moment from the call (not generic)
2. Reinforces the commercial insight (Teach) — link to the pain they acknowledged
3. Includes 1 proof point or relevant resource matched to their pain
4. States the agreed next step with a proposed date/time
5. Keeps it under 200 words — no feature dumping

**Tone:** Challenger — confident, consultative, not apologetic. No "just following up" or "wanted to check in."

---

## STEP 7 — CRM Update Notes

Output this block formatted for copy-paste into HubSpot (or sync via HubSpot MCP if configured):

```
CRM Call Log — {Date}
Call type: {Cold Call / Intro / Discovery / Follow-up}
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
```

---

## STEP 8 — Save Call Notes

**File path:**
- Discovery/intro/follow-up call → `accounts/{account}/discovery/{YYYY-MM-DD}-{type}-notes.md`
  (types: cold-call, intro, discovery, follow-up)
- AE-led meeting → `accounts/{account}/meetings/{YYYY-MM-DD}-meeting-summary.md`

### Call Notes File Structure

```markdown
# Call Notes — {Company} — {Date}
**Type:** {Cold Call / Intro / Discovery / Follow-up}
**Duration:** {X min}
**Participants:** {Their names + titles} | Josh{, other Alignd attendees if present}
**Energy:** {Engaged / Polite / Skeptical / Rushed}

---

## What Happened (1-paragraph summary)
[Raw summary before analysis]

## Key Quotes
1. "[Direct quote showing pain or buying signal]"
2. "[Direct quote showing objection or concern]"

## Challenger Status (Updated)
[Full table from Step 3]

## 3 Whys Status
[Table from Step 4]

## Alignd Pain Map
[Table from Step 5]

## Gaps to Fill (Next Meeting)
1. [Missing element] → Questions to ask: [...]
2. [Missing element] → Questions to ask: [...]

## Next Step Agreed
[Exactly what was agreed on the call — the literal commitment]

## Follow-Up Email
[Draft from Step 6]

## Objections Logged
| Type | Verbatim Quote | Stage | Response Used | Outcome |
|------|---------------|-------|--------------|---------|
| [Timing/Budget/Authority/Trust/Fit/Competition] | "[quote]" | [stage] | [response approach] | [result] |
```

**Note:** The "Objections Logged" section is required — it feeds the `/objection-mining` skill.

---

## STEP 9 — Create CRM Task

Via HubSpot MCP (if configured) or as a paste-ready block:

Create tasks for any commitments made on the call:
- Follow-up email (if not yet sent)
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
- [ ] Follow-up email drafted (Challenger tone, references specific call moment)
- [ ] account-brief.md updated (qualification status + last interaction)
- [ ] CRM log notes drafted (paste-ready or synced)
- [ ] CRM task created for any commitments made on call
