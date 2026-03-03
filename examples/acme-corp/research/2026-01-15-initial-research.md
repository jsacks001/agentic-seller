# Acme Corp — Research
**Date:** 2026-01-15 | **Mode:** Full (Bright Data)

---

## 2026 Key Signals

- **Series C closed Jan 2026:** $45M raised. Lead investor: Tier One Partners. "Building the next generation developer platform." (TechCrunch, Jan 8 2026)
- **Engineering hiring surge:** 12 open roles including Senior Backend Engineers (3), Staff Engineer — Platform (1), and Lead Architect. All mention "high-scale distributed systems." (LinkedIn, Jan 15 2026)
- **New product announced:** "Acme Developer Hub" — a unified API gateway + observability platform. Blog post from CTO Marcus Torres: "We're rethinking the developer experience from the data layer up." (acmecorp.io/blog, Jan 12 2026)
- **Elasticsearch frustration signal:** Stack Overflow question from an Acme Corp engineer: "Best way to sync Postgres → Elasticsearch without 2-hour lag?" Posted Jan 5 2026. 47 views.

---

## Company Overview

Acme Corp builds a developer platform for API management and observability, targeting engineering teams at B2B SaaS companies. Founded 2019, ~280 employees, ~80 engineers. Series C ($45M, Jan 2026). HQ: Austin, TX. Customers include mid-size SaaS companies and scale-ups.

---

## Tech Stack (Confirmed)

| System | Technology | Source |
|--------|-----------|--------|
| Primary DB | PostgreSQL (AWS RDS) | Job posting mentions "PostgreSQL at scale", Jan 2026 |
| Search | Elasticsearch (self-managed) | Stack Overflow post from Acme engineer, Jan 2026 |
| Cache | Redis | Job posting requirement |
| Cloud | AWS (primary) | Multiple job postings |
| Languages | Go, TypeScript | GitHub repos (public) |
| Infra | Kubernetes on EKS | Job posting: "experience with EKS required" |

---

## Leadership Contacts

| Name | Title | Relevance | Source |
|------|-------|-----------|--------|
| Marcus Torres | CTO | Decision maker — authored "data layer" blog post | acmecorp.io/blog |
| Sarah Chen | VP Engineering | Day-to-day technical decisions, likely champion path | LinkedIn |
| Jamie Rodriguez | Lead Architect — Platform | Owns database and infra decisions | LinkedIn |
| Alex Kim | Head of DevOps | Owns operational complexity pain | LinkedIn |

---

## People Publishing About Relevant Topics

| Name | Title | Topic | Link | Why It Matters |
|------|-------|-------|------|----------------|
| Marcus Torres | CTO | "Rethinking the developer experience from the data layer up" | acmecorp.io/blog/developer-hub | He's thinking about data architecture — warm outreach angle |

---

## AI / Tech Job Postings (Architecture Intelligence)

| Role | Tools Mentioned | Posted | Implication |
|------|----------------|--------|-------------|
| Staff Engineer — Platform | "PostgreSQL at scale, experience with schema migrations" | Jan 10 2026 | Schema migration pain confirmed — it's a recurring problem |
| Senior Backend Engineer | "Elasticsearch, search infrastructure" | Jan 12 2026 | Elasticsearch debt — separate search system being managed |
| Lead Architect | "Distributed data systems, unified data layer" | Jan 14 2026 | "Unified data layer" in JD = they're thinking about consolidation |

---

## Pain Signals (Research-Confirmed)

1. **Schema migration bottleneck** → Job posting explicitly lists "experience with schema migrations" as required skill. Stack Overflow question from Acme engineer complaining about sync lag. Source: LinkedIn job posting (Jan 10) + Stack Overflow (Jan 5 2026)

2. **Elasticsearch operational overhead** → Separate self-managed Elasticsearch cluster for search. Engineer asking about sync issue = active pain, not theoretical. Source: Stack Overflow (Jan 5 2026) + job posting (Jan 12 2026)

3. **"Unified data layer" intent signal** → CTO's blog + Lead Architect JD both use "unified data layer" language — they are actively thinking about this. Source: acmecorp.io/blog (Jan 12) + LinkedIn job posting (Jan 14 2026)

---

## Sales Opportunity Analysis

**FITS Score:** 84/100 | **ICP Tier:** 1

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| F — Firmographic | 21/25 | B2B SaaS DevTools, ~80 engineers, Series C — perfect profile |
| I — Intent | 22/25 | 3 confirmed pain signals, "unified data layer" in job posting = active evaluation |
| T — Timing | 22/25 | Series C just closed + hiring surge + new product = urgent window |
| S — Solution Match | 19/25 | Schema flexibility + unified search/operational = strong match, need to confirm use case fit |

**Sales Motion Route:** Sprint (engaged VP Eng, clear pain, budget exists post-Series C)
**Value Driver:** Go Fast — eliminate schema migration bottleneck, consolidate search
**Why Anything:** "Schema migrations block engineering 1-2 weeks per feature" — productivity cost is real and recurring
**Why {{PRODUCT_NAME}}:** Flexible document model eliminates rigid schema; unified search + operational data eliminates Elasticsearch sync
**Why Now:** $45M raised, 12 open engineering roles, new "Developer Hub" product — they're building now

---

## Top 3 Outreach Hooks

1. **For Marcus Torres (CTO):** His Jan 12 blog post uses "data layer" language → he's already thinking about this. "Saw your post about rethinking the data layer — teams building unified developer platforms hit schema migration bottlenecks at exactly your stage. Worth 20 min?"

2. **For Sarah Chen (VP Eng):** 12 engineering roles + job posting mentions schema migrations → hiring to solve the problem manually. "You're hiring to solve schema migration overhead. There's a different approach — [comparable company] eliminated 90% of migration effort by changing the data model, not the team size."

3. **For Jamie Rodriguez (Lead Architect):** "Unified data layer" in the job posting he likely wrote → he's the one feeling the pain. Technical peer-level conversation about document model vs. relational for their use case.

---

## Recommended First Contact

**Who:** Sarah Chen — VP Engineering
**Channel:** LinkedIn → then email
**Hook:** Series C + hiring surge + schema migration job posting signal
**CTA:** 20-min intro call

---

## Sources

- TechCrunch: "Acme Corp raises $45M Series C" — Jan 8 2026
- acmecorp.io/blog: "Rethinking the developer experience from the data layer up" — Jan 12 2026
- LinkedIn job postings (Jan 10–14 2026): Staff Engineer Platform, Senior Backend Engineer, Lead Architect
- Stack Overflow: Acme engineer question on Postgres/Elasticsearch sync — Jan 5 2026
- LinkedIn profiles: Marcus Torres, Sarah Chen, Jamie Rodriguez, Alex Kim
