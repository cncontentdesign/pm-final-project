# A/B Experiment Brief, RouteLogic (B2B)

## Parameters
| Parameter | Decision |
|---|---|
| Feature under test | Driver Alert Notifications - Push alerts on route changes/compliance flags |
| Persona | A mid-size 3PL Coordinator responsible for keeping a live fleet routed correctly and knowing, in real time, where every stop stands. |
| Expected outcome | the management of live coordination on the platform  and cut daily wasted time in half. |
| Primary success metric | Reassignment→acknowledgement time drops from 8–15 min to < 60s |
| Baseline rate | 8 - 15 mins |
| Guardrail metric | Coordinator core-feature adoption (Board 91%, Optimizer 85%) |
| Guardrail boundary | must not drop |
| Second guardrail | Manager Reporting CSAT (4.5) - must not drop. |
| Minimum Detectable Effect | 15% |
| Sample size per arm | 165 |
| Traffic split | · |
| Test duration | 90 days |
| Significance threshold | p<0.05 |

## Control vs. Variant
- **Control (A):** The board lies to coordinators. A reassignment takes 8–15 minutes to reach the driver with no push notification (BUG-2044), and completed stops still read "in progress" for up to an hour, leading to about 69% post-assignment workflow abandonment
- **Variant (B):** As a 3PL Coordinator, I want every reassignment I commit to alert only the affected driver instantly, so that I stop re-sending changes over WhatsApp to confirm they landed. AC: Committing a reassignment fires an alert to that driver alone (never the fleet); board status = Sent within 2s. As a driver, I want an alert that says exactly what changed and by when, so that I act without calling the office back. AC: Card shows changed stop, new stop/ETA window, timestamp; single Got it records ack. As a 3PL Coordinator, I want to see acknowledgement land on the board, so that I know the driver has the correct route without leaving the screen. AC: Status advances Sent → Delivered → Acknowledged with time-to-ack; no WhatsApp/phone step needed. Screens to Build (exactly 3)

Entry point — Coordinator Board / Reassign. Route list per driver, stop rows with status chips, Reassign driver control, driver picker, Confirm change modal. Feature core — Driver Alert (phone view). Simulated Android push banner; alert card with change summary (added/removed/reordered stop), new stop + ETA window, timestamp; large Got it button. Success/confirmation — Ack Tracker (back on board). Status timeline chip (Sent→Delivered→Acknowledged), time-to-ack readout, green "Confirmed — no follow-up needed" state, toast ("Driver acknowledged in 42s"). Functional Requirements (from MUST HAVE)

FR1 — On commit, generate a driver alert and set status Sent within 2s. FR2 — Alert is targeted to affected driver(s) only; fleet broadcast prohibited. FR3 — Payload shows what changed, new stop/ETA window, timestamp — enough to act with zero callbacks. FR4 — Driver acks via a single Got it; ack recorded with timestamp. FR5 — Board shows exactly one of Sent / Delivered / Acknowledged, updated on view. FR6 — Median commit→Acknowledged < 60s (replaces the 8–15 min lag). FR7 — Android-scoped only (no iOS drivers in discovery); no iOS path built. FR8 — Confirming receipt never requires leaving the board or an external channel. Smart Behaviors (Situation → Outcome)

If (Situation) Then (Outcome) Coordinator commits a reassignment Targeted alert to affected driver only; status = Sent Driver opens the alert Status = Delivered; timestamp recorded Driver taps Got it Status = Acknowledged; time-to-ack recorded; chip turns green Newer change hits same driver before ack Latest supersedes; only most recent alert shown (dedup) Driver acks a change a newer one replaced Show "Acknowledged — superseded", not clean green No ack yet (Sent/Delivered) Board shows amber "unacknowledged" — never a false green Technical Constraints ("what not to build") — No external APIs / no real FCM (push simulated in state) · No login/auth (Coordinator + driver are toggled panes) · useState only — no backend/DB/websockets · No real-time socket layer (SHOULD, out of scope) — status refreshes on view · Seed 2–3 mock drivers, no persistence.
- **Held constant (isolation check):** All earlier and later steps in the workflow are unchanged, so all the below:

Open RouteLogic
Load Today’s Fleet View
Assign Routes via Optimizer
Log Compliance Checks
Complete Shift Handoff

## Hypothesis
> I believe that Driver Alert Notifications - Push alerts on route changes/compliance flags for A mid-size 3PL Coordinator responsible for keeping a live fleet routed correctly and knowing, in real time, where every stop stands. will result in the management of live coordination on the platform  and cut daily wasted time in half., as measured by a 15% change in Reassignment→acknowledgement time drops from 8–15 min to < 60s within 90 days. We will protect Coordinator core-feature adoption (Board 91%, Optimizer 85%) throughout the test.

## Shipping criteria
> We will **ship** if Reassignment→acknowledgement time drops from 8–15 min to < 60s improves by ≥ 15% at p<0.05 and Coordinator core-feature adoption (Board 91%, Optimizer 85%) does not reach must not drop after 90 days.
> We will **iterate** if direction is positive but lift is below the MDE.
> We will **kill** if the primary metric shows no improvement or moves negatively.
> The read date is fixed at the end of 90 days, no results reviewed before this date.
