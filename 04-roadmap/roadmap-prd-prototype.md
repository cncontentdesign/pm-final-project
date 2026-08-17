# Roadmap, PRD & Prototype

> Module 4 · Build High-Velocity Product Roadmaps — ★ Deliverable 4
>
> _You'll complete this during Module 4._

## High-level product roadmap

04-roadmap/routelogic-velocity-roadmap.html

_____

## PRD snippets

Simplified PRD — B6 Driver Alert Notifications
Title: Driver Alert Notifications — Push on Route Changes · Author: Me · Status: Draft · Target: High-Fidelity Prototype (useState-only, no backend)

1. THE BIG PICTURE
Vision: Every route reassignment reaches the affected driver and comes back confirmed in under a minute — so the 3PL Coordinator trusts the board again and never opens WhatsApp to check.

Press Release

RouteLogic Velocity today closes the gap that turned its dispatch board into a screen people learned to disbelieve. When a Coordinator reassigns a route, the affected driver now gets an instant, actionable alert — what changed, which stop, by when — and taps Got it. The Coordinator watches that acknowledgement land on the board in seconds, not the 8–15 minutes it used to take (BUG-2044).

For the mid-size 3PL Coordinator, this ends the "phone in the other hand" workflow. Today a reassignment fires into a void, so they re-send the same change over WhatsApp and wait for a manual reply to confirm it was seen — running the app and a chat group as two parallel systems all shift (UXR-02: "We keep a WhatsApp group as the real system"). Now the confirmation lives on the board itself, and the workaround that had become the real system of record goes away.

Success Metrics

Primary: Reassignment→acknowledgement time drops from 8–15 min to < 60s (median) — directly cutting daily time lost to manual workarounds / route-assign time.
Guardrail: Coordinator core-feature (Board) adoption holds at ≥ 91% — the alert must not pull Coordinator off the board.
2. THE DETAILS
User Stories

As a 3PL Coordinator, I want every reassignment I commit to alert only the affected driver instantly, so that I stop re-sending changes over WhatsApp to confirm they landed.
AC: Committing a reassignment fires an alert to that driver alone (never the fleet); board status = Sent within 2s.
As a driver, I want an alert that says exactly what changed and by when, so that I act without calling the office back.
AC: Card shows changed stop, new stop/ETA window, timestamp; single Got it records ack.
As a 3PL Coordinator, I want to see acknowledgement land on the board, so that I know the driver has the correct route without leaving the screen.
AC: Status advances Sent → Delivered → Acknowledged with time-to-ack; no WhatsApp/phone step needed.
Screens to Build (exactly 3)

Entry point — Coordinator Board / Reassign. Route list per driver, stop rows with status chips, Reassign driver control, driver picker, Confirm change modal.
Feature core — Driver Alert (phone view). Simulated Android push banner; alert card with change summary (added/removed/reordered stop), new stop + ETA window, timestamp; large Got it button.
Success/confirmation — Ack Tracker (back on board). Status timeline chip (Sent→Delivered→Acknowledged), time-to-ack readout, green "Confirmed — no follow-up needed" state, toast ("Driver acknowledged in 42s").
Functional Requirements (from MUST HAVE)

FR1 — On commit, generate a driver alert and set status Sent within 2s.
FR2 — Alert is targeted to affected driver(s) only; fleet broadcast prohibited.
FR3 — Payload shows what changed, new stop/ETA window, timestamp — enough to act with zero callbacks.
FR4 — Driver acks via a single Got it; ack recorded with timestamp.
FR5 — Board shows exactly one of Sent / Delivered / Acknowledged, updated on view.
FR6 — Median commit→Acknowledged < 60s (replaces the 8–15 min lag).
FR7 — Android-scoped only (no iOS drivers in discovery); no iOS path built.
FR8 — Confirming receipt never requires leaving the board or an external channel.
Smart Behaviors (Situation → Outcome)

If (Situation)	Then (Outcome)
Dispatcher commits a reassignment	Targeted alert to affected driver only; status = Sent
Driver opens the alert	Status = Delivered; timestamp recorded
Driver taps Got it	Status = Acknowledged; time-to-ack recorded; chip turns green
Newer change hits same driver before ack	Latest supersedes; only most recent alert shown (dedup)
Driver acks a change a newer one replaced	Show "Acknowledged — superseded", not clean green
No ack yet (Sent/Delivered)	Board shows amber "unacknowledged" — never a false green
Technical Constraints ("what not to build") — No external APIs / no real FCM (push simulated in state) · No login/auth (dispatcher + driver are toggled panes) · useState only — no backend/DB/websockets · No real-time socket layer (SHOULD, out of scope) — status refreshes on view · Seed 2–3 mock drivers, no persistence.

3. THE LOGISTICS
Features Out (WON'T HAVE — NOW): Compliance-flag alerts (don't touch BUG-2044; double the trigger surface) · Two-way chat/reply · Driver-initiated change requests · Email/SMS channels · iOS/second platform · Manager/exec dashboards (B8, cut).

Edge Cases (+ safety guard)

Driver offline / not delivered → stays Delivered-pending (amber) + in-app fallback banner on next open; board stays honest.
Rapid duplicate changes → newest supersedes; earlier alerts collapse (no spam).
Stale-route ack → void the acked version, surface "superseded."
Safety / hallucination guard → render only fields present in the committed reassignment record; never infer/invent a stop or ETA (no AI ETA text — that's B7, Later); missing field = —, not a guess. And status never shows Acknowledged without a recorded ack — no false "all clear."
Decision Log (scope-protecting)

Cut compliance-flag alerts despite the feature name — they don't move BUG-2044 and would ~double QA in a 2-eng / 4-week / 3-account pilot.
Android-only, no iOS — discovery's sole device signal is an Android 12/13 finding; iOS doubles cert/build/QA for zero misery reduction.
Evals (3 targets)

Time-on-task: median commit→Acknowledged ≤ 60s (baseline 8–15 min); target 100% of tasks under 60s.
% accuracy: payload matches committed change record in 100% of trials — 0 invented/mismatched stop/ETA fields.
Safety trigger: 0 false "Acknowledged" states — count any unacked alert reading green; target zero.


_____

## Wireframes / prototype

_A visual or interactive model of your proposed solution._

 https://lovable.dev/projects/804ec31c-c201-484f-b26b-04ae98d0688e?magic_link=mc_a6c98b54-5e39-4bb1-b137-dae750da559f
