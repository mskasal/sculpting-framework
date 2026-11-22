---
name: sculpting-block
description: Stage 1 of Sculpting Framework (Block — Problem & Value). Use when framing a new feature or initiative before jumping to solutions, initializing the Living State Card, and drafting Template 1 Async Discovery Pings for stakeholders.
---

# Stage 1: `BLOCK` (Problem & Value)

**Goal:** Prevent solving the wrong problem and gather missing critical unknowns with minimal team friction.

## Input
- Raw request, idea, stakeholder message, or doc/ticket link
- Context Layer (do **not** re-ask facts already recorded in the Context Layer)

## Steps
1. **Frame the problem without solution words:** Write a 1-paragraph problem statement describing user/business pain, not a proposed implementation.
2. **State cost of inaction & success criteria:** What happens if we do nothing? What measurable signal proves this worked?
3. **Draft Async Discovery Pings (Template 1):** For each stakeholder who holds a missing critical unknown, write a **separate, short** message:
   - 1 sentence of context (why I'm reaching out)
   - Max 3 numbered questions — each explicitly stating **which decision the answer changes**
   - Expected response window
   *(Never include framework jargon in the message. Never auto-send — present drafts for the engineer to send or approve.)*
4. **Initialize the Living State Card** at the top of the SSoT doc *(in `manual` mode with no external docs tool, use a single local file like `docs/sculpt-<slug>.md` or keep it pinned in-thread)* (max 10–15 lines):
   - **Active Direction & No-Go:** *(in discovery)*
   - **Superseded:** None
   - **Provisional Assumptions:** *(any delayed stakeholder answer logged with expiry + owner)*
   - **Owners, FTE & Sign-off:** *(list decision makers)*
   - **Next Single Blocker:** *(waiting on discovery answers)*

## Output
- `Living State Card` (initialized at top of SSoT doc)
- 1-paragraph `Block Brief` (problem, cost of inaction, measurable success criteria, open questions + owners)
- Per-stakeholder **Template 1** message drafts

## Gate → `sculpting-rough-cut`
Do not advance until:
- [ ] Problem is stated in one sentence with zero solution words.
- [ ] "Worth doing?" is an explicit **yes**.
- [ ] Decision makers are identified and critical unknowns are answered *(or logged via `Assumption + Expiry` on the Living State Card)*.
