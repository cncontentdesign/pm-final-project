# GTM Strategy & Success Dashboard

> Module 6 · Launch Impactful GTM Plans — ★ Deliverable 6
>
> Scenario B, RouteLogic Velocity. Feature: Driver Alert Notifications

## Go-to-market summary

**Feature.** Driver Alert Notifications. When a dispatcher reassigns a route, the affected driver gets an instant push (what changed, which stop, by when) and taps "Got it". The acknowledgement shows up on the board, so the dispatcher sees the driver has the right route without picking up the phone. It fixes BUG-2044, the 8 to 15 minute reassignment lag that taught dispatchers to stop trusting the board.

**Goal.** Engagement. These are existing customers, so it's a retention play. It only pays off if frontline dispatchers actually change how they work and trust the board again instead of running WhatsApp on the side (UXR-02).

**Audience.** Frontline dispatchers at our 2 to 3 pilot accounts and the wider at-risk cohort CS has flagged. Behind them, the ops managers and admins who own the renewal.

**Size.** M, targeted. Small reach on purpose, but these are our biggest, most at-risk enterprise contracts. It needs a real go-to-market because we're asking people to change a habit, and that won't happen if nobody tells them the board is fixed. It doesn't need a press push at prospects.

**Channels (all owned).** In-app notification with a short walkthrough (reaches the dispatcher where the work happens). Customer newsletter and admin update (reaches the admins and execs who hold the renewal). Direct CSM outreach, one to one, on the named accounts. Paid and earned add little for a known list.

**Enablement.** Sales just need their reliability talk track refreshed. CS need early access and a heads-up for QBRs and renewals. Support need an FAQ (Android-only, the Sent/Delivered/Acknowledged states, the amber and superseded cases). Assets: one-page explainer, 90-second demo clip, in-app walkthrough, release note, newsletter blurb, Support FAQ.

**Owners.** In-app: Chris (PM). Newsletter, clip and release note: Fiona (PMM). CSM outreach: named CSM. Support readiness: named Support lead. Budget is near zero since it's all owned, so the real cost is time plus the walkthrough tooling. We can't build iOS (Android-only for now), and engineering capacity is the constraint (2 engineers, 4 weeks, 3 accounts).

**Timeline.** Phase 1, a 90-day beta on pilot accounts with instrumentation from day one. Phase 2, the launch moment at the 90-day read: if the gate is met, roll to the wider cohort and fire all three channels. Phase 3, 30 to 60 days of monitoring, expanding towards GA and retiring the WhatsApp messaging.

**Post-launch call.** Most likely double down, triggered by the 90-day read hitting acknowledgement time under 60s at 15% lift or better (p < 0.05) with guardrails holding. Iterate if the direction is right but under the MDE. Pull back if the guardrail drops. The bad signal I'm watching for is people opening the announcement and finishing the walkthrough while adoption stays flat and WhatsApp keeps running, which would mean the message landed but the trust didn't.

## Success dashboard

| KPI | Type | Baseline | Target | Window |
|---|---|---|---|---|
| Alert-flow adoption (dispatchers who reassign through the alert at least once) | GTM, engagement | 0% | 70%+ of target dispatchers | First 30 days |
| Ack-on-board usage (confirmed on the board, not off-platform) | GTM, engagement | ~0% | 60%+, rising | Rolling 30 days |
| Announcement to walkthrough completion | GTM, engagement | 0% | 50%+ | First 14 days |
| Reassignment to acknowledgement time (median) | North-star | 8 to 15 min | under 60s | 90-day pilot |
| Dispatch-workflow completion (Open to Shift Handoff) | Outcome | 31% | 65%+ | 90-day pilot |
| Core-feature adoption (Board, Optimizer) | Guardrail | 91% / 85% | Must not drop | Throughout |
