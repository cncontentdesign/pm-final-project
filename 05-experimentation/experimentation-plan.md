# Experimentation Plan (Module 5)

## Get your documents ready
- **From M3, your hypothesis sentence:** My hypothesis is that delivering real-time trust in the core of our product, through instant, confirmed, reassignments and accurate stop status that matches what's happening on the ground, will pull live coordination back onto the platform for mid-size 3PL coordinators and cut that daily wasted time in half. I'll look to measure by workflow completion (Open to Shift Handoff) climbing from 31% to at least 65%. I'll protect core-feature adoption (Dispatch Board 91%, Optimizer 85%) and manager Reporting CSAT (4.5) so a leaner frontline doesn't cost us the backend power buyers pay for, and I'll make the go/no-go call after a 90-day pilot on 2 or 3 enterprise accounts - we might well target some of those most at risk of churning.
- **From M3, your primary success metric & guardrail metric:** Primary Success Metric: Dispatch-workflow completion (Open to Shift Handoff) - 31% up to at least 65%

Guardrail: Coordinator core-feature adoption (Board 91%, Optimizer 85%) plus Manager Reporting CSAT (4.5)
- **From M4, the feature you scoped in your PRD this is what you're testing:** Driver Alert Notifications - Push alerts on route changes/compliance flags

## Define your experiment parameters
- **Feature under test pull from your M4 PRD:** Driver Alert Notifications - Push alerts on route changes/compliance flags
- **Persona pull your M2 persona:** A mid-size 3PL dispatcher responsible for keeping a live fleet routed correctly and knowing, in real time, where every stop stands.
- **Expected outcome the behaviour change you expect, from your M3 hypothesis:** Pull live coordination back onto the platform for mid-size 3PL coordinators and cut daily wasted time in half.
- **Primary success metric the one number that defines success, from M3:** Workflow completion 31% to 65%
- **Baseline rate today's rate of your primary metric, from your M3 data:** 31%
- **Guardrail metric & boundary what must not break, and how far it can move before you investigate:** Coordinator core-feature adoption (Board 91%, Optimizer 85%) plus Manager Reporting CSAT (4.5) - must not drop.
- **Minimum Detectable Effect (MDE) the smallest improvement worth shipping, your floor:** 15% improvement - this may need to be a directional pilot,
- **Sample size per arm use the calculator in the builder, baseline + MDE:** 165 - but it may be unlikely we'll be able to get 165 users per arm across a handful of enterprise accounts - would warrant further investigation, but
- **Traffic split & test duration 50/50 standard · cover ≥ 2 weekly cycles:** 50/50 - over 90 days
- **Significance threshold p < 0.05 is standard, explain any deviation:** p<0.05

## Define your control and variant
- **Control (A) the current experience, reference your M2 moment of misery and M3 funnel/workflow data:** The board lies to coordinators. A reassignment takes 8–15 minutes to reach the driver with no push notification (BUG-2044), and completed stops still read "in progress" for up to an hour, leading to about 69% post-assignment workflow abandonment
- **Variant (B) your single change, copy the relevant screens & functional requirements from your M4 PRD:** As a 3PL dispatcher, I want every reassignment I commit to alert only the affected driver instantly, so that I stop re-sending changes over WhatsApp to confirm they landed. AC: Committing a reassignment fires an alert to that driver alone (never the fleet); board status = Sent within 2s. As a driver, I want an alert that says exactly what changed and by when, so that I act without calling the office back. AC: Card shows changed stop, new stop/ETA window, timestamp; single Got it records ack. As a 3PL dispatcher, I want to see acknowledgement land on the board, so that I know the driver has the correct route without leaving the screen. AC: Status advances Sent → Delivered → Acknowledged with time-to-ack; no WhatsApp/phone step needed. Screens to Build (exactly 3)

Entry point — Dispatcher Board / Reassign. Route list per driver, stop rows with status chips, Reassign driver control, driver picker, Confirm change modal. Feature core — Driver Alert (phone view). Simulated Android push banner; alert card with change summary (added/removed/reordered stop), new stop + ETA window, timestamp; large Got it button. Success/confirmation — Ack Tracker (back on board). Status timeline chip (Sent→Delivered→Acknowledged), time-to-ack readout, green "Confirmed — no follow-up needed" state, toast ("Driver acknowledged in 42s"). Functional Requirements (from MUST HAVE)

FR1 — On commit, generate a driver alert and set status Sent within 2s. FR2 — Alert is targeted to affected driver(s) only; fleet broadcast prohibited. FR3 — Payload shows what changed, new stop/ETA window, timestamp — enough to act with zero callbacks. FR4 — Driver acks via a single Got it; ack recorded with timestamp. FR5 — Board shows exactly one of Sent / Delivered / Acknowledged, updated on view. FR6 — Median commit→Acknowledged < 60s (replaces the 8–15 min lag). FR7 — Android-scoped only (no iOS drivers in discovery); no iOS path built. FR8 — Confirming receipt never requires leaving the board or an external channel. Smart Behaviors (Situation → Outcome)

If (Situation) Then (Outcome) Dispatcher commits a reassignment Targeted alert to affected driver only; status = Sent Driver opens the alert Status = Delivered; timestamp recorded Driver taps Got it Status = Acknowledged; time-to-ack recorded; chip turns green Newer change hits same driver before ack Latest supersedes; only most recent alert shown (dedup) Driver acks a change a newer one replaced Show "Acknowledged — superseded", not clean green No ack yet (Sent/Delivered) Board shows amber "unacknowledged" — never a false green Technical Constraints ("what not to build") — No external APIs / no real FCM (push simulated in state) · No login/auth (dispatcher + driver are toggled panes) · useState only — no backend/DB/websockets · No real-time socket layer (SHOULD, out of scope) — status refreshes on view · Seed 2–3 mock drivers, no persistence.
- **Isolation check, what has NOT changed? list everything identical between arms (app version, recommendation engine, notifications, onboarding). If something changed inadvertently, your test is compromised.:** All earlier and later steps in the workflow are unchanged, so all the below:

Open RouteLogic
Load Today’s Fleet View
Assign Routes via Optimizer
Log Compliance Checks
Complete Shift Handoff

## Formalize your hypothesis & shipping criteria
- **Your hypothesis (filled in):** I believe Driver Alert Notifications - Push alerts on route changes/compliance flags for A mid-size 3PL dispatcher responsible for keeping a live fleet routed correctly and knowing, in real time, where every stop stands. will result in the management of live coordination on the platform  and cut daily wasted time in half. , measured by a 15 point change in Dispatch-workflow completion (Open to Shift Handoff)	 within 90 days. We will protect Coordinator core-feature adoption (Board 91%, Optimizer 85%) .
- **Your shipping criteria (filled in):** We will SHIP if Dispatch-workflow completion (Open to Shift Handoff) improves by ≥ 20 at p<0.05 and Coordinator core-feature adoption (Board 91%, Optimizer 85%) does not drop after 90 days. We will ITERATE if direction is positive but lift is below MDE. We will KILL if the primary metric shows no improvement or moves negatively. The read date is fixed at the end of 90 days, no results reviewed before then.
- **Hardest parameter to define, and did it change your hypothesis? quick debrief:** MDE - we are looking for a significant change, but must be willing to accept a smaller one, however as B2B software, looking to pilot over relatively few customers, it may not be realistic for us to expect high numbers of users on each arm - depending on the scale of our enterprise customers, perhaps.
