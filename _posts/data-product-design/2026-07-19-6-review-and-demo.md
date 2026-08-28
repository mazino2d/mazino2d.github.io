---
layout: post
title: "Review & Demo: Present to Get Approved, Not to Show Off"
subtitle: "Structuring a convincing demo, storytelling with data, and handling objections"
tags: [data-product, product-management, data-science]
comments: true
series: "Data Product Design for Data Scientists"
series_part: 6
---

A demo has exactly one job: get the audience to approve moving forward. It is not a venue for showing off modeling technique, and treating it as one is a common way to lose an audience that came in ready to say yes. Everything in this stage should be shaped around the decision you need stakeholders to make at the end of the meeting.

## Structuring a Convincing Demo: Problem → Solution → Impact → Next Step

Resist the instinct to open with methodology. The audience in this meeting is usually the same stakeholders from the Part 4 alignment session — they don't need to be re-sold on why the problem matters from scratch, but they do need to see the through-line from that alignment to what's in front of them now. A structure that works reliably:

1. **Problem** — restate the pain point and root cause exactly as aligned in Part 4, in one or two sentences. This isn't filler — it re-anchors the room on the specific, agreed problem, not a generic one, and it's your first checkpoint that nothing has silently drifted since alignment.
2. **Solution** — describe what was built, at the level of "what it does," not "how it works." Save architecture and modeling detail for an appendix or a follow-up technical session with whoever actually needs it.
3. **Impact, in numbers** — this is the core of the meeting. Show the measured result against the success criteria agreed in Part 3, not a different metric that happens to look better. If the agreed criterion was "reduce wasted collection calls by 20%," report against exactly that number — substituting a flattering but different metric here is the fastest way to lose credibility with a room that remembers what was promised.
4. **Next step** — end with a specific ask: approve deployment, approve a pilot, approve additional data access. A demo that ends with "any questions?" instead of a concrete ask wastes the momentum of everything before it.

Keep the whole narrative anchored to the same four things from the Part 4 alignment: pain point, root cause, solution, success criteria. If the audience agreed to those four things going in, the demo's job is simply to show that the built solution honored them — not to introduce new framing at the last moment.

## Storytelling With Data for Non-DS Audiences

Non-technical stakeholders don't process a confusion matrix or an ROC curve the way a Data Scientist does — and asking them to is putting the burden of translation on the wrong person in the room. A few practical rules that work well in front of business and risk audiences:

- **Lead with the business unit, not the statistical one.** "This saves the collections team roughly 400 wasted calls a month" lands; "precision improved from 0.61 to 0.74" does not, even though it's the same underlying result.
- **One number per slide, not a table of them.** A dense metrics table invites the room to hunt for a number that looks bad instead of absorbing the one that matters. Pick the single number tied to the success criterion and let it stand alone.
- **Show before/after, not just after.** A simple comparison — calls made under the old process vs. the new one, for the same time period — communicates impact faster than an abstract improvement percentage.
- **Use a visual only if it removes a sentence of explanation, not adds one.** A chart that needs a paragraph of caption to interpret is worse than no chart at all in front of this audience.

The goal is for someone in the room to be able to repeat the headline result accurately to their own boss immediately after the meeting, without needing you there to translate it again.

## Handling Feedback and Objections in the Room

Objections in a review meeting are not the meeting going badly — they're often the meeting doing exactly its job, and how you receive them is what determines whether the room feels good about approving. A few patterns worth having ready:

- **"The results look too good."** Don't get defensive. Walk through how the evaluation was set out (holdout period, out-of-time validation) and welcome scrutiny — a stakeholder who pressure-tests the number now is doing you a favor compared to one who trusts it blindly and gets surprised in production later.
- **"What about edge case X?"** If it was explicitly scoped out in Part 3, say so plainly and reference the recap document from Part 4 — this is exactly the artifact that turns "did we agree to skip this?" from a debate into a lookup. If it wasn't scoped out and is a genuine gap, don't improvise an answer on the spot — commit to following up, and actually do it.
- **"Can we also add Y?"** New scope requests at demo stage are common and usually well-intentioned. Acknowledge the idea, but explicitly route it to a future cycle rather than agreeing to fold it in immediately — expanding scope in the room, under social pressure, is how "approve this" meetings quietly turn into "let's also rebuild half of it" meetings.
- **Silence.** A quiet room is not agreement. Ask directly: "does this meet the bar we set in [alignment date]?" and wait for an actual answer before moving to the next step.

Leave the meeting with an explicit decision, in writing, ideally within the meeting itself: approved to deploy, approved for a pilot, or specific conditions to be met before approval. Part 7 assumes you're walking out of this meeting with a clear yes — and covers everything that needs to be in place before you actually flip the switch.
