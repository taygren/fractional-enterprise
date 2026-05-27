[README.md](https://github.com/user-attachments/files/28307382/README.md)
# Fractional Enterprise

**A complete virtual executive committee for any company.**

38 specialized AI agents across two organizational tiers — C-Suite and management — each with defined decision frameworks, signature questions, red flags, blind spots, and three behavioral personas. Use individually for focused functional advice, or run as an orchestrated committee executing structured business processes like QBRs, SWOT analyses, board prep, and crisis response.

Built for founders, operators, and teams who need senior executive thinking on demand, calibrated to their specific company context.

---

## How to Use This Repo

This system runs inside any AI platform that supports system prompts or project-level instructions (Claude Projects, ChatGPT Custom GPTs, etc.).

**Step 1 — Fill in your company context**
Open `company-context.md` and populate it with your company's current financials, GTM motion, team size, and strategic priorities. Every agent loads this file. Without it, advice is generic. With it, advice is specific to your company at your current stage.

**Step 2 — Load the skill**
Paste `SKILL.md` into your AI platform's system prompt or project instructions. This activates all agent commands and workflows.

**Step 3 — Load the agents**
Add the relevant agent files from `csuite/` and `management/` to your project knowledge base. Load all for full committee access, or load selectively for specific functions.

**Step 4 — Invoke**
```
@cfo review this budget request
@committee review: should we move upmarket?
/workflow qbr
/war-room: funding-gap
```

---

## Why This Exists

Most business decisions benefit from multiple functional perspectives simultaneously. A hiring decision looks different through the CFO's lens (cost, payback, runway) than through the CHRO's (cultural fit, team health) or the CRO's (does this role accelerate revenue?). A product roadmap decision looks different to the CTO (technical feasibility) than to the VP Product (market fit) or the CFO (ROI).

Getting those perspectives from people who understand your specific company context, know how to challenge each other, and can synthesize into a clear recommendation normally requires a full leadership team or expensive fractional executives.

This system provides that on demand.

---

## The Agent Roster

### Tier 1 — C-Suite (7 Agents)
*Strategic layer. Sets direction, integrates across functions, owns cross-functional tradeoffs.*

| Agent | Activation | Owns | Persona Dimension |
|---|---|---|---|
| **CEO** | `@ceo` | Vision, strategy, integration, final synthesis | Strategic Orientation |
| **CFO** | `@cfo` | Finance, capital allocation, risk, investor relations | Capital Posture |
| **CMO** | `@cmo` | Brand, demand generation, market positioning, ICP | Marketing Philosophy |
| **CRO** | `@cro` | Revenue, GTM strategy, sales, retention, NRR | Revenue Growth Model |
| **CTO** | `@cto` | Technology strategy, architecture, engineering org | Engineering Philosophy |
| **COO** | `@coo` | Operations, execution, process, delivery | Operational Philosophy |
| **CHRO** | `@chro` | People strategy, culture, org design, talent | People Philosophy |

---

### Tier 2 — Management (31 Agents)
*Operational layer. Executes within each function. Activates on drill, brief, or explicit invocation.*

#### Finance *(reports to CFO)*
| Agent | Activation | Owns | Persona Dimension |
|---|---|---|---|
| **VP Finance** | `@vp-finance` | Financial operations, team, reporting, systems | Governance Style |
| **Controller** | `@controller` | Accounting, compliance, audit, close process | Compliance Posture |
| **FP&A Lead** | `@fpa` | Forecasting, budgeting, models, variance analysis | Forecasting Philosophy |

#### Marketing *(reports to CMO)*
| Agent | Activation | Owns | Persona Dimension |
|---|---|---|---|
| **VP Marketing** | `@vp-marketing` | Team leadership, campaigns, channel mix, budget | Growth Philosophy |
| **Demand Gen Manager** | `@demand-gen` | Pipeline, CAC, paid/owned/earned channels, MQLs | Channel Philosophy |
| **Content & Brand Manager** | `@content-brand` | Brand voice, editorial calendar, creative standards | Content Philosophy |
| **Product Marketing Manager** | `@pmm` | Positioning, messaging, launches, sales enablement | Messaging Orientation |

#### Revenue *(reports to CRO)*
| Agent | Activation | Owns | Persona Dimension |
|---|---|---|---|
| **VP Sales** | `@vp-sales` | Sales team, quota, forecast, deal execution | Sales Management Style |
| **Sales Operations Manager** | `@sales-ops` | CRM, process, reporting, compensation, tooling | Process Philosophy |
| **Customer Success Manager** | `@cs` | Onboarding, retention, expansion, NRR, NPS | CS Philosophy |
| **Partnerships Manager** | `@partnerships` | Channel partners, alliances, co-sell, BD | Partnership Philosophy |

#### Technology *(reports to CTO)*
| Agent | Activation | Owns | Persona Dimension |
|---|---|---|---|
| **VP Engineering** | `@vp-eng` | Engineering team, delivery, velocity, quality | Engineering Culture |
| **Engineering Manager** | `@eng-manager` | Sprint execution, team health, individual performance | Leadership Style |
| **Solutions Architect** | `@architect` | System architecture, integration, technical design | Architecture Philosophy |
| **VP Product** | `@vp-product` | Roadmap, prioritization, user research, backlog | Product Philosophy |

#### Operations *(reports to COO)*
| Agent | Activation | Owns | Persona Dimension |
|---|---|---|---|
| **VP Operations** | `@vp-ops` | Operational systems, vendor management, KPIs | Maturity Target |
| **Program Manager** | `@program-mgr` | Cross-functional delivery, timelines, dependencies | Delivery Philosophy |
| **Biz Ops & Strategy Manager** | `@biz-ops` | OKRs, special projects, exec reporting, analysis | Strategic Orientation |

#### People *(reports to CHRO)*
| Agent | Activation | Owns | Persona Dimension |
|---|---|---|---|
| **VP People** | `@vp-people` | People team, HR programs, culture, engagement | Function Identity |
| **Talent Acquisition Lead** | `@ta` | Recruiting, sourcing, offers, employer brand | Hiring Philosophy |
| **People Operations Manager** | `@people-ops` | Onboarding, HRIS, comp, compliance, offboarding | Compliance vs. Experience |

---

## The Persona System

Every agent has three behavioral personas along the dimension most critical to their role. Personas shift *how* the agent thinks — not their expertise. The CFO[steward] is still a rigorous, data-driven CFO; the persona adjusts the capital lens, not the competence.

### Complete Persona Reference

| Agent | Persona 1 | Persona 2 | Default |
|---|---|---|---|
| CEO | `[visionary]` — long-term position, tolerates short-term pain | `[operator]` — execution first, thinks in quarters | `[balanced]` |
| CFO | `[steward]` — capital preservation, aggressive downside modeling | `[growth]` — ROI-positive deployment, investment lens | `[balanced]` |
| CMO | `[brand]` — brand equity first, thinks in years | `[performance]` — pipeline and CAC, thinks in weeks | `[balanced]` |
| CRO | `[hunter]` — new logo acquisition, pipeline volume | `[farmer]` — NRR and expansion, existing customer growth | `[balanced]` |
| CTO | `[craft]` — technical excellence, architecture quality | `[pragmatist]` — ship fast, iterate, debt is acceptable | `[balanced]` |
| COO | `[system]` — process and repeatability above all | `[executor]` — outcomes over process, moves fast | `[balanced]` |
| CHRO | `[culture]` — protects values aggressively | `[talent]` — performance and capability density first | `[balanced]` |
| VP Finance | `[control]` — tight governance, minimal exceptions | `[partner]` — finance as business enabler | `[balanced]` |
| Controller | `[strict]` — audit-ready always, zero exceptions | `[pragmatic]` — compliant paths to desired outcomes | `[balanced]` |
| FP&A Lead | `[conservative]` — undercommit, model downside | `[aggressive]` — holds team to ambitious targets | `[balanced]` |
| VP Marketing | `[brand]` — long-term equity investment | `[pipeline]` — MQLs and pipeline contribution only | `[balanced]` |
| Demand Gen | `[paid]` — speed and control via paid channels | `[organic]` — builds compounding owned channels | `[balanced]` |
| Content & Brand | `[purist]` — brand consistency non-negotiable | `[experiment]` — ships fast, tests everything | `[balanced]` |
| PMM | `[feature]` — capabilities and differentiation | `[outcome]` — customer results and ROI | `[balanced]` |
| VP Sales | `[pressure]` — accountability culture, quota or out | `[coach]` — develops reps, invests in skills | `[balanced]` |
| Sales Ops | `[process]` — CRM hygiene, defined stages | `[outcome]` — process serves reps, not vice versa | `[balanced]` |
| CS Manager | `[retention]` — protect revenue, prevent churn | `[expansion]` — CS as a revenue function | `[balanced]` |
| Partnerships | `[strategic]` — fewer, deeper, long-term ecosystem | `[volume]` — more partners, more coverage | `[balanced]` |
| VP Engineering | `[quality]` — ships when right | `[velocity]` — ships fast, iterates in production | `[balanced]` |
| Eng Manager | `[performance]` — clear standards, fast feedback | `[advocate]` — protects team, invests in growth | `[balanced]` |
| Architect | `[purist]` — correct architecture, invest upfront | `[pragmatist]` — right architecture for current scale | `[balanced]` |
| VP Product | `[user]` — research drives every decision | `[vision]` — ships what users need before they ask | `[balanced]` |
| VP Ops | `[efficiency]` — automate and optimize relentlessly | `[scale]` — builds for 10x current size | `[balanced]` |
| Program Mgr | `[schedule]` — dates are commitments | `[scope]` — ships the right thing, dates are targets | `[balanced]` |
| Biz Ops | `[analyst]` — won't advise without the numbers | `[strategist]` — leads with judgment, supported by data | `[balanced]` |
| VP People | `[culture]` — programs serve values | `[business]` — programs drive business outcomes | `[balanced]` |
| TA Lead | `[bar-raiser]` — rather leave open than hire wrong | `[velocity]` — fills roles fast, calibrated standards | `[balanced]` |
| People Ops | `[compliance]` — consistency is fairness | `[experience]` — humans over policy where possible | `[balanced]` |

### Invoking Personas

```
@cfo[steward]              Single agent, specific persona
@cfo                       Single agent, default balanced persona
@committee[aggressive]     Full C-Suite, all aggressive personas
@committee[conservative]   Full C-Suite, all conservative personas
@cfo[steward] vs @cro[hunter] on: [topic]    Structured debate
```

---

## Commands

### Agent Commands
```
@[agent]                              Single agent, balanced persona
@[agent][persona]                     Single agent, specified persona
@committee                            Full C-Suite committee, all balanced
@committee[persona]                   Full C-Suite, all specified persona
@drill [function]                     C-Suite + all management in one function
@brief [csuite-agent]                 C-Suite briefed by their management team
@escalate [manager] to [csuite]       Formal escalation up the chain
@[agent] vs @[agent] on [topic]       Structured debate
@reset-personas                       Return all agents to balanced default
```

### Workflow Commands
```
/workflow swot                        SWOT Analysis
/workflow annual-plan                 Annual Planning
/workflow board-prep                  Board Meeting Preparation
/workflow market-entry                Market Entry Assessment
/workflow competitive-response        Competitive Response
/workflow qbr                         Quarterly Business Review
/workflow budget-review               Budget Review
/workflow fundraise-ready             Fundraising Readiness
/workflow scenario-plan               Scenario Planning
/workflow gtm-launch                  GTM Launch
/workflow pipeline-review             Pipeline Review
/workflow pricing-review              Pricing Review
/workflow customer-health             Customer Health Review
/workflow exec-hire [role]            Executive Hiring
/workflow org-design                  Org Design Review
/workflow perf-review                 Performance Review Cycle
/workflow culture-assessment          Culture Assessment
/workflow build-vs-buy [capability]   Build vs. Buy Assessment
/workflow tech-debt                   Technical Debt Review
/workflow roadmap-review              Product Roadmap Review
```

### Crisis Commands
```
/war-room: revenue-miss               Revenue Miss Response
/war-room: key-person-departure [role] Key Person Departure
/war-room: security-incident          Security Incident
/war-room: funding-gap                Funding Gap Response
```

---

## Workflow Examples

**Single agent — quick decision:**
```
@cfo review this vendor contract:
Cost: $180K/year | Current ARR: $2.1M | Runway: 14 months
Business case: needed to support 10x data volume in 18 months
```

**Committee review — strategic decision:**
```
@committee review: Should we move upmarket from SMB to enterprise?
Context: $1.8M ARR, 85% SMB, avg deal $8K, enterprise inbound increasing
```

**Persona stress-test — contested decision:**
```
@cfo[steward] vs @cro[hunter] on: hiring 3 sales reps immediately
Context: $1.2M ARR, 16-month runway, pipeline coverage 2.8x
```

**Full workflow — end of quarter:**
```
/workflow qbr
Q2 Results: Revenue $580K vs. plan $620K | ARR: $2.3M | NRR: 108%
Burn: $180K/mo | Runway: 11 months | Pipeline: $1.8M (3.1x coverage)
```

**Drill down — deep functional review:**
```
@drill revenue: NRR has dropped from 112% to 97% over 3 quarters. Why and what do we do?
```

**Crisis mode:**
```
/war-room: key-person-departure VP Engineering
Context: 3 months from major release, 6-person eng team, no clear internal successor
```

---

## Cross-Agent Tension Map

The most productive debates — invoke both sides for contested decisions:

| The Fight | Invoke | Core Disagreement |
|---|---|---|
| Growth vs. Capital | `@cfo[steward]` vs `@cro[hunter]` | Sales headcount before revenue supports it |
| Brand vs. Pipeline | `@cmo[brand]` vs `@cro[hunter]` | Long-term brand vs. near-term demand spend |
| Ship Right vs. Ship Fast | `@cto[craft]` vs `@vp-eng[velocity]` | Quality investment vs. market timing |
| Culture vs. Performance | `@chro[culture]` vs `@vp-sales[pressure]` | Values alignment vs. quota accountability |
| Vision vs. Capacity | `@ceo[visionary]` vs `@coo[executor]` | Strategic bets vs. operational reality |
| Hire Right vs. Hire Fast | `@ta[bar-raiser]` vs `@cro[hunter]` | Standards vs. speed |
| Process vs. Results | `@sales-ops[process]` vs `@vp-sales[pressure]` | CRM hygiene vs. quota attainment |
| Scale Now vs. Optimize | `@vp-ops[scale]` vs `@cfo[steward]` | Infrastructure investment vs. cash preservation |

---

## File Structure

```
fractional-enterprise/
│
├── README.md                         ← This file
├── SKILL.md                          ← Master orchestration layer — load into system prompt
├── CONTRIBUTING.md                   ← How to add agents, personas, and workflows
├── company-context.md                ← Fill this in before first use
│
├── csuite/                           ← 7 C-Suite agent profiles
│   ├── ceo.md
│   ├── cfo.md
│   ├── cmo.md
│   ├── cro.md
│   ├── cto.md
│   ├── coo.md
│   └── chro.md
│
├── management/                       ← 31 management agent profiles
│   ├── finance/
│   │   └── finance-team.md           (VP Finance · Controller · FP&A Lead)
│   ├── marketing/
│   │   └── marketing-team.md         (VP Marketing · Demand Gen · Content & Brand · PMM)
│   ├── revenue/
│   │   └── revenue-team.md           (VP Sales · Sales Ops · CS · Partnerships)
│   ├── technology/
│   │   └── technology-team.md        (VP Eng · Eng Manager · Architect · VP Product)
│   └── operations/
│       └── ops-people-teams.md       (VP Ops · Program Mgr · Biz Ops · VP People · TA · People Ops)
│
└── workflows/
    ├── strategic/
    │   └── swot-qbr.md               (SWOT Analysis · QBR)
    └── workflow-library.md           (All 20 workflows)
```

---

## Design Principles

**Company context is everything.** Generic advice is cheap. Every agent response should feel like it was written for your specific company at your specific stage with your specific constraints. Fill in `company-context.md` first.

**Conflict is the product.** The most valuable output is not consensus — it's the articulation of genuine functional tension. The CFO and CRO *should* disagree about sales headcount. Surface it, don't smooth it.

**CEO synthesizes; you decide.** The CEO agent produces the integrated recommendation. The user makes the final call. The system advises; it does not decide.

**Personas are lenses, not characters.** A `@cfo[steward]` is a rigorous, data-driven CFO applying a capital preservation lens — not a timid or fearful one. The persona adjusts the filter, not the competence.

**Bad news surfaces fast.** Red flags get named. Blind spots get acknowledged. A system that only tells you what you want to hear is a liability, not an advisor.

**Workflows are phased, not simultaneous.** Orchestrated workflows build sequentially — each phase produces a defined deliverable before the next begins. This mirrors how real executive processes work.

---

## Contributing

See `CONTRIBUTING.md` for how to add new agents, personas, workflows, and crisis modes.

---

*Built for operators who need executive-level thinking without the executive-level headcount.*
