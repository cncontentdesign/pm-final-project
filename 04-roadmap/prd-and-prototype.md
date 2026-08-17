# PRD & Prototype Sprint (Module 4)

## Pick & scope with MoSCoW
- **The “Now” feature I’m scoping (name + one-line core description):** Driver Alert Notifications - Push alerts on route changes/compliance flags
- **My finalized Must-Haves (after overriding the AI):** Trigger on route-change / reassignment event
Targeted push to the specific affected driver(s)
Actionable payload: what changed + when (new/removed stop, new ETA window)
Driver acknowledgement — one-tap "Got it"
Delivery-failure surfaced to the coordinator (undelivered/token dead)
Device push-token registration + permission handling
- **What I demoted from Must → Should/Won’t, and why:** Ack state visible to the coordinator in real time (sent >> delivered >>  acknowledged) - moved to should - real time = additional infrastructure. Polling is enough to get 80% or more of the value.

Driver acknowledgement — one-tap "Got it" - moved to SHould. Cross-platform lock-screen action APIs can be brittle. Acknowledge on Open is a cheaper/more reliable substitute

## Generate your Simplified PRD
- **One thing my PRD makes explicit that a vague brief would have missed:** My PRD makes explicit that the alert is not adequate/complete/MVP without a confirmed acknowledgement the Coordinator can see on the board. The moment of misery isn't the missing notification, it's that the Coordinator can't trust the change has been seen by the driver, so they go to WhatsApp to verify.

## Prompt-to-prototype sprint
- **Where did the prototype reveal a gap in my PRD logic? (what I had to update):** My "amber = not acknowledged" state didn't work on screen — you can't tell a 10-second wait from a 10-minute one, which is the whole point. With more prompts / dev time we would need to add a time since sent or age to each alert. A time signal here is a Must.
- **My shareable prototype URL (Lovable: Share → Share Preview · Bolt: Publish → Web):** https://lovable.dev/projects/804ec31c-c201-484f-b26b-04ae98d0688e?magic_link=mc_a6c98b54-5e39-4bb1-b137-dae750da559f
