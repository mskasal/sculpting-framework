---
name: sculpting-detail
description: Stage 3 of Sculpting Framework (Detail — Technical Plan, Vertical Slices & Parallel Capacity). Use after Rough Cut has unconditional sign-off and spike evidence to lock data/API contracts, produce Template 4 vertical slices, and verify conflict-free parallelism with 1-line owner capacity confirmations.
---

# Stage 3: `DETAIL` (Technical Plan, Team & Work Breakdown)

**Goal:** Turn an unconditionally approved, spike-validated Rough Cut into codebase-grounded contracts, independently testable vertical slices, and a conflict-free parallel execution plan.

## Input
- Unconditionally approved `Rough Cut Pitch / RFC` (Template 2 all `Approved`, Template 3 approved if applicable)
- **Template 5 (Spike Summary)**
- Actual codebase/repositories + `Living State Card`

## Steps
1. **Evidence-Based Technical Contract:** Inspect the actual codebase and lock:
   - Data model / migrations (additive & backwards-compatible where required)
   - API / event contracts
   - **Carry forward every single edge case and constraint** from Template 5 (Spike Summary) so nothing drops between Rough Cut and implementation.
2. **Vertical Slicing (Template 4):** Break the work into independently testable, deployable end-to-end slices (never horizontal-only layers unless strictly gated). For each slice:
   - **Slice:** *(end-to-end working increment)*
   - **Owner & Dependency:** *(explicit owner + upstream dependency)*
   - **Flag / Rollout Control & Rollback:** *(progressive rollout mechanism + clean revert path)*
   - **Testable Acceptance Criteria (AC):** *(objective pass/fail checks)*
3. **Capacity–Parallelism Check (Mandatory):**
   - **Single-Owner Rule:** Never assign the same owner (e.g., 1.0 FTE) to two parallel tracks at the same time.
   - Identify the single synchronization point(s) (e.g., Day 1 contract lock).
   - **1-Line Capacity Confirmation:** Request a 1-line timeline/FTE confirmation from each technical owner before locking the plan.
4. **Update Living State Card & Issue Tracker:** Update the SSoT card and export Template 4 slices to the team's issue tracker (via MCP adapter or formatted copy-ready list).

## Gate → `sculpting-polish`
Do not advance until:
- [ ] Every slice is independently understandable, testable, and has objective ACs.
- [ ] Every Spike edge case is reflected in the contract/ACs.
- [ ] No owner is double-booked across parallel tracks, and every technical owner gave a 1-line capacity confirmation.
- [ ] Slices can be handed directly to coding/engineering skills without ambiguity.
