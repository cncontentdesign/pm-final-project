# GTM Strategy & Success Dashboard (Module 6)

## Get your prior work ready
- **The feature you're launching from your M4 PRD, one feature, not a list:** Driver Alert Notifications — instant, targeted push to the affected driver on a route reassignment, acknowledged back on the board (Sent → Delivered → Acknowledged).
- **What your M5 experiment told you shipped / iterating, the evidence behind the launch:** I believe that Driver Alert Notifications, for the mid-size 3PL dispatcher who keeps a live fleet routed correctly and needs to know in real time where every stop stands, will pull live coordination back onto the platform and cut daily wasted time in half — measured by reassignment→acknowledgement time dropping from 8–15 min to < 60s within 90 days.
  We ship if that ack-time improves by **≥ 15% at p < 0.05** *and* Coordinator core-feature adoption (Board 91%, Optimizer 85%) does **not** drop. We iterate if the direction is positive but lift is below the MDE. We kill if the primary metric shows no improvement or moves negatively. The read date is fixed at end of 90 days — no results reviewed before then.
- **Your persona pull your M2 persona, this anchors your audience:** A mid-size 3PL dispatcher (coordinator) responsible for keeping a live fleet routed correctly and knowing, in real time, where every stop stands — today forced to run a WhatsApp group as "the real system" because the board can't be trusted (UXR-02).

## Set your goal, then your audience
- **Primary GTM goal awareness · engagement · conversion, pick one:** Engagement.
- **Why this goal? what makes this the right goal for this feature right now:** This is a retention play, not a demand-gen one. These accounts already pay us; the risk is that their frontline dispatchers have quietly defected to WhatsApp and their execs are trialling leaner rivals (M1 churn crisis). The launch only works if the *right users start using the board differently* — reassigning through the alert flow instead of the phone. So success is behaviour change (engagement) among an existing audience, not net-new sign-ups.
- **Target audience the specific segment your goal implies, be precise:** Two rings.
  **Primary:** frontline fleet dispatchers/coordinators at the 2–3 enterprise pilot accounts (the M3/M5 retention cohort) plus the wider at-risk cohort — mid-size and enterprise 3PL accounts where telemetry/CS flags a live WhatsApp-workaround pattern.
  **Secondary (influence, not usage):** the ops managers and account admins at those same accounts who sign the renewal — reached so they see the board becoming trustworthy again ahead of the contract conversation.

## Size your launch
- **Launch tier S (minimal) · M (targeted) · L (multi-channel) · XL (full GTM):** M — targeted. The right people at the right named accounts, not the whole market.
- **Justification reach + revenue impact + what silence would risk:** Reach is deliberately narrow (dispatchers at a handful of named, at-risk accounts), but the revenue behind them is our largest enterprise contracts — the existential NRR threat from M1, where 4 of 5 churning accounts cited complexity. So low reach, disproportionately high revenue impact. **Silence risks the whole bet:** if we ship quietly, the dispatchers who already stopped trusting the board never learn it's fixed, keep running WhatsApp, the pilot shows no engagement lift, and we lose the retention proof point right before renewals. Equally, an XL market launch would be wrong — this is a trust/reliability fix for existing users, not a prospect-facing differentiator, and over-hyping a bug fix invites scrutiny we don't want.
- **Is this a launch or a release? does it need go-to-market, or can it just ship?:** A launch — but a targeted, inward-facing one. The feature can technically just ship, but the *goal* (dispatchers returning to the board and dropping WhatsApp) is a behaviour change that won't happen on its own. It needs go-to-market to the existing at-risk accounts to drive adoption and to be visible to the renewal owners. It does **not** need a market/press launch to prospects.

## Choose your top three channels and plan assets
- **Channel 1 owned / earned / paid, and why it reaches your audience:** **Owned — in-app notification + guided walkthrough.** Reaches the dispatcher exactly where the behaviour lives (on the board, mid-shift). A short in-product walkthrough of the reassign → *Got it* → *Acknowledged* loop shows the new confirmation lands *on the board*, which is the whole trust argument.
- **Channel 2 owned / earned / paid, and why:** **Owned — customer newsletter / account admin update.** Reaches the customer admins and execs (the secondary ring) who can cascade the message to their dispatch teams and who hold the renewal. Same story, framed for the buyer: "the board is now the single source of truth again."
- **Channel 3 owned / earned / paid, and why:** **Owned — direct CSM / account-team outreach (1:1).** The highest-signal channel for an M-tier launch to *named* accounts. The CSM walks each pilot/at-risk account through the change in a check-in or QBR, confirms dispatchers are using it, and turns adoption into a renewal talking point. Paid/earned add nothing here — the audience is a known, finite list.
- **Enablement & assets what Sales / CS / Support need, plus the assets to build (one-pager, demo, etc.):** For **Sales**, this is an update to existing assets — a nice reliability win for current customers, not a net-new prospect hook; refresh the "board reliability" talk track only. **CS** need early access, awareness, and a talking point so they can raise it with their accounts in QBRs and renewal conversations. **Support** need an internal FAQ (Android-only scope, what the Sent/Delivered/Acknowledged states mean, the "superseded" and amber "unacknowledged" states, no iOS path). Assets to build: (1) one-page "what changed & why it matters" explainer for dispatchers; (2) a ~90-second demo clip/GIF of the reassign → Got it → Acknowledged loop; (3) in-app walkthrough + tooltip; (4) release note; (5) newsletter blurb; (6) Support FAQ.

## Make it executable
- **Ownership named owner per key activity, individual, not department:**
  - Channel 1 — in-app notification + walkthrough — **Chris, PM**
  - Channel 2 — customer newsletter / admin update — **Fiona, PMM**
  - Channel 3 — direct CSM outreach to named accounts — **[Terry, CSM]**
  - Demo clip + one-pager + release note — **Fiona, PMM**
  - Support FAQ + Support readiness — **[named Support lead]**
- **Budget & resource gaps what costs extra, and any asset you can't currently build:** Near-zero cash — all three channels are owned. Real costs are people/time, not spend. Gaps: (1) the demo clip needs design/enablement time; (2) the in-app walkthrough depends on our walkthrough tooling (Pendo/Appcues) already being licensed — if not, that's the one line item. Can't currently build: an **iOS** driver experience (Android-only per PRD FR7) and any AI-generated ETA copy (out of scope, that's B7). Engineering capacity is the binding constraint — 2 engineers / 4 weeks / 3 accounts for the pilot.
- **Timeline Phase 1 beta → Phase 2 launch moment → Phase 3 post-launch:**
  - **Phase 1 — Beta (Days 0–90):** enable for the 2–3 pilot accounts; CSM-led onboarding; in-app walkthrough live for those accounts only. Instrument adoption + ack-time from day one.
  - **Phase 2 — Launch moment (Day 90 read):** if the M5 gate is met (ack-time < 60s, ≥ 15% lift at p < 0.05, adoption guardrail holds), roll to the wider at-risk cohort — newsletter + admin update + in-app announcement fire together.
  - **Phase 3 — Post-launch (Days 90–150):** monitor 30–60 days, expand toward GA for all board accounts, retire the WhatsApp-workaround messaging, and feed the next trust features (compliance-flag alerts, B7 AI ETA) into the roadmap.

## Define how you'll know it worked
- **Success metrics 2 to 3 metrics that match your GTM goal:** (goal = engagement, so these measure whether the audience *adopted the behaviour*, not just whether the feature works)
  1. **Alert-flow adoption** — % of dispatchers at target accounts who commit ≥ 1 reassignment through the alert flow in the first 30 days. Target **≥ 70%**.
  2. **Ack-on-board usage** — % of reassignments confirmed via on-board acknowledgement (vs a manual/WhatsApp confirm). Target **≥ 60%** of reassignments, trending up. This is the WhatsApp-replacement signal.
  3. **Launch engagement** — in-app announcement open + walkthrough-completion rate among target dispatchers. Target **≥ 50%** completion.
  _Underlying product north-star (from M3/M5): reassignment→ack time 8–15 min → < 60s; dispatch-workflow completion 31% → ≥ 65%._
- **Bad signal to watch for e.g. high reach, zero signups = message-market mismatch:** High announcement opens / walkthrough completion **but** flat alert-flow adoption and WhatsApp still running = message landed, trust didn't — a message-market (or credibility) mismatch, not a reach problem. Second bad signal: adoption climbs **but** the Board/Optimizer adoption guardrail slips = the alert added friction and is pulling dispatchers off the board (a kill trigger from M5).
- **Most likely post-launch decision double-down · iterate · pivot · deprioritize, and what would trigger it:** Most likely **double-down** — the evidence base is strong. **Trigger:** at the fixed Day-90 read, ack-time < 60s with ≥ 15% lift (p < 0.05) and the adoption/CSAT guardrails intact → expand to GA and green-light the next trust feature. **Iterate** if direction is positive but lift is below the MDE (tune the walkthrough / CSM push, re-read). **Deprioritize/pivot** if announcement engagement is high but behaviour doesn't change, or if the guardrail drops.

---

## Success dashboard

| KPI | Type | Baseline | Target | Measurement window |
|---|---|---|---|---|
| Alert-flow adoption (dispatchers using reassign→alert ≥ 1×) | GTM · engagement | 0% (new) | ≥ 70% of target-account dispatchers | First 30 days per account |
| Ack-on-board usage (reassignments confirmed on the board vs off-platform) | GTM · engagement | ~0% (WhatsApp today) | ≥ 60% and rising | Rolling 30 days |
| In-app announcement → walkthrough completion | GTM · engagement | 0% (new) | ≥ 50% | First 14 days of announcement |
| Reassignment → acknowledgement time (median) | Product north-star | 8–15 min | < 60s | 90-day pilot |
| Dispatch-workflow completion (Open → Shift Handoff) | Product outcome | 31% | ≥ 65% | 90-day pilot |
| Coordinator core-feature adoption (Board 91% / Optimizer 85%) | Guardrail | Board 91% / Optimizer 85% | Must not drop | Throughout |
