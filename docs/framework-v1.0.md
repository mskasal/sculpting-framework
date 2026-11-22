# Sculpting — Product Engineer Framework (v1.0)

> **Purpose:** A tool-agnostic, end-to-end operating framework for Product Engineers to take an ambiguous problem or feature request, progressively increase resolution, align with the right stakeholders, plan parallel execution, and hand off clean vertical slices to implementation.

---

## Core Rules (Anti-Slop & Anti-Over-Engineering)
- **Zero meta-jargon in team messages:** Never leak framework jargon ("Triage: partially ambiguous", "Block gate passed") into Slack/email/ticket messages. Stakeholders only see questions, realistic options, and decisions.
- **Anti-Strawman:** Never invent obviously eliminated fake options just to fill a comparison table. Compare only realistic options (2 is fine).
- **Tool-agnostic core:** No vendor lock-in. Tools (Notion, Linear, Jira, Slack, GitHub, CLI, or plain manual handoff) plug in via the Context Layer.
- **Meetings are last resort:** Default to async. Trigger a 25-minute Conflict Resolution Meeting only after 2 deadlocked async rounds or an expired assumption deadline.
- **Single Source of Truth (SSoT):** Threads are for discussion; a decision is only active once written to the **Living State Card** *(for Fast-Track tasks, the Ticket itself is the SSoT)*.
- **Hard Vetoes (Red Lines) are non-negotiable:** Red lines defined in the Context Layer (GDPR, SOC2, security, zero-downtime constraints) are never negotiated via variations; exceptions require explicit escalation to the escalation owner.

---

## 1. Context Layer (Static / Quarterly)
Populated once during onboarding and lightly refreshed quarterly:
- **Product & Architecture Summary:** Core product, main services/apps, repositories, and **known domain constraints** *(e.g., data model boundaries, current RBAC roles, critical tech debt)*.
- **Team, Escalation & Capacity Map:** Ownership, decision makers (veto power), **escalation / tie-breaker owner**, and baseline quarterly capacity *(per-project FTE changes live on the Living State Card)*.
- **Tool Adapters:** Documentation hub, issue tracker, communication channels, code repos, and existing coding/review skills (MCP, webhook/CLI, or manual fallback).
- **Red Lines:** Non-negotiable constraints (SLA, security, privacy/GDPR, compliance, design system).

---

## 2. Automatic Triage & Fast-Track
Classify every incoming piece of work using 3 internal questions:
1. **Uncertainty:** How clear are the problem and solution? *(Clear / Partially ambiguous / Wide open)*
2. **Blast Radius:** How many teams and services are affected? *(Single service & team / Multi-service or multi-team / Greenfield)*
3. **Nature of Work:** Direct user value or platform/technical bet?

| Work Type | Block | Rough Cut | Detail | Polish |
| :--- | :--- | :--- | :--- | :--- |
| **1. Micro-Feature / Tweak** | **Fast-Track** | **Fast-Track** | Single Ticket | Primary weight |
| **2. Focused Feature** | Medium | Medium | Crisp | Standard |
| **3. Cross-Cutting Feature** | Deep | Heaviest | Detailed | Coordinated |
| **4. 0-to-1** | Heaviest | Aggressive cut | Flexible | Cyclical |
| **5. Technical / Platform Bet** | Business case | Risk & migration | Sequenced | Verification-heavy |

### Fast-Track Rule (Micro-Feature / Tweak)
- **Eligibility:** ≤2 days, single service, single owner, no new vendor, no schema/architectural break.
- **Skipped:** `Living State Card`, separate `Block Brief` / `RFC`, **Template 2**, **Template 3**, **Template 5**, and the `Detail` Capacity–Parallelism Check.
- **Flow:** One async message combining **Template 1** (max 3 questions) + 1-line **No-Go** → thread approval → single **Template 4** ticket (SSoT) → straight to `POLISH`.
- **Escalation Valve:** If discovery reveals cross-service dependencies, new vendor/GDPR impact, or >1 decision maker in conflict, exit Fast-Track immediately and upgrade to **Focused Feature**.

---

## 3. Minimal Recovery Protocol (Delay, Reversal, Pause & Handoff)

1. **Living State Card (Pinned at the top of the SSoT doc, max 10–15 lines, 1–2 short sentences per field):**
   - **Active Direction & No-Go**
   - **Superseded Decisions** *(old direction + 1-line reason)*
   - **Provisional Assumptions** *(assumption + expiry date + owner)*
   - **Active Owners, Capacity (FTE) & Sign-off Status**
   - **Next Single Blocker / First Action**
   - *Rule:* Update the card **only** at the top of the SSoT document — never copy-paste the full card into every chat reply; share only a link or a 1-line delta. Both post-pause catch-up and owner handoffs read exclusively from this card.
2. **Assumption + Expiry Rule (Delayed Stakeholders):**
   - If a decision maker cannot respond in time, do not freeze the project: log one **provisional assumption + expiry date** on the card. Proceed only on **reversible (no-regret)** work; lock irreversible investments (new infra, vendors, schema migrations). State upfront what happens at expiry (*assumption locks* or *25-min fallback meeting triggers*).
3. **Delta & Sign-off Reset Rule:**
   - On **(i) scope/direction pivot**, **(ii) 5+ business days pause**, or **(iii) technical owner change**, never rewrite the RFC from scratch: append a concise **Change Delta** (what changed + timeline/capacity impact) to the card. Any affected stakeholder's or incoming owner's prior sign-off and FTE commitment automatically reset to `Re-confirm` *(approvals do not transfer across owners)*.

---

## 4. Stage Contracts *(All non-Fast-Track work)*

### Stage 1: `BLOCK` (Problem & Value)
- **Input:** Raw request, idea, link, or stakeholder message + Context Layer.
- **Actions:** Run internal Triage; frame the problem **without solution words** + cost of inaction; send **Template 1** per stakeholder for missing critical unknowns; define measurable success criteria; initialize the **Living State Card**.
- **Output:** `Living State Card` + 1-paragraph `Block Brief`.
- **Gate → `Rough Cut`:** Problem stated in one solution-free sentence; "worth doing" is a clear yes; decision makers identified and critical questions answered *(or logged via Assumption + Expiry)*.

### Stage 2: `ROUGH CUT` (Solution Space, Scope & Alignment)
- **Input:** Approved `Block Brief`, discovery answers, service constraints.
- **Actions:** Compare realistic options (**Anti-Strawman**); split out-of-scope into **Hard No-Go** vs. **Deferred** *(not in v1, but schema/contracts keep the door open)*; close external/3rd-party unknowns via a time-boxed **Pre-Detail Spike** (**Template 5**); if introducing a new vendor/3rd-party, assign cost + Legal/Security sub-processor owner; align business rules/edge cases via **Template 3**; track sign-off via **Template 2**.
- **Output:** Updated `Living State Card` + `Rough Cut Pitch / RFC` (including Templates 2, 3, 5 as applicable).
- **Gate → `Detail` (Strict Lock):** Single direction + No-Go/Deferred locked; **Conditional Approval Lock** (zero open caveats, vetoes, or `Re-confirm` items in Template 2); new vendor cost + DPA/sub-processor sign-off cleared; Pre-Detail Spike completed and logged via Template 5.

### Stage 3: `DETAIL` (Technical Plan, Team & Work Breakdown)
- **Input:** Unconditional sign-off on RFC, Template 5 (Spike Summary), codebase, `Living State Card`.
- **Actions:** Produce evidence-based data/API contracts, rollout controls, and rollback plan (carrying every spike edge case into the contract); break work into testable vertical slices (**Template 4**); run **Capacity–Parallelism Check** *(the same owner cannot be assigned to two parallel tracks; collect a 1-line capacity/timeline confirmation from each technical owner)*.
- **Output:** Updated `Living State Card` + `Detail Plan` (Template 4 slices + owner confirmations).
- **Gate → `Polish`:** Every slice is independently testable with clear ACs; contracts locked; conflict-free parallelism verified; owner capacity confirmations received.

### Stage 4: `POLISH` (Implementation, Rollout & Closure)
- **Input:** Approved `Detail Plan`, `Block Brief` success criteria, `Rough Cut` No-Go list.
- **Actions:** Hand off vertical slices to existing coding, TDD, and code review skills (brake scope creep using the No-Go list); verify progressive rollout, rollback readiness, and telemetry; draft stakeholder release summary; verify post-launch impact against the original success criteria and feed learnings into the next `Block` cycle.
- **Output:** `Release Summary` (verification log, release comms draft, impact closure note).
- **Done Gate:** All ACs/tests/reviews passed; live telemetry flowing; stakeholders notified; post-launch impact check scheduled/logged.

---

## 5. Standard Micro-Templates

### Template 1: Async Discovery Ping (`Block`)
- 1 sentence of context (why I'm reaching out)
- Max 3 numbered questions — each stating **which decision the answer changes**
- Expected response window

### Template 2: Decision & Sign-off Log (`Rough Cut → Detail`)
- **Re-ping & Reset Rule:** If a resolved caveat does not change another stakeholder's scope/UX/security, re-ping only the caveat owner. On scope pivot, 5+ business days pause, or owner handoff, reset affected sign-offs/FTE to `Re-confirm`.

| Decision Maker | Status (`Approved` / `Conditional` / `Veto` / `Re-confirm`) | Caveat / Condition | Closure Rule & Owner |
| :--- | :--- | :--- | :--- |

### Template 3: Business Rule & State Machine Micro-Contract (`End of Rough Cut`)

| State / Event | Trigger (`Manual` / `Automatic`) | System Behavior | User / Access Impact | Alert / Manual Action |
| :--- | :--- | :--- | :--- | :--- |

### Template 4: Vertical Slice / Ticket (`End of Detail`)
- **Slice:** *(end-to-end working increment)*
- **Owner & Dependency:** *(single-owner rule: never assign the same owner to two parallel tracks)*
- **Flag / Rollout Control & Rollback:** *(how it rolls out and how it reverts)*
- **Testable Acceptance Criteria (AC):** *(objective pass/fail checks)*

### Template 5: Spike Summary (`Inside Rough Cut`)
- **Validated:** *(proven technical/external assumptions)*
- **Eliminated:** *(rejected approaches)*
- **New Edge Cases & Constraints:** *(must be carried into Detail contracts)*
- **Contract / Cost Impact:** *(schema, API, or vendor/budget implications)*

### Optional Fallback: Conflict Resolution Meeting (Max 25 min)
- **When:** Only after 2 deadlocked async rounds or an expired Assumption Deadline.
- **Input:** Single deadlocked decision + 2 realistic options + decision makers.
- **Output:** Updated **Template 2** + **Living State Card**.
- **Timeout / Tie-Breaker:** If unresolved at 25 min, the escalation owner from the Context Layer makes a single binding call *(or the red line / hard veto holds and scope is cut accordingly)*.
