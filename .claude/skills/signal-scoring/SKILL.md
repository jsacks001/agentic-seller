---
name: signal-scoring
description: |
  Scans territory for buying signals, weights by ICP tier, surfaces prioritized action list.
  Use when: prioritizing which accounts to focus on this week, scanning for hot signals,
  doing a territory health check, or deciding where to spend outreach energy.
  Triggers: score signals, territory health, what's hot, signal scan,
  prioritize accounts, rank accounts, territory snapshot, hot accounts.
version: 1.0.0
user-invocable: true
---

# Signal Scoring

**Purpose:** Surface the right accounts at the right time. Not all signals are equal.
ICP tier × signal urgency = prioritization.

**Input:** `memory/icp-matrix.md` (tier weights) + web research per account + existing research files
**Output:** `memory/territory-signals.md` — overwrite with each run

---

## STEP 0 — Confirm Scope

1. **Full territory sweep:** "Score my territory" or "What's hot this week?"
   → Run signal scan across all Tier 1 and Tier 2 accounts from icp-matrix.md
2. **Single account:** "Score signals for [company]"
   → Run signal scan for that account only

---

## STEP 1 — Load ICP Tiers

Read `memory/icp-matrix.md` → extract the Account Tiers table.

If icp-matrix.md doesn't exist → run `/icp-matrix-builder` first, then return here.

**Tier weighting for signal priority:**
- Tier 1 (score 80+): All signals = urgent
- Tier 2 (score 60–79): All signals = high
- Tier 3 (score 40–59): Only strong signals (score 15+) = medium
- Tier 4 (below 40): Only hiring surge or funding (score 20+) = low

---

## STEP 2 — Scan for Signals

For Tier 1 and Tier 2 accounts, run fresh web research.

**Full mode (Bright Data):** Per account, run:
```
"{Company} news announcement 2026"
"{Company} hiring {{SOLUTION_CATEGORY}} engineer 2026"
"{Company} funding investment 2026"
"{Company} leadership change CTO VP 2026"
```

**Lite mode (WebSearch):** Same queries via WebSearch tool.

**Also check existing research files:**
`accounts/{account}/research/` → read latest file for any signals already captured.

---

## STEP 3 — Signal Taxonomy and Scoring

For each signal found, score it using this taxonomy:

| Signal Type | Base Score | Urgency Window | Why It Matters |
|-------------|-----------|----------------|----------------|
| Funding round (Series A+) | 22 | 0–60 days | New budget, new mandate, new velocity |
| Leadership change (CTO/VP/Architect hired) | 20 | 0–90 days | New leader evaluates everything in first 90 days |
| Active hiring surge (5+ relevant roles) | 18 | 0–60 days | Growth = new projects = new spend |
| Product launch announced | 18 | 0–30 days | Launch creates immediate tech decisions |
| Competitor's product gap announced | 17 | 0–45 days | Window to position before they solve it internally |
| Reorg / restructuring news | 15 | 0–60 days | Change = evaluation opportunities |
| Conference speaking appearance | 14 | 0–30 days before | Warm outreach referencing their talk |
| Engineering blog post about relevant pain | 14 | 0–21 days | Author = warm outreach target |
| Job posting mentioning pain/competitor tool | 13 | Open while posting exists | Architecture decision in progress |
| Expansion to new market / geo | 12 | 0–90 days | New operations = new systems |
| New partnership announced | 10 | 0–60 days | May change stack or create integration need |
| Contract renewal timing (if known) | 20 | 60–90 days before | Evaluation window |

**Apply ICP tier multiplier:**
- Tier 1: score × 1.3 (round up)
- Tier 2: score × 1.0
- Tier 3: score × 0.7
- Tier 4: score × 0.4

**Final signal score = base × tier multiplier**

---

## STEP 4 — Build Territory Health Snapshot

```markdown
# Territory Signals — {YYYY-MM-DD}

## Priority Queue (score 18+, Tier 1-2 accounts)

| Account | Tier | Signal | Signal Score | Urgency Window | Recommended Action |
|---------|------|--------|-------------|----------------|-------------------|
| | | | | | |

## Watch List (score 12–17)

| Account | Tier | Signal | Score | Window | Notes |
|---------|------|--------|-------|--------|-------|

## Territory Health

| Metric | Count |
|--------|-------|
| Total accounts tracked | |
| Tier 1 accounts | |
| Tier 2 accounts | |
| Active signals (score 12+) | |
| Hot signals (score 18+) | |
| Accounts with no recent signal | |

## Suppression List
[Accounts not to contact — DNC, AE-owned, just-closed, etc.]

| Account | Reason | Until |
|---------|--------|-------|

## Recommended Focus This Week
1. [Account — Signal — Specific action]
2. [Account — Signal — Action]
3. [Account — Signal — Action]
```

---

## STEP 5 — Save

**Save to:** `memory/territory-signals.md` (overwrite — this is a current-state snapshot)
**Update:** `memory/account-intel.md` → Key Dates section for any time-sensitive signals (funding, leadership change)

---

## Quality Gates

- [ ] ICP tiers loaded from memory/icp-matrix.md
- [ ] At least Tier 1 + Tier 2 accounts scanned for signals
- [ ] Signal scores calculated with tier multiplier applied
- [ ] Suppression list checked — no flagged accounts in priority queue
- [ ] Priority queue (score 18+) complete
- [ ] Territory health metrics calculated
- [ ] Recommended actions are specific (not generic "reach out")
- [ ] Output saved to memory/territory-signals.md
