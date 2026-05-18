[SKILL.md](https://github.com/user-attachments/files/27959772/SKILL.md)
---
name: security-gut-check
version: 1.0.0
description: >
  Security Gut Check — activate whenever a user wants a defensive security review of any
  workflow, system, automation, or architecture where software, customer data, accounts, or
  automated actions are involved. Trigger when the user says "security review this", "gut check
  this workflow", "find the trust assumptions", "what could go wrong here", "review this for
  security risks", "is this safe to deploy", "check this automation", or pastes a description
  of any system, workflow, integration, or process and asks for a risk assessment. Also trigger
  proactively when a user describes a new system or automation and security hasn't been
  discussed. The goal is to find places where trust is assumed rather than verified. Defensive
  only — never produces exploit steps, attack code, or offensive security content.
---

# Security Gut Check

Runs a **defensive trust audit** on any workflow, system, or automation. The goal is simple: find the places where the system assumes trust it hasn't earned.

Most security failures aren't exotic. They're places where something assumed a user was legitimate, a package was safe, an API key was private, or a side effect was reversible. This skill surfaces those assumptions systematically before they become incidents.

**Defensive only.** This skill explains what could go wrong and how to fix it. It never produces exploit steps, attack code, or instructions that could be used offensively.

---

## Workflow Overview

1. **Intake** — Understand the system being reviewed and its context
2. **Trust surface mapping** — Identify where the system extends trust
3. **Seven-domain audit** — Systematic review across all risk categories
4. **Risk synthesis** — Prioritize findings by likelihood and impact
5. **Render** — Produce a structured, actionable security review

---

## Step 1: Intake

Extract the following before reviewing. Most should come from the user's description; only ask for what's genuinely missing.

### Required
- **System / workflow description** — What is being reviewed? (paste or describe the workflow, architecture, automation, or process)

### Useful Context
- **Environment** — Production / staging / internal tool / customer-facing
- **Data sensitivity** — What kinds of data does this system touch? (PII, credentials, financial, health, etc.)
- **Scale** — Rough user count, data volume, automation frequency
- **Existing security controls** — What's already in place? (auth providers, secret managers, WAFs, etc.)
- **Who built / maintains this** — Solo developer, small team, enterprise engineering?

If the description is thin, proceed with what's given and note gaps explicitly. A partial review that flags unknowns is more useful than a review that assumes away the gaps.

---

## Step 2: Trust Surface Mapping

Before diving into the seven domains, do a rapid mental map of every place in this system where trust is extended:

**Ask for each component:**
> *"What does this part of the system assume is true — about the user, the input, the dependency, or the environment — without verifying it?"*

Common trust assumptions to look for:
- "This user has the access they claim to have"
- "This input has already been validated upstream"
- "This package / integration does what it says"
- "This API key is only used by authorized callers"
- "This automated action will only affect the intended target"
- "This data will stay within our perimeter"
- "If something goes wrong, we'll know about it"

Note the trust assumptions you've identified before starting the domain audit. They become the organizing thread for findings.

---

## Step 3: Seven-Domain Audit

Review the system across all seven domains. For every risk identified, produce a structured finding (see output format below). Skip domains with no surface area and note why.

---

### Domain 1: User Accounts and Permissions

*Where does the system trust who someone is or what they're allowed to do?*

**What to look for:**
- Permissions granted beyond what the role actually requires (over-permissioning)
- Shared accounts or credentials (no individual accountability)
- Implicit admin or elevated access (granted once, never reviewed)
- Authentication that can be bypassed or replayed
- Partial-access users who can reach sensitive operations through side paths
- Privilege escalation paths — ways a lower-trust user can gain higher-trust access
- Session management — how long do sessions last? Can they be revoked?
- Password / credential reset flows — can they be exploited to take over accounts?

**Why normal checks miss this:** Permission audits are typically point-in-time. Permissions accumulate over time as people change roles, leave projects, or receive temporary access that never gets revoked.

---

### Domain 2: Third-Party Packages and Integrations

*Where does the system execute code or data it didn't write?*

**What to look for:**
- Package dependencies — are they pinned to specific versions or floating to "latest"?
- Transitive dependencies — what do your dependencies depend on?
- Supply chain risk — are any packages from small or single-maintainer projects?
- Integrations with external services — what access do they have once connected?
- Webhooks from external services — is the source validated before acting on the payload?
- Auto-update mechanisms — could an update introduce a malicious change?
- Open source components — when were they last updated? Are there known CVEs?

**Why normal checks miss this:** Developers review direct dependencies but rarely audit the full dependency tree. A compromise two levels down can be just as dangerous.

---

### Domain 3: API Keys, Tokens, and Credentials

*Where does the system hold secrets — and how well are they protected?*

**What to look for:**
- Credentials stored in code, config files, or environment variables that could be logged or exposed
- API keys with broader scope than the task requires (e.g., read/write key used for read-only operation)
- Keys or tokens that never expire and have never been rotated
- Secrets passed through URLs, query strings, or headers that get logged
- Service accounts with production access that developers can also access
- CI/CD pipelines that have access to production credentials
- Third-party services that have been granted persistent access (check OAuth grants, connected apps)
- Keys shared across environments (dev / staging / prod using the same credentials)

**Why normal checks miss this:** Credential audits tend to check if secrets are stored; they rarely audit *scope*, *rotation history*, or *who else has access* to the same secret.

---

### Domain 4: Automated Actions That Could Cause Damage

*Where does the system take actions without a human in the loop — and what's the blast radius?*

**What to look for:**
- Automated deletions, modifications, or publications triggered by external input
- Bulk operations that affect many records based on a single trigger
- Actions that are difficult or impossible to reverse (deletes, sends, payments, deployments)
- Automation that runs with elevated permissions because "it needs them sometimes"
- Cascading automations — where one automation triggers another, creating amplified effects
- Error states that trigger actions (e.g., "if X fails, try Y which has broader access")
- Race conditions — what happens if the same automation runs twice simultaneously?
- No dry-run mode — can you test what an automation would do without actually doing it?

**Why normal checks miss this:** Automation is reviewed at build time. The risk accumulates when the data it acts on changes, when edge cases appear, or when the automation is repurposed beyond its original scope.

---

### Domain 5: Data That Should Stay Private

*Where does sensitive data travel, rest, or get exposed unintentionally?*

**What to look for:**
- PII, credentials, or sensitive data in logs (this is extremely common and easy to miss)
- Data retained longer than necessary (backups, logs, analytics events)
- Overly broad data access — does this service need access to all customer records or just the ones it serves?
- Data passed through client-side code or URLs where it could be captured
- Exports or reports that include more data than the recipient should see
- Third-party analytics or error tracking tools that may capture sensitive fields
- Test data that uses real customer records
- Shared data stores where multiple services read from the same location (blast radius of a breach)

**Why normal checks miss this:** Data privacy reviews focus on collection and storage. Leakage through logs, analytics, and error reporting is often missed because it's not a deliberate data flow.

---

### Domain 6: Approval Steps Before Anything Public or Irreversible

*Where is the system missing a gate before a high-stakes action?*

**What to look for:**
- Irreversible actions (publish, delete, send, deploy, charge) without a confirmation step
- Changes to high-blast-radius settings (email templates, pricing, access controls) without review
- Deployments to production without staging validation
- Content or communications that go to users or public channels without a human review step
- Actions triggered by external events (webhooks, scheduled jobs, user submissions) without validation
- Role changes or permission grants that take effect immediately without approval
- "Undo" capabilities — when they exist, how long is the window? Is there actually a way to reverse?

**Why normal checks miss this:** Approval workflows are designed for the expected flow. The gaps appear in automated paths, edge cases, and developer/admin shortcuts that were added "temporarily."

---

### Domain 7: Monitoring and Logs to Check Regularly

*Where would you see evidence of a problem — and are those signals actually being watched?*

**What to look for:**
- Authentication logs — failed logins, unusual times, unfamiliar locations
- Permission changes — who granted what access, when
- API usage anomalies — unusual call volumes, calls from unexpected IPs, calls to sensitive endpoints
- Automated job logs — did the job run? Did it succeed? How many records did it affect?
- Data export or access logs — who accessed sensitive data, when, and how much
- Dependency or package update logs — what changed, when
- Error rates and error content — errors sometimes reveal system internals
- Absence of expected signals — if a security log suddenly goes quiet, that itself is a signal

**For each log source identified:**
- Is it being collected?
- Is anyone actually reviewing it, or does it only get checked after an incident?
- Is there an alert if the log stops updating?
- How long are logs retained? Is that enough for incident investigation?

**Why normal checks miss this:** Monitoring is treated as an infrastructure concern. The gap between "logs exist" and "someone will notice a problem" is almost always larger than assumed.

---

## Step 4: Risk Synthesis

After completing all seven domains, produce a prioritized findings summary.

### Priority Classification

| Priority | Criteria |
|---|---|
| 🔴 **Critical** | Could result in data breach, account takeover, or irreversible damage; relatively easy to trigger |
| 🟠 **High** | Significant risk; requires some effort or knowledge to exploit but not unlikely |
| 🟡 **Medium** | Real risk but requires specific conditions or is lower-impact |
| 🟢 **Low / Hardening** | Good practice; reduces attack surface even if active risk is low |

### Cross-Domain Patterns
After individual findings, look for patterns that cut across domains — combinations of risks that compound each other:
- e.g., An overly permissioned API key (Domain 3) + an automated action with broad scope (Domain 4) + no monitoring (Domain 7) is a much bigger problem than any one of those alone
- Note these combinations explicitly; they often represent the actual high-risk scenarios

---

## Step 5: Output Format

Produce the security review as a clean, structured document. Use the format below.

---

### Security Gut Check — [System Name or Description]
*Reviewed: [date] | Scope: [what was reviewed]*

---

#### Trust Surface Summary
*2–3 sentences identifying the most significant places where this system extends trust.*

---

#### Findings

For each finding:

**[PRIORITY] Finding: [Short name]**
**Domain:** [Which of the 7 domains]

- **What could go wrong:** [Specific, concrete description of the failure mode — not generic]
- **Why a normal check might miss it:** [The specific blind spot that makes this easy to overlook]
- **Safest practical fix:** [Actionable recommendation — specific enough to act on]
- **Needs expert review:** Yes / No / Maybe — [brief rationale]

---

#### Priority Summary

| Finding | Priority | Effort to Fix | Needs Expert |
|---|---|---|---|
| [Short name] | 🔴 / 🟠 / 🟡 / 🟢 | Low / Medium / High | Yes / No |

---

#### Cross-Domain Risk Combinations
*Where multiple findings interact to create compounding risk.*

[2–3 sentences per combination, if applicable]

---

#### Monitoring Checklist
*The specific logs and signals to review regularly for this system.*

- [ ] [Log or signal] — Check [frequency] for [what to look for]
- [ ] [Log or signal] — Alert if [condition]

---

#### What to Do First
*If you only do three things based on this review:*

1. [Highest-priority, actionable first step]
2. [Second step]
3. [Third step]

---

## Quality Checklist

Before delivering the review:
- [ ] Every finding includes all four fields: what could go wrong, why it's missed, the fix, and expert review flag
- [ ] Fixes are specific and actionable — not "improve your security" or "add authentication"
- [ ] No exploit steps, attack code, or offensive content of any kind
- [ ] Cross-domain combinations identified where they exist
- [ ] Monitoring checklist is specific to this system, not generic
- [ ] "What to Do First" is genuinely prioritized — not just the first three findings
- [ ] Domains with no surface area are noted as N/A with brief rationale

---

## Edge Cases

**Description is very thin (e.g., "my web app"):**
Produce a generic trust surface map for that system type and flag every assumption explicitly. A partial review with visible gaps is more honest and more useful than a false-confidence review.

**User provides a very complex system (microservices, multi-cloud, large team):**
Focus on the trust boundaries between components rather than internals of each. The highest-risk points in complex systems are usually at seams — where one service hands off to another.

**User asks for offensive help ("how would someone exploit this?"):**
Redirect clearly: "This skill is defensive only — I can tell you what's at risk and how to fix it, but I don't produce exploit steps. Here's the defensive finding for this risk area: [proceed with finding]."

**System involves regulated data (HIPAA, PCI, GDPR, SOC 2):**
Flag the regulatory surface in the Trust Surface Summary and note which findings may have compliance implications. Recommend expert review for those findings. Do not attempt to provide authoritative compliance guidance.

**User is a developer reviewing their own work:**
This is the ideal use case. Acknowledge that self-review has limits (we're blind to our own assumptions) and encourage sharing the review with a peer who didn't build the system.

**Finding requires specialized knowledge to fix (e.g., cryptography, zero-trust network architecture):**
Mark "Needs expert review: Yes" and explain specifically what kind of expert (security engineer, pentest firm, compliance auditor) and why. Don't provide half-correct guidance on complex security topics.
