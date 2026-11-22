---
name: sculpting
description: End-to-end Product Engineer operating framework (Block → Rough Cut → Detail → Polish). Use when starting a new feature, product initiative, or platform bet, resuming after a pause, handling a stakeholder handoff or mid-flight decision reversal, or triaging work size into Fast-Track vs. full sculpting.
---

# Sculpting — Product Engineer Orchestrator

Sculpting turns ambiguous problems into aligned, scoped, implementation-ready vertical slices through progressive resolution: **Block → Rough Cut → Detail → Polish**.

## Core Rules (Always On)
- **Zero meta-jargon in team messages:** Never mention "Triage", "Block gate", "SSoT", or template names in outgoing stakeholder messages. Stakeholders only see clear questions, realistic options, and decisions.
- **Anti-Strawman:** Never invent fake/eliminated options to fill a table. Compare only realistic choices.
- **Tool-agnostic adapters:** Read/write to whatever tools are configured in the Context Layer (MCP servers like Notion/Linear/Slack/GitHub, webhooks/CLI, or plain manual prompts telling the engineer what to ask/record).
- **Hard Vetoes (Red Lines) are non-negotiable:** Red lines from the Context Layer (GDPR, SOC2, security, zero-downtime) cannot be negotiated via variations; exceptions require explicit escalation to the escalation owner.
- **Meetings are last resort:** Default to async. Escalate to a 25-min Conflict Resolution Meeting only after 2 deadlocked async rounds or an expired assumption deadline.

## Step 0: Context Layer Check (First-Time Onboarding)
Before starting work, check if the workspace has a `sculpting.context.md` (or configured Context Layer doc). If missing, ask the engineer 4 brief questions once and save it:
1. **Product & Architecture:** Main services/repos and known domain constraints (data model limits, current RBAC, critical tech debt).
2. **Team, Veto & Escalation Map:** Key owners (PM, Design, Backend/Infra, Security/Legal), who holds veto power, **escalation / tie-breaker owner**, and baseline quarterly capacity.
3. **Tool Adapters:** Docs hub, issue tracker, chat channel, repos, and coding/review skills (or `manual`).
4. **Red Lines:** Non-negotiable constraints (SLA, GDPR/SOC2, security, zero-downtime).

- **Git & Manual-Mode Policy:** In public/open-source repos, keep `sculpting.context.md` local (add to `.gitignore` or `.git/info/exclude`) unless the team explicitly wants shared context committed. When `manual` mode is used without an external docs hub, store the project's SSoT doc locally (e.g., `docs/sculpt-<slug>.md` or in-thread) rather than inventing ad-hoc files.

## Step 1: Internal Triage (Do Not Send to Stakeholders)
Classify the incoming request using 3 questions:
1. **Uncertainty:** Clear / Partially ambiguous / Wide open?
2. **Blast Radius:** Single service & team / Multi-service or multi-team / Greenfield?
3. **Nature of Work:** User value or technical/platform bet?

| Work Type | Path |
| :--- | :--- |
| **1. Micro-Feature / Tweak** *(≤2 days, 1 service, 1 owner, no new vendor/schema break)* | **Fast-Track** (below) |
| **2. Focused Feature** | `sculpting-block` → `sculpting-rough-cut` → `sculpting-detail` → `sculpting-polish` (light) |
| **3. Cross-Cutting Feature** | Full 4 stages (heaviest on `sculpting-rough-cut` & `sculpting-detail`) |
| **4. 0-to-1** | Full 4 stages (heaviest on `sculpting-block`; cyclical after launch) |
| **5. Technical / Platform Bet** | Full 4 stages (business case in Block; migration/rollback in Rough Cut) |

## Fast-Track Rule (Micro-Feature / Tweak)
- **Skip:** `Living State Card`, separate `Block Brief` / `RFC`, Sign-off table, State Machine table, Spike Summary, and Capacity–Parallelism Check.
- **Execute:** Send one short async message combining **max 3 questions** (stating which decision each answer changes) + **1-line No-Go**. Once approved in-thread, write a single **Vertical Slice Ticket** (Scope + No-Go + Rollback + Testable AC) as the SSoT and jump straight to `sculpting-polish`.
- **Escalation Valve:** If discovery uncovers cross-service dependencies, a new vendor/GDPR issue, or >1 decision maker in conflict, abort Fast-Track and upgrade to **Focused Feature**.

## Minimal Recovery Protocol (Delay, Reversal, Pause & Handoff)
- **Living State Card (SSoT):** Pinned at the top of the project doc (max 10–15 lines: Active Direction & No-Go, Superseded Decisions, Provisional Assumptions with expiry/owner, Active Owners/FTE & Sign-off, Next Single Blocker). **Never copy-paste the full card into every chat reply** — share only a link or a 1-line delta.
- **Delayed Stakeholder (`Assumption + Expiry`):** Log one provisional assumption + expiry date on the card. Proceed only on reversible (*no-regret*) work; lock irreversible investments (infra, vendors, migrations). Define what happens at expiry (*assumption locks* or *25-min fallback*).
- **Pivot, 5+ Day Pause, or Owner Handoff (`Delta & Sign-off Reset`):** Never rewrite the RFC from scratch. Append a short **Change Delta** (what changed + timeline/capacity impact) to the card, mark superseded decisions, and reset affected stakeholders' or incoming owners' approvals and FTE commitments to `Re-confirm` *(approvals never transfer across owners)*.

## Stage Routing
- Problem unclear or just starting → load `sculpting-block`
- Problem clear, need options, scope cuts, spike, or stakeholder sign-off → load `sculpting-rough-cut`
- Unconditional sign-off & spike done, need contracts, slices, and parallel plan → load `sculpting-detail`
- Slices approved, ready to build, roll out, and close the loop → load `sculpting-polish`
