---
layout: post
title: "Solution Design: From Pain Point to Design Blueprint"
subtitle: "Choosing the right solution type, writing requirements, and defining success upfront"
tags: [data-product, product-management, data-science]
comments: true
series: "Data Product Design for Data Scientists"
series_part: 3
---

With a validated root cause in hand from Part 2, the temptation is to jump straight to modeling — it's the part of the job most Data Scientists enjoy most. Resist it for one more step. Solution design is where you decide *what kind* of thing you're building, write it down precisely enough that someone else could build it without you, and — critically — define what "done and working" means before a single line of code exists.

## Choosing a Solution Type: The Criteria That Actually Matter

A root cause does not imply one specific solution. The same root cause — "no ranking of recovery likelihood exists" — could be addressed by a rule, a statistical model, a dashboard, or a piece of automation. Each has a different cost, speed, and maintenance profile. Choose deliberately using these criteria:

| Solution Type | Best When | Cost to Build | Cost to Maintain | Risk |
| --- | --- | --- | --- | --- |
| **Rule-based** | Pattern is simple, well-understood, and stable (e.g. "flag if DPD > 90") | Low | Low, but rules rot silently as behavior shifts | Under-fits complex patterns |
| **Model** | Pattern is complex, enough labeled history exists, and the lift over rules is worth the overhead | Medium–High | Requires monitoring, retraining, ownership (Part 8) | Overfits, decays, needs explainability |
| **Dashboard** | The bottleneck is visibility, not decision automation — a human still makes the call | Low–Medium | Low, but only as good as the underlying metric definitions | Wrong metric ships, gets used wrong |
| **Automation** | The decision itself is simple and repetitive once the ranking/rule/model exists | Medium | Needs rollback and override paths | Removes a human check that was silently catching edge cases |

A rule of thumb: **don't reach for a model when a rule would do, and don't reach for a dashboard when the actual ask is a decision, not a view.** Many "we need a dashboard" requests are really "we need someone to decide something," and a dashboard just defers that decision indefinitely while looking like progress. Test this by asking: "If this dashboard existed today, what would you do differently tomorrow?" If the honest answer is "keep watching it," you haven't found a solution — you've found a reporting artifact.

Also weigh how root cause and solution type interact. In the Part 2 example, the root cause was a data integration gap. The correct first solution might not be a model at all — it might be "join the collections outcome table to the servicing data," with a simple rule or lightweight model layered on top only once that join exists. Solving the plumbing problem before reaching for the fancier solution is very often the higher-leverage move.

## Writing a "Development Plan + Requirements" Doc

The purpose of this document is narrow: a developer, another DS, or even future-you six months from now should be able to pick it up and build the thing without a meeting. Keep it to one page with these sections:

- **Problem summary** — one paragraph, restating the user story and root cause from Part 2 (not the original vague request).
- **Proposed solution** — the solution type chosen and why, referencing the criteria above.
- **Inputs** — exact data sources, tables, or fields required, and who owns them.
- **Outputs** — the exact artifact produced (a score, a flag, a table, a chart) and where it lands (an API, a table, a BI tool).
- **Logic / approach** — the rule, the modeling approach, or the transformation logic, at a level of detail someone could implement from.
- **Out of scope** — explicitly list what this version will *not* do. This single section prevents more scope creep than anything else in the document.
- **Success criteria** — see below; this is non-negotiable and belongs here, not in a separate afterthought.

Write this for the reader who wasn't in the room for the Part 2 conversation. If a sentence only makes sense to someone who already knows the backstory, rewrite it.

## Success Criteria: Defined Now, Not After Launch

The single biggest procedural mistake in data product work is deciding what "success" means only after the model is built — because by then, the definition of success quietly bends to match whatever the model actually achieved. Defining success criteria at design time, before you've seen results, is what keeps you honest.

Good success criteria are specific on three axes:

- **Business metric, not just model metric.** "AUC > 0.75" is not a success criterion a business stakeholder can validate. "Reduces wasted collection calls by 20% within one quarter of rollout" is.
- **A number and a timeframe.** Vague direction ("improve recovery rate") is not falsifiable. State the threshold and the window in which it will be measured.
- **A pre-agreed fallback.** Decide now what happens if the criteria aren't met — rollback, iterate, or kill the project. Deciding this under pressure after a disappointing launch produces worse decisions than deciding it upfront with a clear head.

Write these criteria into the requirements doc, then get explicit sign-off on them in the alignment session — which is the entire subject of Part 4, the stage most teams skip and the one that most reliably determines whether this project succeeds or quietly stalls.
