---
layout: post
title: "Full Case Study: Applying the Framework End to End"
subtitle: "One anonymized project through all three stages, plus a copy-paste checklist"
tags: [data-product, product-management, data-science]
comments: true
series: "Data Product Design for Data Scientists"
series_part: 5
---

This closing part walks one real project — details anonymized and simplified — through every stage covered in Parts 1 through 4, then leaves you with a checklist template built from the framework so you can apply it directly to your own next project.

## The Request, As It Arrived

A collections operations lead asked for "a model to help us prioritize which delinquent accounts to call first." This is the same shape of request Part 2 warns about: it names a role, but it has already jumped past the pain point straight to a solution ("a model") without anyone yet confirming what problem that model was supposed to solve.

## Stage 1 — Problem Statement

Reconstructing the user story: **as a collections team lead, I want to know which delinquent accounts are worth agent time this week, so that limited call capacity isn't spent on accounts that won't recover regardless.**

The pain point, once unpacked with the team: agents were calling accounts in a fixed queue order (oldest delinquency first), with no signal for which accounts were actually likely to respond. Applying the 5-Whys chain from Part 2 surfaced two candidate root causes, not one:

- Recovery outcome history existed but had never been joined to the servicing data used to build the call queue.
- Even where the join existed for a subset of accounts, no one had ever analyzed which account characteristics correlated with call responsiveness.

Both were real, but the first was the binding constraint — without the join, the second couldn't be evaluated at all. Root cause: **a data integration gap prevents any recovery-likelihood signal from being computed**, not an absence of a sophisticated model.

## Stage 2 — Solution Design

Applying the selection criteria from Part 3: the pattern (which accounts respond to calls) was plausibly complex enough to warrant more than a fixed rule, but the immediate blocker was data, not modeling technique. The solution design therefore had two phases, made explicit in the requirements doc rather than left implicit:

- **Phase A**: build the missing join between collections outcome history and servicing data — a data engineering task, not a modeling one.
- **Phase B**: once Phase A existed, a simple logistic regression scoring call-responsiveness likelihood, output as a daily-refreshed rank feeding the existing call queue tool.

Success criteria, defined before any modeling began: **reduce calls to accounts with no payment activity in the following 30 days by 20%, measured over one full quarter post-rollout, without reducing total dollars recovered.** That second clause mattered — it existed specifically to prevent the model from optimizing call efficiency by avoiding hard-but-recoverable accounts.

## Stage 3 — Alignment

The alignment session included the collections lead, a risk team representative, and the data engineering owner of the servicing tables — deliberately not run as separate technical and business conversations. Two outcomes from that session materially changed the plan:

- The risk representative flagged that a subset of accounts (active hardship/restructuring cases) needed to be excluded from automated de-prioritization for compliance reasons — this became an explicit "out of scope / excluded segment" item, not something discovered after launch.
- The collections lead pushed back on the initial success criteria timeframe (one month), correctly pointing out that call outcomes lag by several weeks — the quarter-long window in the final criteria came directly from that pushback, not from the original design.

Both changes were cheap at this stage and would have been expensive to discover after development had already started.

## What Alignment Bought Us

With the pain point, root cause, solution shape, and success criteria all confirmed in writing, the collections lead, the risk representative, and the data engineering owner walked away from that session with the same understanding of what would get built and why. The excluded hardship segment and the quarter-long measurement window were both decided here — cheaply — rather than surfacing as objections after something had already shipped. That written recap became the reference point for every conversation that followed, and the point at which "design" ends and execution begins.

## Copy-Paste Checklist Template

```plan
PROBLEM STATEMENT
[ ] User story written (role, outcome, reason) — not solution-shaped
[ ] Pain point stated in the stakeholder's own language
[ ] Root cause identified via Whys chain, stated without naming a solution
[ ] Checked: is the "root cause" actually a data-availability gap?

SOLUTION DESIGN
[ ] Solution type chosen against explicit criteria (rule / model / dashboard / automation)
[ ] One-page requirements doc: problem summary, inputs, outputs, logic, out-of-scope
[ ] Success criteria: business metric + number + timeframe + fallback plan

ALIGNMENT
[ ] Pain point confirmed by stakeholders in their own words
[ ] Root cause presented as hypothesis and confirmed or corrected
[ ] Solution and explicit out-of-scope items confirmed
[ ] Success criteria signed off with a number and timeframe
[ ] Written recap sent same day
```

That's the full design loop. The framework in this series isn't a substitute for modeling skill — it's the missing half of the job that determines whether that modeling skill ever gets built against the right problem in the first place. Treat each stage as seriously as you'd treat the model itself, and the gap between "good model" from Part 1 and "product actually used" closes considerably before a single line of code is written.
