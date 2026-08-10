# Hypothesis & Success Metrics

> Module 3 · Use Analytics and Metrics for Data-Driven Decisions, Deliverable 3
>
> Scenario B, RouteLogic Velocity

## Finalized product hypothesis

> Coordinators keep a parallel WhatsApp group because they can't trust the board (UXR-02, UXR-09), and the numbers back it up: about 69% stop using our tool right after route assignment, daily time lost to workarounds has tripled to 31 minutes, and Coordinator NPS has fallen 30 points to -12. My hypothesis is that restoring real-time trust in the core dispatch loop, meaning instant confirmed reassignments and stop status that matches what's happening on the ground, will pull live coordination back onto the platform for mid-size 3PL coordinators and cut that daily waste in half, which I'll measure by workflow completion (Open to Shift Handoff) climbing from 31% to at least 65%. I'll protect core-feature adoption (Dispatch Board 91%, Optimizer 85%) and manager Reporting CSAT (4.5) so a leaner frontline doesn't cost us the backend power buyers pay for, and I'll make the go/no-go call after a 90-day pilot on 2 or 3 accounts.

## Success metrics

| Metric | Type | Target | Why it matters |
|---|---|---|---|
| Dispatch-workflow completion (Open to Shift Handoff) | North-star (outcome) | 31% up to at least 65% | Shows coordinators trust the board through the live-coordination stage instead of defecting to WhatsApp. This is the behaviour that drives NPS and retention back up. |
| Daily time lost to manual workarounds (and route-assign time) | Leading indicator | 31 min down to 15 min or less (route-assign 8.2 down to 4.0 min or less) | Moves first, within weeks, so it's early proof the trust gap is closing before NPS and churn catch up. Pilot already shows route-assign up 34%. |
| Coordinator core-feature adoption (Board 91%, Optimizer 85%) plus Manager Reporting CSAT (4.5) | Guardrail | Must not drop | A simpler frontline can't come at the cost of the backend platform power enterprise admins pay for. That power is what keeps the contract signed. |

## Evidence trail

- **Qualitative (M2):** "We keep a WhatsApp group as the real system" (UXR-02); "A stop shows 'in progress' when it was delivered an hour ago, I can't trust the board" (UXR-09). Root causes: reassignment lag 8 to 15 min with no push (BUG-2044), status lag 20 to 60 min (BUG-2072).
- **Quantitative (M3):** About 69% post-assignment workflow abandonment (funnel 71%, 31%, 18%); Assign Routes 8.2 min vs 4.0 benchmark; daily time lost tripled (about 9 to 31 min); Coordinator NPS +18 to -12; complexity cited by 4 of 5 churning accounts (was 1 of 8); Velocity pilot route-assign up 34%.
- **Reconciliation insight:** The misery lives in the high-adoption core loop (Dispatch Board, Optimizer), not the low-adoption bloat features. It's a reliability defect inside a feature people otherwise like, which is why it shows up in behaviour and account health rather than in a single red CSAT cell.

## Decision window

90-day pilot on 2 or 3 enterprise accounts (one retention cohort). Scale if post-assignment drop-off is 35% or less, daily time lost is 15 minutes or less, and there's no slip in core-feature adoption or manager CSAT, with NPS heading back toward zero or positive. Pivot if drop-off stays above 50%. Kill if adoption or manager CSAT go backwards.
