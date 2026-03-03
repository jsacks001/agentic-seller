---
name: objection-mining
description: |
  Aggregates objections from call notes across territory. Builds a living response library.
  Use when: logging a new objection, reviewing objection patterns, building response templates,
  or understanding what pushback is most common in your territory.
  Triggers: log objection, objection library, common pushback, what objections,
  track objection, objection pattern, add to objection library, objection trend,
  what are they pushing back on.
version: 1.0.0
user-invocable: true
---

# Objection Mining

**Purpose:** Turn individual objections from every call into a territory-wide pattern library.
Every call is a data point. This skill is what connects them.

**Input source:** `## Objections Logged` sections in all `accounts/*/discovery/` files.
**Output:** `memory/objection-library.md` — append only, never overwrite.

---

## STEP 0 — Confirm Scope

1. **Single account:** "Log the objection from my last call with [company]"
   → Read the most recent `discovery/` file for that account only
2. **Territory sweep:** "Update my objection library" or "What are they pushing back on?"
   → Scan all `accounts/*/discovery/` files

---

## STEP 1 — Scan Call Notes Files

Read all files matching `accounts/*/discovery/*.md`.

For each file, look for the `## Objections Logged` section:

```
## Objections Logged
| Type | Verbatim Quote | Stage | Response Used | Outcome |
```

If no section found in a file → skip it. If found → extract all rows.

**Objection types:** Timing / Budget / Authority / Trust / Fit / Competition

---

## STEP 2 — Parse and Classify

For each objection row extracted:
1. Confirm or correct the Type classification
2. Note the Stage (what deal stage was this objection raised at?)
3. Note the Response Used and Outcome
4. Check if this is a new objection or a variant of an existing one

**Classification guide:**

| Type | Description | Example |
|------|-------------|---------|
| Timing | "Not now" — they're not ready to act | "We're heads-down on a product launch until Q3" |
| Budget | Cost or prioritization block | "No budget allocated for this this year" |
| Authority | Wrong level — needs escalation or different contact | "I'd need to check with my manager" |
| Trust | Skepticism about claims, product, or vendor | "We've heard this before and it didn't deliver" |
| Fit | Genuine mismatch concern | "We're too small / too big for this" |
| Competition | Evaluating or committed to an alternative | "We're already deep into evaluating [competitor]" |

---

## STEP 3 — Aggregate into Library

Read `memory/objection-library.md` (create if doesn't exist).

For each objection:
- Find the matching entry in the library, or create a new one
- Increment count
- Add the new verbatim quote to the examples list
- Update win/loss pattern if outcome is known

**Library format:**

```markdown
# Objection Library
*Last updated: YYYY-MM-DD | {N} objections tracked | {N} accounts*

---

## Timing Objections
**Count:** {N} | **Win rate:** {N}% | **Most common stage:** {stage}

### Most Common Responses (by win rate)
1. [Response that worked — with example]
2. [Second best response]

### Verbatim Quotes (latest 5)
- "[Quote]" — {Company}, {Stage}, {Date}
- ...

---

## Budget Objections
[Same structure]

## Authority Objections
[Same structure]

## Trust Objections
[Same structure]

## Fit Objections
[Same structure]

## Competition Objections
[Same structure]

---

## Top 5 Objections by Frequency

| Rank | Objection | Type | Count | Win Rate | Best Response |
|------|-----------|------|-------|----------|--------------|
| 1 | | | | | |
```

---

## STEP 4 — Generate Response Templates

For any objection type where:
- Count ≥ 3 AND
- No "Best Response" is documented yet

→ Generate a response template using the AAA framework:

```
Type: [Timing/Budget/Authority/Trust/Fit/Competition]
Objection pattern: "[Common version of this objection]"

AAA Response:
- Acknowledge: "[Validate without agreeing]"
- Ask: "[Reframe question to understand root cause]"
- Advance: "[Earn the next 30 seconds]"

Outcome goal: [What constitutes a win for this objection]
```

---

## STEP 5 — Save to Memory

**Append to** `memory/objection-library.md` — never overwrite the full file.
Update only the sections with new data.

Also update `memory/account-intel.md` → Objection Patterns section if a new territory-wide pattern emerges.

---

## Quality Gates

- [ ] All `discovery/` files scanned for `## Objections Logged` sections
- [ ] Each objection type-classified correctly
- [ ] Frequency counts updated
- [ ] Win rate updated where outcome is known
- [ ] Response templates generated for objection types with 3+ examples and no template
- [ ] `memory/objection-library.md` updated (append only)
- [ ] Top 5 objections by frequency table updated
