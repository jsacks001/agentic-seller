# Account Brief — Acme Corp
*Living document. Updated after every interaction.*

**Last Updated:** 2026-01-22
**Stage:** Discovery

---

## Company Snapshot

| Field | Value |
|-------|-------|
| Company | Acme Corp |
| Industry | B2B SaaS — DevTools |
| Size | ~280 employees, ~80 engineers |
| Stage | Series C ($45M raised Jan 2026) |
| HQ | Austin, TX |
| Website | acmecorp.io |
| Tech Stack (confirmed) | PostgreSQL (primary), Elasticsearch (search), Redis (cache), AWS |
| Cloud Provider | AWS |
| CRM Record | Exists — no open opportunity |

---

## Qualification Status (MEDDPICC)

| Letter | Question | Status | Evidence | Date |
|--------|----------|--------|----------|------|
| M — Metrics | What numbers change if they fix this? | 🎯 Probing | Engineering mentioned "weeks of schema migration time" — no dollar figure yet | 2026-01-20 |
| E — Economic Buyer | Who approves budget? | ⬜ Unknown | Sarah (VP Eng) likely has budget authority but hasn't confirmed | |
| D — Decision Criteria | How will they evaluate? | ⬜ Unknown | Not yet discussed | |
| D — Decision Process | Steps to get to yes? | ⬜ Unknown | Not yet discussed | |
| P — Paper Process | Procurement / legal / security? | ⬜ Unknown | Not yet discussed | |
| I — Identified Pain | What specific pain? | ✅ Confirmed | "Every new feature requires a schema migration that blocks the team for 1-2 weeks." — Sarah Chen, 2026-01-20 | 2026-01-20 |
| C — Champion | Who advocates internally? | 🎯 Probing | Sarah Chen (VP Eng) is engaged but not yet confirmed champion | |
| C — Competition | What else evaluating? | ⬜ Unknown | Not yet discussed — likely on PostgreSQL roadmap | |

**Qual score:** 2/8 confirmed + 2 probing

---

## 3 Whys

| Why | Status | Evidence |
|-----|--------|----------|
| Why Anything | ✅ Confirmed | "Schema migrations block the team 1-2 weeks per feature" — real, painful, recurring |
| Why {{PRODUCT_NAME}} | 🎯 Probing | Flexible document model eliminates rigid schema — demo needed |
| Why Now | 🎯 Probing | Series C funding ($45M, Jan 2026) + hiring surge (12 engineering roles open) = new projects starting |

---

## Key Contacts

| Name | Title | Relationship | Last Contact | LinkedIn |
|------|-------|-------------|--------------|----------|
| Sarah Chen | VP Engineering | Warm — 2 calls | 2026-01-20 | linkedin.com/in/sarah-chen-acme |
| Marcus Torres | CTO | Cold | Never | linkedin.com/in/marcus-torres-acme |
| Jamie Rodriguez | Lead Architect | Cold — warm intro possible via community | Never | |

---

## Outreach Log

| Date | Contact | Channel | Response | Notes |
|------|---------|---------|----------|-------|
| 2026-01-10 | Sarah Chen | LinkedIn | Accepted | Engaged with post about schema flexibility |
| 2026-01-15 | Sarah Chen | Email | Replied | Asked for 20-min call |
| 2026-01-20 | Sarah Chen | Call (25 min) | Positive | Confirmed pain. Agreed to intro Marcus |

---

## Sales Motion

**Route:** Sprint (eager VP Eng, clear pain, Series C = budget exists)
**Value Driver:** Go Fast — dev velocity, eliminate schema migration bottleneck
**Top Pain Signal:** "Schema migrations block engineering 1-2 weeks per feature" — Sarah Chen, 2026-01-20
**Top Hook:** Series C ($45M) + 12 open engineering roles = new product surface coming
**Recommended CTA:** Sprint Zero with Marcus + Sarah — 3 hours to scope migration path

---

## Next Actions

1. Get intro to Marcus Torres (CTO) from Sarah — follow up by 2026-01-25
2. Run `/discovery-prep` for AE intro call with Marcus
3. Find a proof point: Series C SaaS company that eliminated schema migration overhead

---

## Research Files
- `research/2026-01-15-initial-research.md` — initial scan
