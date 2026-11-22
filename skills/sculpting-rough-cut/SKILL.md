---
name: sculpting-rough-cut
description: Stage 2 of Sculpting Framework (Rough Cut — Solution Space, Scope & Alignment). Use after Block is approved to compare realistic options (Anti-Strawman), split Hard No-Go vs. Deferred, run Pre-Detail Spikes (Template 5), clear Vendor/DPA gates, align business rules (Template 3), lock Sign-off (Template 2), or run the 25-min Conflict Resolution Meeting Fallback.
---

# Stage 2: `ROUGH CUT` (Solution Space, Scope & Alignment)

**Goal:** Narrow the solution space, cut excess scope ruthlessly, close external/technical unknowns with evidence, and secure unconditional stakeholder sign-off before detailed engineering planning.

## Input
- Approved `Block Brief` & discovery answers
- Existing service/architecture constraints from the Context Layer

## Steps
1. **Compare realistic options (Anti-Strawman):** Present only viable options (2 is completely fine; never invent an obviously dead option to fill a table) with crisp trade-offs.
2. **Split Out-of-Scope:** Explicitly separate:
   - **Hard No-Go:** Will not build.
   - **Deferred:** Out of v1, but schema/contracts intentionally keep the door open for v2.
3. **Respect Hard Vetoes (Red Lines):** Never pitch variations that violate a Context Layer Red Line (GDPR, SOC2, security). If an exception is genuinely needed, route directly to the escalation owner.
4. **Vendor / Sub-processor Gate:** If introducing a new 3rd-party service or vendor, assign both **cost owner** and **Legal/Security (DPA / sub-processor) owner** here.
5. **Pre-Detail Spike (Template 5):** Never defer external approvals or 3rd-party technical unknowns to "Slice 0" in Detail. Time-box a 1–2 day spike here and record findings using **Template 5**:
   - **Validated:** *(proven assumptions)*
   - **Eliminated:** *(rejected approaches)*
   - **New Edge Cases & Constraints:** *(must carry into Detail contracts)*
   - **Contract / Cost Impact:** *(schema, API, or budget implications)*
6. **Business Rule & State Machine Micro-Contract (Template 3):** For flows with payments, permissions, or state transitions, align edge cases jointly across Product and Engineering:
   `| State / Event | Trigger (Manual / Automatic) | System Behavior | User / Access Impact | Alert / Manual Action |`
7. **Decision & Sign-off Log (Template 2):**
   `| Decision Maker | Status (Approved / Conditional / Veto / Re-confirm) | Caveat / Condition | Closure Rule & Owner |`
   - **Re-ping & Reset Rule:** If closing a caveat does not alter another stakeholder's scope/UX/security, re-ping only the caveat owner. If a pivot, 5+ day pause, or owner change occurs, append a Change Delta to the `Living State Card` and reset affected approvals/FTE to `Re-confirm`.
8. **Optional Fallback — 25-Min Conflict Resolution Meeting:** Trigger **only** after 2 deadlocked async rounds or an expired Assumption Deadline.
   - **Input:** Single deadlocked decision + 2 realistic options + decision makers.
   - **Output:** Updated **Template 2** + **Living State Card**.
   - **Timeout / Tie-Breaker:** If unresolved at 25 min, the escalation owner from the Context Layer makes a single binding call *(or the red line/veto holds and scope is cut)*.

## Gate → `sculpting-detail` (Strict Lock)
Do not advance until:
- [ ] Single direction, Hard No-Go, and Deferred lists are locked.
- [ ] **Conditional Approval Lock:** Zero open caveats, vetoes, or `Re-confirm` entries in Template 2.
- [ ] New vendor/3rd-party cost + DPA/sub-processor sign-off cleared (if applicable).
- [ ] Pre-Detail Spike completed and logged via **Template 5**.
- [ ] `Living State Card` updated at the top of the SSoT doc (share link/delta only in chat).
