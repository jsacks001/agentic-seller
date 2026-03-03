---
name: icp-matrix-builder
description: |
  Scores accounts on 5 ICP dimensions and assigns tier. Feeds signal-scoring weighting.
  Use when: scoring a new account against your ICP, updating the territory tier list,
  deciding which accounts to prioritize, or building an initial ICP profile from scratch.
  Triggers: icp score, tier assignment, update icp, icp matrix, who fits best,
  score account, qualify account, tier this account.
version: 1.0.0
user-invocable: true
---

# ICP Matrix Builder

**Purpose:** Not all accounts are equal. Score them honestly.
Tier 1 accounts get aggressive pursuit. Tier 4 accounts get deprioritized or dropped.

**Input:** Research files + {{ICP_DESCRIPTION}} from CLAUDE.md
**Output:** `memory/icp-matrix.md` — overwrite monthly (or after scoring new accounts)
**Feeds:** `/signal-scoring` uses ICP tiers to weight signal priority

---

## STEP 0 — Confirm Scope

1. **Score a new account:** "Score [company] on ICP"
   → Read research file or run prospect-research first if no file exists
2. **Full territory scoring:** "Update ICP matrix" or "Score all accounts"
   → Score all accounts in `accounts/` folder against current ICP definition
3. **Refresh ICP definition:** "Update my ICP"
   → Re-read {{ICP_DESCRIPTION}} from CLAUDE.md, discuss changes, then re-score

---

## STEP 1 — Load ICP Definition

Read {{ICP_DESCRIPTION}} from CLAUDE.md.

Parse into scoring dimensions:
- What **industry/vertical** is ideal?
- What **company size** (employees / ARR) is ideal?
- What **tech stack signals** indicate fit?
- What **stage** (Series A, B, C, Enterprise, SMB) is ideal?
- What **role** or team structure drives the buying decision?

If {{ICP_DESCRIPTION}} is vague → ask seller to clarify before scoring.

---

## STEP 2 — Read Account Data

For each account to score:
1. Read `accounts/{account}/account-brief.md` → company snapshot, tech stack, contacts
2. Read `accounts/{account}/research/` → most recent research file
3. If no data exists → note "insufficient data" and run `/prospect-research` to gather it

---

## STEP 3 — Score on 5 Dimensions

Score each dimension 0–20 (total = 100):

### D1 — Firmographic Fit (0–20)
Does the company match the ideal profile on industry, size, and stage?
- 18–20: Perfect match across all firmographic criteria
- 12–17: Matches 2 of 3 criteria
- 6–11: Matches 1 criterion
- 0–5: Outside ICP profile

### D2 — Technical Fit (0–20)
Does their confirmed tech stack create a natural use case for {{PRODUCT_NAME}}?
- 18–20: Confirmed tech stack is an obvious fit — specific tools/patterns we solve
- 12–17: Likely fit based on their profile, not yet confirmed
- 6–11: Possible fit but no clear signal
- 0–5: Tech stack confirmed incompatible or no signal at all

### D3 — Timing / Urgency (0–20)
Is there a signal that creates urgency now vs. in 6 months?
- 18–20: Clear forcing function — launch date, funding, leadership change, migration underway
- 12–17: Some urgency signal — active hiring, growth phase
- 6–11: No current urgency, but the pain is real
- 0–5: Active lock-in, no forcing function visible

### D4 — Decision Capacity (0–20)
Can they make a decision? Champion, economic buyer, reasonable process?
- 18–20: Known champion + economic buyer accessible + clear process
- 12–17: Champion identified but EB unknown, or process unclear
- 6–11: No champion identified, buying process opaque
- 0–5: Gatekept, wrong contact, or known slow/broken buying process

### D5 — {{PRODUCT_NAME}} Value Match (0–20)
Is the specific pain we solve clearly present and important to them?
- 18–20: Confirmed pain in their words — it's a priority this year
- 12–17: Pain likely based on their profile and stage
- 6–11: Pain possible but not confirmed
- 0–5: No clear pain signal, or confirmed different priorities

---

## STEP 4 — Assign Tier

| Total Score | Tier | Label | Strategy |
|-------------|------|-------|---------|
| 80–100 | **Tier 1** | Bullseye | Pursue aggressively — multi-channel, high cadence |
| 60–79 | **Tier 2** | Strong | Worth full outreach — standard cadence |
| 40–59 | **Tier 3** | Possible | Lower priority — lighter touch, monitor signals |
| 0–39 | **Tier 4** | Stretch | Deprioritize — only pursue if inbound or warm intro |

---

## STEP 5 — Save to ICP Matrix

**Output format in `memory/icp-matrix.md`:**

```markdown
# ICP Matrix — {{COMPANY_NAME}} Territory
*Last updated: YYYY-MM-DD | Scored by: {{SELLER_NAME}}*

## ICP Definition
{{ICP_DESCRIPTION}}

---

## Account Tiers

| Account | Tier | ICP Score | D1 Firm | D2 Tech | D3 Timing | D4 Decision | D5 Value | Top Fit Reason | Last Scored |
|---------|------|-----------|---------|---------|-----------|-------------|----------|---------------|------------|
| [Company] | 1 | 88 | 18 | 20 | 16 | 18 | 16 | Series C, 200 engineers, active migration | YYYY-MM-DD |

---

## Tier Summary

| Tier | Count | Strategy |
|------|-------|---------|
| Tier 1 (80+) | | Pursue aggressively |
| Tier 2 (60-79) | | Standard cadence |
| Tier 3 (40-59) | | Monitor + light touch |
| Tier 4 (<40) | | Deprioritize |

---

## Accounts Needing More Data (scored with insufficient research)

| Account | Missing | Action |
|---------|---------|--------|
| [Company] | Tech stack, contacts | Run /prospect-research |
```

**Save to:** `memory/icp-matrix.md` (full overwrite — this is a current-state snapshot)

---

## Quality Gates

- [ ] {{ICP_DESCRIPTION}} loaded from CLAUDE.md before scoring
- [ ] All 5 dimensions scored (not skipped) for each account
- [ ] Score reasoning documented (what evidence drove each score)
- [ ] Accounts with insufficient data flagged — not scored 0 by default
- [ ] Tier assignments match score ranges exactly
- [ ] memory/icp-matrix.md saved with today's date
- [ ] Accounts needing more data listed with action plan
