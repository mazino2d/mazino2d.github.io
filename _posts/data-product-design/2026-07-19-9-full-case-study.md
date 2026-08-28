---
layout: post
title: "Full Case Study: Applying the Framework End to End"
subtitle: "One anonymized project through all five stages, plus a copy-paste checklist"
tags: [data-product, product-management, data-science]
comments: true
series: "Data Product Design for Data Scientists"
series_part: 9
---

This closing part walks one real project — details anonymized and simplified — through every stage covered in Parts 1 through 8, then leaves you with a checklist template built from the framework so you can apply it directly to your own next project.

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

Both changes were cheap at this stage and would have been expensive to discover after Phase B was already built and deployed.

## Stage 4 — Solution Development

Phase A (the data join) took longer than the modeling itself — consistent with the MVP guidance in Part 5 to validate the pipeline before the model. Phase B started with a plain logistic regression on a handful of account and payment-history features. It cleared the success criteria in backtesting without needing anything more complex, so no further model sophistication was added. Weekly two-line updates went to the collections lead throughout Phase A, since that phase had no visible output yet and was the phase most at risk of feeling like silent progress.

## Stage 5 — Review, Deployment & Maintenance

The demo followed the Part 6 structure — problem, solution, backtested impact against the exact agreed metric, and a specific ask (approval for a soft launch on 20% of the queue). Two objections came up: a question about the excluded hardship segment (answered directly by pointing to the alignment recap) and a request to also rank accounts by expected recovery *amount*, not just likelihood — logged explicitly as a future-cycle candidate rather than folded in immediately.

Deployment followed the Part 7 staged approach: two weeks in shadow mode comparing the new ranking against actual outcomes without changing agent behavior, then a 20% soft launch, then a phased widen after the monitoring in Part 8 confirmed stability across all three observability pillars. Three months in, the business metric monitoring pillar showed the reduction in wasted calls holding steady — with usage data showing the collections team had, on their own, started requesting the ranking be extended to a second product line, which became the next cycle's Part 2.

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

SOLUTION DEVELOPMENT
[ ] Simplest viable approach tried first
[ ] Data pipeline validated before modeling complexity added
[ ] "Wrong" vs. "not yet optimal" issues explicitly separated
[ ] Regular, short progress updates sent to non-technical stakeholders

REVIEW & DEMO
[ ] Structure: problem → solution → impact (against agreed metric) → next step
[ ] Impact reported against the exact success criteria metric, not a substitute
[ ] Explicit ask made at the end of the meeting
[ ] Objections logged and routed (answered now, or committed to a follow-up)

DEPLOYMENT
[ ] Monitoring live before go-live, not planned
[ ] Rollback plan defined with a named owner and explicit trigger
[ ] Product ownership assigned to a specific person
[ ] Staged rollout planned (shadow / pilot / phased widen)

MAINTENANCE
[ ] Data Quality monitoring in place
[ ] Model Performance monitoring in place
[ ] Business Metric monitoring in place, tracked over time
[ ] Retrain-vs-redesign criteria defined for when performance degrades
[ ] New pain points surfaced in production routed back to Problem Statement
```

That's the full loop. The framework in this series isn't a substitute for modeling skill — it's the missing half of the job that determines whether that modeling skill ever reaches production and stays useful once it's there. Treat each stage as seriously as you'd treat the model itself, and the gap between "good model" from Part 1 and "product actually used" closes considerably.
