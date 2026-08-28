---
layout: post
title: "Problem Statement: Don't Rush to Build — Reframe the Problem First"
subtitle: "User story, pain points, root cause, and the trap of solving symptoms"
tags: [data-product, product-management, data-science]
comments: true
series: "Data Product Design for Data Scientists"
series_part: 2
---

Almost every data product starts with a request, not a problem statement: "Can you build a model to flag risky transactions?" "Can we get a dashboard for this?" "Can you predict which customers will churn?" These requests already contain an assumed solution. The first job of a Data Scientist acting as PO is to *not* accept the assumed solution and instead reconstruct the actual problem underneath it. Skipping this step is the single most common reason data products get built and then quietly abandoned.

## The Structure: User Story → Pain Points → Root Cause → Solution Design → Alignment

Treat every request as raw material for five sequential artifacts, in this order:

1. **User story** — who has this problem, and what are they trying to accomplish.
2. **Pain points** — what specifically is broken or costly about their current way of working.
3. **Root cause** — why that pain point exists in the first place.
4. **Solution design** — what you propose to build, informed by the root cause, not the surface request (covered in Part 3).
5. **Alignment** — stakeholders confirm all of the above before development starts (covered in Part 4).

This part covers the first three. Get these wrong, and everything downstream — however well engineered — solves the wrong problem faster.

## Writing a User Story for Non-Dev Stakeholders

Software teams write user stories like "As a user, I want to reset my password, so that I can regain access to my account." Data products need the same discipline, but stakeholders are usually risk officers, collection managers, or business analysts — not developers. Keep the format but make the language theirs:

> **As a** [specific role, not "the business"],
> **I want** [an outcome, not a feature],
> **so that** [the underlying goal this serves].

The two failure modes to avoid:

- **Too vague**: "As a manager, I want better visibility into risk, so that I can make better decisions." This validates nothing — everyone would agree with it, which means it isn't testable.
- **Too solution-shaped**: "As a manager, I want a real-time dashboard with a red/yellow/green risk indicator, so that I can act fast." This has already jumped to Part 3 (solution design) before the pain point is even understood.

A well-scoped example: "As a collections team lead, I want to know which delinquent accounts are worth a phone call this week, so that I don't spend agent hours on accounts that won't recover regardless." Notice this names a specific role, a concrete decision, and a reason — but says nothing yet about models, scores, or dashboards. That restraint is deliberate: it keeps the door open for Part 3 to evaluate multiple solution shapes on their merits.

## From Pain Points to Root Cause: 5 Whys for Business and Data Context

Once you have a user story, ask what specifically is painful about the current state. Then keep asking why, the same way manufacturing teams use the classic 5 Whys — except here the "why" chain usually runs through data, process, and incentive structures rather than mechanical failure.

Example chain:

- **Pain point**: Collections agents are calling accounts that never pay, wasting effort.
- **Why?** They call accounts in a fixed order (oldest first), not by recovery likelihood.
- **Why?** There's no ranking of which accounts are likely to respond to a call.
- **Why?** No one has ever segmented recovery behavior by account characteristics.
- **Why?** Historical call outcomes were logged in a system that was never connected to the loan servicing data.
- **Root cause**: A data integration gap prevents any recovery-likelihood signal from existing at all — not a lack of a model, but a lack of joined data.

Notice where this lands: the root cause is a data plumbing problem, not a modeling problem. If you had accepted the original framing ("build us a model"), you would have built a model on incomplete data and been surprised when it underperformed. The 5 Whys forced the real constraint to the surface *before* any development effort was spent.

Two adaptations matter when you apply 5 Whys in a data/business context rather than a factory floor:

- **Whys can branch.** Business causes are rarely a single chain — expect 2-3 plausible root causes per pain point, and investigate each until one clearly dominates.
- **Data-availability is a valid root cause.** In manufacturing, root causes are usually process or mechanical. In data work, "we don't collect this" or "these two systems have never been joined" is very often the real answer, and it changes the entire solution shape.

## The Trap: Solving the Symptom, Not the Root Cause

The most expensive mistake in this stage is building a solution that treats the pain point as if it *were* the root cause. It is seductive because symptom-level solutions are usually faster to build and demo well in the short term.

Going back to the collections example: if you skip root-cause analysis and jump straight to "build a churn-style model to predict who will pay," you might get a working model — but it will be trained on the same disconnected data, capped at the same ceiling, and you will have spent development time arriving at a marginal improvement instead of fixing the actual gap (the missing data join). Six months later, someone will ask "why isn't this model better?" and the honest answer will be "because we never fixed what was actually broken."

A quick self-check before moving to solution design: **can you state the root cause in one sentence that a business stakeholder would recognize as true, independent of any solution you're proposing?** If the "root cause" you've written already contains the word "model," "dashboard," or "automation," you haven't found the root cause yet — you've found a solution wearing a root-cause costume.

In Part 3, you will take this root cause and turn it into an actual solution design — including how to choose between a rule, a model, a dashboard, or an automation, and how to write requirements that a developer or fellow Data Scientist can pick up without needing you in the room.
