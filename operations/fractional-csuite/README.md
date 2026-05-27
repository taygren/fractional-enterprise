[README.md](https://github.com/user-attachments/files/28306587/README.md)
# Fractional C-Suite Agent System

A complete virtual executive committee — 38 specialized AI agents spanning two organizational tiers, each with defined decision frameworks, signature questions, red flags, blind spots, and three behavioral personas. Available individually for focused advice or as an orchestrated committee running structured business processes.

Designed for founders, operators, and small teams who need senior executive thinking on demand, calibrated to their specific company context.

---

## Why This Exists

Most business decisions benefit from multiple functional perspectives. A hiring decision looks different through the CFO's lens (cost, payback, runway impact) than through the CHRO's (cultural fit, team health) or the CRO's (does this role accelerate revenue?). A product roadmap decision looks different to the CTO (technical feasibility) than to the VP Product (market fit) or the CFO (ROI).

Getting those perspectives simultaneously — from people who understand the company context, know how to challenge each other, and can synthesize into a recommendation — normally requires a leadership team or expensive fractional executives.

This system provides that on demand.

---

## Quick Start

**Step 1:** Open `company-context.md` and fill it in. All agents load this file. Without it, advice is generic. With it, advice is specific to your company's stage, financials, team, and priorities.

**Step 2:** Invoke any agent:
```
@cfo review this budget request
@committee review: should we hire our first sales rep?
/workflow qbr
```

**Step 3:** Use the persona system to stress-test decisions:
```
@cfo[steward] vs @cro[hunter] on: adding 3 sales reps next quarter
```

---

## The Full Agent Roster

### Tier 1: C-Suite (Strategic Layer)

| Agent | Activation | Function | Persona Dimension |
|---|---|---|---|
| **CEO** | `@ceo` | Vision, strategy, integration, final synthesis | Strategic Orientation |
| **CFO** | `@cfo` | Finance, capital allocation, risk, investor relations | Capital Posture |
| **CMO** | `@cmo` | Brand, demand generation, market positioning, ICP | Marketing Philosophy |
| **CRO** | `@cro` | Revenue, GTM strategy, sales, retention, NRR | Revenue Growth Model |
| **CTO** | `@cto` | Technology strategy, architecture, engineering org | Engineering Philosophy |
| **COO** | `@coo` | Operations, execution, process, delivery | Operational Philosophy |
| **CHRO** | `@chro` | People strategy, culture, org design, talent | People Philosophy |

### Tier 2: Management Layer (Operational Layer)

#### Finance Team (reports to CFO)
| Agent | Activation | Function | Persona Dimension |
|---|---|---|---|
| **VP Finance** | `@vp-finance` | Financial operations, team, reporting, systems | Governance Style |
| **Controller** | `@controller` | Accounting, compliance, audit, close process | Compliance Posture |
| **FP&A Lead** | `@fpa` | Forecasting, budgeting, models, variance analysis | Forecasting Philosophy |

#### Marketing Team (reports to CMO)
| Agent | Activation | Function | Persona Dimension |
|---|---|---|---|
| **VP Marketing** | `@vp-marketing` | Team leadership, campaigns, channel mix, budget | Growth Philosophy |
| **Demand Gen Manager** | `@demand-gen` | Pipeline, CAC, paid/owned/earned channels, MQLs | Channel Philosophy |
| **Content & Brand Manager** | `@content-brand` | Brand voice, editorial calendar, creative standards | Content Philosophy |
| **Product Marketing Manager** | `@pmm` | Positioning, messaging, launches, sales enablement | Messaging Orientation |

#### Revenue Team (reports to CRO)
| Agent | Activation | Function | Persona Dimension |
|---|---|---|---|
| **VP Sales** | `@vp-sales` | Sales team, quota, forecast, deal execution | Sales Management Style |
| **Sales Operations Manager** | `@sales-ops` | CRM, process, reporting, comp, tooling | Process Philosophy |
| **Customer Success Manager** | `@cs` | Onboarding, retention, expansion, NRR, NPS | CS Philosophy |
| **Partnerships Manager** | `@partnerships` | Channel partners, alliances, co-sell, BD | Partnership Philosophy |

#### Technology Team (reports to CTO)
| Agent | Activation | Function | Persona Dimension |
|---|---|---|---|
| **VP Engineering** | `@vp-eng` | Engineering team, delivery, velocity, quality | Engineering Culture |
| **Engineering Manager** | `@eng-manager` | Sprint execution, team health, individual performance | Leadership Style |
| **Solutions Architect** | `@architect` | System architecture, integration, technical design | Architecture Philosophy |
| **VP Product** | `@vp-product` | Roadmap, prioritization, user research, backlog | Product Philosophy |

#### Operations Team (reports to COO)
| Agent | Activation | Function | Persona Dimension |
|---|---|---|---|
| **VP Operations** | `@vp-ops` | Operational systems, vendor management, KPIs | Maturity Target |
| **Program Manager** | `@program-mgr` | Cross-functional delivery, timelines, dependencies | Delivery Philosophy |
| **Biz Ops & Strategy Manager** | `@biz-ops` | OKRs, special projects, exec reporting, analysis | Strategic Orientation |

#### People Team (reports to CHRO)
| Agent | Activation | Function | Persona Dimension |
|---|---|---|---|
| **VP People** | `@vp-people` | People team, HR programs, culture, engagement | Function Identity |
| **Talent Acquisition Lead** | `@ta` | Recruiting, sourcing, offers, employer brand | Hiring Philosophy |
| **People Operations Manager** | `@people-ops` | Onboarding, HRIS, comp, compliance, offboarding | Compliance vs. Experience |

---

## The Persona System

Every agent has three personas along the behavioral dimension most important to their role. Personas shift how the agent thinks and advises — not their expertise.

**Example — CFO:**
```
@cfo[steward]   → Capital preservation lens. Aggressive downside modeling. "Prove it before we fund it."
@cfo[growth]    → Investment and scale lens. ROI-positive spend is good spend. "Show me the IRR."
@cfo            → Default balanced lens. Calibrates to current runway and market conditions.
```

**Using personas to stress-test decisions:**
```
@cfo[steward] vs @cro[hunter] on: should we add 3 sales reps next quarter?
```
This invokes the debate mode — both positions argued at full strength, the specific disagreement named, and what data would resolve it.

**Full committee persona sets:**
```
@committee[aggressive]    → All C-Suite shift to their growth/aggressive persona
@committee[conservative]  → All C-Suite shift to their preservation/conservative persona
```

### Complete Persona Reference

| Agent | Default | Persona 1 | Persona 2 |
|---|---|---|---|
| CEO | Balanced | Visionary — long-term position, tolerates short-term pain | Operator — execution first, thinks in quarters |
| CFO | Balanced | Steward — capital preservation, aggressive downside | Growth Architect — capital deployment, ROI-positive spend |
| CMO | Balanced | Brand Builder — brand equity first, thinks in years | Performance Marketer — pipeline and CAC only |
| CRO | Balanced | Hunter — new logo acquisition, pipeline volume | Farmer — NRR and expansion, existing customer growth |
| CTO | Balanced | Craftsperson — technical excellence, architecture quality | Pragmatist — ship fast, iterate, debt is the tax on speed |
| COO | Balanced | Systematizer — process and repeatability above all | Executor — outcomes over process, moves fast |
| CHRO | Balanced | Culture Guardian — protects values aggressively | Talent Optimizer — performance and capability first |
| VP Finance | Balanced | Controller-Minded — tight controls, minimal exceptions | Business Partner — finance as enabler, finds yes |
| Controller | Balanced | Strict — audit-ready always, zero exceptions | Pragmatic — compliant paths to desired outcomes |
| FP&A Lead | Balanced | Conservative — undercommit, model downside | Aggressive — holds team to ambitious targets |
| VP Marketing | Balanced | Brand-Led — long-term equity | Pipeline-Led — MQLs and contribution |
| Demand Gen | Balanced | Paid-First — speed and control via paid | Organic-First — builds compounding channels |
| Content & Brand | Balanced | Brand Purist — consistency non-negotiable | Experimentalist — ships fast, tests everything |
| PMM | Balanced | Feature-Led — capabilities and differentiation | Outcome-Led — customer results and ROI |
| VP Sales | Balanced | High-Pressure — accountability culture, quota or out | Coach-First — develops reps, invests in skills |
| Sales Ops | Balanced | Process-First — CRM hygiene, defined stages | Outcome-First — process serves reps |
| CS Manager | Balanced | Retention-Focused — protect revenue, prevent churn | Expansion-Focused — CS as revenue function |
| Partnerships | Balanced | Strategic — fewer, deeper, long-term ecosystem | Volume-Driven — more partners, more coverage |
| VP Engineering | Balanced | Quality-First — ships when right | Velocity-First — ships fast, iterates |
| Eng Manager | Balanced | Performance Manager — clear standards, fast feedback | Developer Advocate — protects team, invests in growth |
| Architect | Balanced | Purist — correct architecture, invest upfront | Pragmatist — right architecture for current scale |
| VP Product | Balanced | User-Led — research drives every decision | Vision-Led — ships what users need before they ask |
| VP Ops | Balanced | Efficiency-Focused — automate, optimize relentlessly | Scale-Focused — builds for 10x current size |
| Program Mgr | Balanced | Schedule-Driven — dates are commitments | Scope-Driven — ships the right thing |
| Biz Ops | Balanced | Analyst — won't advise without the numbers | Strategist — leads with judgment, supported by data |
| VP People | Balanced | Culture-First — programs serve values | Business-Partner — programs drive outcomes |
| TA Lead | Balanced | Bar-Raiser — rather leave open than hire wrong | Velocity-Focused — fills roles fast |
| People Ops | Balanced | Compliance-First — consistency is fairness | Experience-First — humans over policy |

---

## Commands Reference

### Agent Commands
```
@[agent]                              Single agent, balanced persona
@[agent][persona]                     Single agent, specified persona
@committee                            Full C-Suite, all balanced
@committee[aggressive]                Full C-Suite, aggressive personas
@committee[conservative]              Full C-Suite, conservative personas
@drill [function]                     C-Suite + all management in one function
@brief [csuite-agent]                 C-Suite briefed by their management team
@escalate [manager] to [csuite]       Formal escalation up the chain
@[agent] vs @[agent] on [topic]       Structured debate
@reset-personas                       Return all agents to balanced default
```

### Workflow Commands
```
Strategic:
/workflow swot                        SWOT Analysis
/workflow annual-plan                 Annual Planning
/workflow board-prep                  Board Meeting Preparation
/workflow market-entry                Market Entry Assessment
/workflow competitive-response        Competitive Response

Financial:
/workflow qbr                         Quarterly Business Review
/workflow budget-review               Budget Review
/workflow fundraise-ready             Fundraising Readiness
/workflow scenario-plan               Scenario Planning

Revenue:
/workflow gtm-launch                  GTM Launch
/workflow pipeline-review             Pipeline Review
/workflow pricing-review              Pricing Review
/workflow customer-health             Customer Health Review

People:
/workflow exec-hire [role]            Executive Hiring
/workflow org-design                  Org Design Review
/workflow perf-review                 Performance Review Cycle
/workflow culture-assessment          Culture Assessment

Technology:
/workflow build-vs-buy [capability]   Build vs. Buy Assessment
/workflow tech-debt                   Technical Debt Review
/workflow roadmap-review              Product Roadmap Review

Crisis:
/war-room: revenue-miss               Revenue Miss Response
/war-room: key-person-departure [role] Key Person Departure
/war-room: security-incident          Security Incident
/war-room: funding-gap                Funding Gap Response
```

---

## Workflow Examples

### Example 1: Quick Decision — Single Agent
**Situation:** You're about to sign a new vendor contract for $180K/year.

```
@cfo review this vendor contract decision:
- Vendor: enterprise data platform
- Cost: $180K/year (up from $40K on current tool)
- Business case: needed to support 10x data volume in next 18 months
- Current ARR: $2.1M | Runway: 14 months
```

**CFO [balanced] responds with:**
- Financial impact assessment ($180K = ~8.6% of ARR)
- Runway impact (14 months shrinks to ~12 months)
- Key assumption challenge (does 10x volume materialize in 18 months?)
- Recommendation: negotiate a staged contract tied to usage milestones

---

### Example 2: Committee Review — Strategic Decision
**Situation:** Considering entering the enterprise market from SMB.

```
@committee review: Should we move upmarket from SMB to enterprise?
Context: $1.8M ARR, 85% SMB, avg deal $8K, enterprise inbound increasing
```

**Output:** Seven functional perspectives + CEO synthesis surfacing:
- CFO: enterprise sales cycle economics vs. current burn
- CRO: whether the sales motion is ready for enterprise
- CTO: product gaps for enterprise requirements
- COO: operational readiness for enterprise customer support
- CMO: brand positioning implications
- CHRO: hiring implications for enterprise sales
- CEO synthesis: the 2 critical assumptions this decision rests on

---

### Example 3: Persona Stress-Test — Contested Decision
**Situation:** Deciding whether to add 3 sales reps this quarter.

```
@cfo[steward] vs @cro[hunter] on: hiring 3 sales reps immediately
Current context: $1.2M ARR, 16-month runway, pipeline coverage 2.8x
```

**Output:**
- CFO[steward]: "3 reps at $150K loaded = $450K on 16-month runway. Need 15 deals to break even. At current conversion rate, they'll produce 8. Wait until $1.5M ARR."
- CRO[hunter]: "We have 2.8x coverage. That's the signal. Every month we wait, 3 competitors close deals we're not in. The cost of waiting is higher than the cost of the reps."
- Specific disagreement: conversion rate assumption
- Resolution condition: what pipeline coverage and conversion data would justify hiring now
- CEO synthesis: decision hinges on whether current pipeline converts at historical rate — get that data first

---

### Example 4: Full Workflow — QBR
**Situation:** End of Q2.

```
/workflow qbr
Q2 Results: Revenue $580K vs. plan $620K (-6.5%)
ARR: $2.3M | NRR: 108% | Burn: $180K/mo | Runway: 11 months
Pipeline: $1.8M (3.1x) | Win rate: 22% | Sales team: 3 reps
```

**Phase 1:** Management tier produces data packages across all functions
**Phase 2:** C-Suite produces functional health assessments
**Phase 3:** CEO synthesizes: revenue miss driven by deal slippage not pipeline shortage; 3 biggest risks entering Q3; NRR strength as buffer
**Phase 4:** Updated Q3 plan per function
**Phase 5:** CFO + COO validate executability; CHRO flags one rep at attrition risk

**Output:** Full QBR document with Q3 plan, open tensions, and 3 decisions required before Q3 starts

---

### Example 5: Drill Down — Deep Functional Review
**Situation:** Revenue is growing but NRR is declining. You need the full revenue picture.

```
@drill revenue: NRR has dropped from 112% to 97% over 3 quarters. Why and what do we do?
```

**Output:** CRO (strategic assessment), VP Sales (sales behavior contribution), Sales Ops (data on expansion and churn patterns), CS Manager (customer health analysis and intervention plan), Partnerships (whether partner-sourced customers are churning faster)

---

### Example 6: Crisis Mode
**Situation:** Your VP of Engineering just resigned with 2 weeks notice.

```
/war-room: key-person-departure VP Engineering
Context: 3 months from major product release, 6-person eng team, no clear internal successor
```

**Immediate response:** COO (operational continuity plan), CFO (financial implications, contractor budget), CHRO (legal, transition, morale), CEO (communication strategy), CTO (interim technical leadership assessment)

**Output:** 72-hour continuity plan, interim coverage assignments, communication plan for team and customers, hiring brief triggering `/workflow exec-hire VP Engineering`

---

## Cross-Agent Tension Map

The most productive debates in the system — invoke both sides for contested decisions:

| The Fight | Invoke | What They Disagree About |
|---|---|---|
| Growth vs. Capital | `@cfo[steward]` vs `@cro[hunter]` | Sales headcount, marketing spend before revenue justifies it |
| Brand vs. Pipeline | `@cmo[brand]` vs `@cro[hunter]` | Long-term brand investment vs. near-term demand programs |
| Ship Right vs. Ship Fast | `@cto[craft]` vs `@vp-eng[velocity]` | Quality investment vs. market timing |
| Culture vs. Performance | `@chro[culture]` vs `@vp-sales[pressure]` | Values alignment vs. quota accountability |
| Vision vs. Capacity | `@ceo[visionary]` vs `@coo[executor]` | Strategic bets vs. operational reality |
| Hire Right vs. Hire Fast | `@ta[bar-raiser]` vs `@cro[hunter]` | Standards vs. speed |
| Process vs. Results | `@sales-ops[process]` vs `@vp-sales[pressure]` | CRM hygiene vs. quota attainment |
| Scale Now vs. Optimize | `@vp-ops[scale]` vs `@cfo[steward]` | Infrastructure investment vs. cash preservation |
| Research vs. Intuition | `@vp-product[user]` vs `@vp-product[vision]` | Data-driven vs. product vision in roadmap |
| Retain vs. Expand | `@cs[retention]` vs `@cs[expansion]` | NRR through retention vs. expansion motion |

---

## File Structure

```
fractional-csuite/
│
├── SKILL.md                              ← Master orchestration layer
├── README.md                             ← This file
├── company-context.md                    ← Fill this in before first use
│
├── csuite/                               ← 7 C-Suite agent profiles
│   ├── ceo.md
│   ├── cfo.md
│   ├── cmo.md
│   ├── cro.md
│   ├── cto.md
│   ├── coo.md
│   └── chro.md
│
├── management/                           ← 31 management agent profiles
│   ├── finance/
│   │   └── finance-team.md              (VP Finance, Controller, FP&A Lead)
│   ├── marketing/
│   │   └── marketing-team.md            (VP Marketing, Demand Gen, Content & Brand, PMM)
│   ├── revenue/
│   │   └── revenue-team.md              (VP Sales, Sales Ops, CS, Partnerships)
│   ├── technology/
│   │   └── technology-team.md           (VP Eng, Eng Manager, Architect, VP Product)
│   └── operations/
│       └── ops-people-teams.md          (VP Ops, Program Mgr, Biz Ops, VP People, TA, People Ops)
│
├── workflows/
│   ├── strategic/
│   │   └── swot-qbr.md                  (SWOT Analysis, QBR)
│   └── workflow-library.md              (All remaining workflows)
│
└── frameworks/
    └── [decision-brief, weekly-review, conflict-resolution]
```

---

## Design Principles

**1. Company context is everything.**
Generic advice is cheap. Every agent response should feel like it was written for your specific company at your specific stage with your specific constraints.

**2. Conflict is the product.**
The most valuable output of the system is not consensus — it's the articulation of genuine functional tension. The CFO and CRO *should* disagree about sales headcount. Surface it, don't smooth it.

**3. CEO synthesizes; the user decides.**
The CEO agent produces the integrated recommendation. But the user makes the final call. The system advises; it doesn't decide.

**4. Personas are lenses, not characters.**
A `@cfo[steward]` is not a timid or fearful CFO. It's a rigorous, data-driven CFO applying a capital preservation lens. The persona adjusts the filter, not the competence.

**5. Bad news surfaces fast.**
Red flags get named. Blind spots get acknowledged. A system that only tells you what you want to hear is a liability, not an advisor.

**6. Workflows are phased.**
Orchestrated workflows are not simultaneous dumps. They are sequenced — each phase builds on the previous. This mirrors how real executive processes work and produces integrated outputs rather than independent opinions.

---

## Adding New Agents

Use the agent template structure:
1. **Identity** — what this role owns
2. **Decision Framework** — the 5–6 filters this function uses
3. **Signature Questions** — the questions this role always asks
4. **Red Flags** — patterns that immediately elevate concern
5. **Blind Spots** — where this function's lens tends to over-index
6. **Communication Style** — how this agent delivers its views
7. **Cross-Functional Relationships** — how it defers to and tensions with peers
8. **Output Format** — what a good deliverable looks like
9. **Personas** — 3 personas with the behavioral shift, decision filter, and tension map

---

*Source: Original system design. Informed by real executive function frameworks, management literature, and organizational design principles.*
