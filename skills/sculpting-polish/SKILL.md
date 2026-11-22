---
name: sculpting-polish
description: Stage 4 of Sculpting Framework (Polish — Implementation Handoff, Rollout & Impact Closure). Use after Detail (or Fast-Track) is locked to delegate coding/testing/review, enforce the No-Go scope brake, verify rollout and telemetry, draft release comms, and close the loop against original Block success criteria.
---

# Stage 4: `POLISH` (Implementation, Rollout & Closure)

**Goal:** Delegate code execution cleanly to engineering skills, protect scope during implementation, ship safely with observability, communicate clearly, and verify whether the original problem was actually solved.

## Input
- Approved `Detail Plan` (Template 4 slices) — or single **Fast-Track Ticket**
- Original success criteria (`Block Brief`) and `Hard No-Go` list (`Rough Cut`)

## Steps
1. **Execution Handoff:** Hand each vertical slice to existing coding, TDD, and code-review workflows/skills. Do not reinvent engineering mechanics here.
2. **Scope-Creep Brake:** If new requests surface mid-implementation, check against the `Hard No-Go` / `Deferred` list. Park out-of-scope items for the next cycle; if a genuine pivot is unavoidable, trigger the `Delta & Sign-off Reset` rule on the `Living State Card`.
3. **Rollout & Observability Check:**
   - Verify feature flag / progressive rollout control and rollback path.
   - Verify that live telemetry/metrics needed to measure the original `Block` success criteria are firing.
4. **Release Communication Draft:** Draft a concise, jargon-free update for stakeholders and affected teams:
   - What shipped
   - What changed for users/teams
   - Any action required (or "none")
5. **Impact Closure:** Schedule or run the post-launch check against the `Block Brief` success criteria. Feed verified gaps or v2 learnings into the next `Block` cycle (especially for `0-to-1` work).

## Output
- `Release Summary`: AC verification log, stakeholder release draft, and post-launch impact note.

## Done Gate
- [ ] All slice ACs, tests, and code reviews passed.
- [ ] Live telemetry/signals for success criteria are flowing.
- [ ] Stakeholders and affected teams notified.
- [ ] Post-launch impact check logged/scheduled.
