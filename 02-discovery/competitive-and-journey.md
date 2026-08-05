# Competitive Analysis & Journey Map (Module 2)

## Responses
- **Role, who are you solving for? (the specific user segment or profile):** A mid-size 3PL dispatcher responsible for keeping a live fleet routed correctly and knowing, in real time, where every stop stands.
- **Goal, what is this user ultimately trying to achieve?:** To reassign routes and read accurate delivery status off a single trustworthy board, without a phone in the other hand.
- **Friction, the main barrier (moment of misery) stopping them from succeeding:** The board lies to them. A reassignment takes 8–15 minutes to reach the driver with no push notification (BUG-2044), and completed stops still read "in progress" for up to an hour (BUG-2072). Their verdict is the churn signal in miniature: "We keep a WhatsApp group as the real system" (UXR-02) — the coordinator has already replaced the product with a manual workaround.
- **External tools, the outside platforms or tools the user is forced to use:** A WhatsApp group as the de facto real-time system (UXR-02: "the real system").
Direct voice calls to the office/drivers when data is lost or ambiguous (UXR-03: Elena had to call the office to read them to me off a screen).
Inbound driver texts they must catch and log, because drivers push completion off-platform too (UXR-01: Diego "just texting my dispatcher instead").
- **The process, the 3 to 5 manual steps the user takes to get the job done:** Make the route reassignment in the app, then immediately distrust it (8–15 min lag, no notification).
Re-send the same change to the driver over WhatsApp so they see it now, and wait for a manual reply to confirm receipt.
Treat the board's delivery status as unreliable — assume "in progress" may already be delivered.
Ping each driver on WhatsApp to confirm actual stop status, then hold the true state in the chat thread, a side note, or their head.
Repeat per driver, per stop, continuously — running WhatsApp and the app as two parallel systems all shift.
- **Core frustration, the exact moment the process feels most “broken”:** The instant they look at their own dashboard to answer "where is everything right now?" — and know they can't trust the answer. The board shows a route that's already been changed and stops marked "in progress" that were delivered an hour ago, so the single screen built to give them real-time truth is the one thing they've learned to disbelieve. Their goal was one trustworthy board; the broken moment is realizing they need a phone in the other hand to verify it.
- **The evidence, a specific quote or behavior from the research that proves this:** Direct quote: "We keep a WhatsApp group as the real system." (UXR-02)
Corroborating behavior: "A stop shows 'in progress' when it was delivered an hour ago. I can't trust the board." (UXR-09)
Supporting bugs: BUG-2044 (reassignments lag 8–15 min, no push) and BUG-2072 (status lags 20–60 min on the dashboard).
- **📎 Your journey map, a shareable link, or the map file you committed (e.g. journey-map.html):** routelogic-velocity-future-state.html
