---
layout: post
title: "Solution Development: Build Right, Build Enough"
subtitle: "MVP mindset for data products, balancing rigor with deadlines, and communicating progress"
tags: [data-product, product-management, data-science]
comments: true
series: "Data Product Design for Data Scientists"
series_part: 5
---

With alignment locked from Part 4, development finally starts — and this is where the temptation to over-engineer is strongest, because building is the part Data Scientists are best at and most eager to do well. The discipline in this stage is not technical skill, which you already have. It's knowing when "good enough to test the hypothesis" beats "as good as I could eventually make it."

## MVP Mindset for Data Products

MVP in software usually means shipping a thin slice of a feature. For data products, the equivalent discipline is: **start with the simplest model or rule that could plausibly meet the success criteria, and only add complexity the data proves you need.**

Concretely:

- **Start with a rule or a simple model, not the fanciest architecture you know.** A logistic regression or a handful of business rules will tell you within days whether the signal exists at all. A gradient-boosted ensemble with extensive feature engineering might tell you the same thing three weeks later — and if the signal isn't there, you've spent three weeks discovering that a rule could have told you in three days.
- **Validate the data pipeline before validating the model.** More data products fail because an input feed was stale, mis-joined, or had a subtle timing leak than because the modeling technique was wrong. Confirm your inputs are actually what the requirements doc says they are before investing in modeling sophistication.
- **Add complexity only when the simple version measurably falls short of the success criteria from Part 3** — not because a more sophisticated approach is available, or interesting, or would look better in a portfolio. The success criteria you aligned on is the bar; clearing it with a simpler model is a win, not a compromise.

This mindset also protects you later: a simpler model is easier to explain in the Part 6 demo, easier to monitor in Part 8, and easier to debug when something drifts. Complexity you didn't need is a maintenance cost you'll pay for the life of the product.

## Balancing Technical Correctness and Business Deadlines

Data Scientists tend to have a high internal bar for "correct" — properly handled class imbalance, rigorously validated feature stability, carefully tuned thresholds. Business deadlines rarely wait for that bar to be fully cleared. The job in this stage is judging, explicitly, which imperfections are acceptable for this release and which are not.

A useful filter: separate issues into **"wrong" vs. "not yet optimal."**

- **Wrong** means the output could be actively misleading or harmful if shipped as-is: a data leak inflating offline metrics, a fairness issue in a regulated decision, a broken edge case that silently produces nonsense for a meaningful share of records. These block shipping, deadline or not — surfacing a wrong result on time is worse than a correct one shipped late, and it's usually far cheaper to say so before launch than to explain it afterward.
- **Not yet optimal** means the model works and clears the success criteria, but could be improved with more time: a slightly better feature set, a more efficient training pipeline, tighter hyperparameters. These are exactly what the maintenance and iteration cycle in Part 8 exists for. Shipping "not yet optimal but correct and aligned" on time beats shipping "more optimal" three weeks late.

Make this distinction explicit to yourself before every development decision, and be honest about which category a given shortcut falls into — the failure mode to watch for is quietly reclassifying a "wrong" issue as merely "not yet optimal" because the deadline is close.

## Communicating Progress to Non-Technical Stakeholders

Silence during a multi-week build is what erodes stakeholder trust, even when the work is going fine. Non-technical stakeholders don't need — and usually don't want — updates about feature engineering or hyperparameter search. They need answers to three recurring questions, delivered on a predictable cadence:

- **Are we still on track against the timeline we agreed on?** A simple on-track / at-risk / blocked status, not a narrative.
- **Has anything changed about scope, root cause, or success criteria since alignment?** If yes, this is a trigger to go back to Part 4, not something to mention in passing.
- **Is there anything you need from me?** Access to a data source, a decision on an edge case, clarification on a business rule — surfacing blockers early keeps a stakeholder from becoming a bottleneck later.

A short weekly written update covering these three points, even two sentences long, does more for stakeholder confidence than an impressive final demo after weeks of silence. It also means the Part 6 demo isn't the first time anyone has heard how the work is progressing — which changes the entire tone of that meeting from "convince me this worked" to "confirm what we already expected."

In Part 6, you'll take the finished (or MVP-complete) solution and structure a demo that gets it approved — not one that showcases the modeling work for its own sake.
