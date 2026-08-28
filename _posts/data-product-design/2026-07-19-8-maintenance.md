---
layout: post
title: "Maintenance: How Long Your Product Survives Depends on This Stage"
subtitle: "Three observability pillars, retrain vs. redesign, and the loop back to problem statement"
tags: [data-product, product-management, data-science]
comments: true
series: "Data Product Design for Data Scientists"
series_part: 8
---

Every stage in this series up to now builds toward a single launch moment. Maintenance is different: it has no defined endpoint, it's the longest phase by far, and it's the one that determines whether the work from Parts 1 through 7 keeps paying off or quietly stops mattering. Most data products don't die in a dramatic failure — they die slowly, unmonitored, until someone finally notices the numbers have been wrong for months.

## Three Pillars of Observability

A data product needs monitoring across three distinct layers, and they fail independently — healthy readings on one tell you nothing about the other two.

**1. Data Quality.** Is the input data still what the Part 3 requirements doc says it should be? Watch for:

- Schema changes upstream (a field renamed, a type changed, a new enum value nobody told you about)
- Missing or null rates shifting for fields the model depends on
- Volume anomalies — a source suddenly delivering far more or far fewer records than usual, often a sign of an upstream pipeline break rather than a real-world change

**2. Model Performance.** Is the model's statistical behavior still sound? Watch for:

- Prediction distribution drift — is the model's output shifting shape even before you have ground truth to check accuracy against?
- Feature drift — are the input feature distributions moving away from what the model was trained on?
- Realized accuracy against ground truth, once it becomes available (often lagged — credit risk models, for instance, may not have a clean outcome label for months)

**3. Business Metric Monitoring.** Is the product still delivering the outcome the Part 3 success criteria promised? Watch for:

- The actual business metric from your success criteria (not a proxy metric that's easier to compute) tracked over time, not just measured once at launch
- Whether the metric's improvement is holding, fading, or reversing as the initial post-launch period passes
- Whether usage or adoption itself is holding — a product stakeholders quietly stop consulting is failing on this pillar even if the model's statistics look fine

These three pillars are deliberately separate because a product can look perfectly healthy on one axis while failing badly on another: data quality can be pristine while the business metric drifts because the world changed in a way the model didn't capture; model performance can look statistically stable while a schema change upstream silently corrupts a feature. Monitor all three, not whichever is easiest to instrument.

## Retrain vs. Redesign: How to Tell Which One You Need

Not every degradation calls for the same fix, and picking the wrong one wastes effort without solving the actual problem.

- **Retrain** when the underlying relationship between inputs and outcome is still fundamentally the same, but the data has moved — new customer mix, seasonal shift, gradual drift within the same problem shape. A retrain on more recent data restores performance without touching the solution design from Part 3.
- **Redesign from scratch** when the root cause itself has changed, or your Part 2 root cause analysis turns out to have missed something that's now become unavoidable — a new fraud pattern the original feature set structurally cannot capture, a regulatory change that alters what decision is even allowed, a business process change that makes the original user story obsolete. No amount of retraining fixes a model built to answer a question that no longer matches reality.

A useful diagnostic: if retraining on recent data restores the success criteria without changing features, logic, or scope, it was a retrain problem. If retraining doesn't help, or helps only briefly before decaying again, that's a signal the root cause itself has shifted — and it's time to go back to Part 2, not to keep retraining the same design against a moving target.

## The Feedback Loop: Maintenance Surfaces New Pain Points

Treat maintenance as the stage that generates the next Part 2, not as a dead end. In production, a data product surfaces information that was invisible during design:

- Edge cases the original scope excluded turn out to be common enough to matter
- Stakeholders discover adjacent problems once they trust the first solution and start asking for more
- Monitoring itself reveals gaps in the original root cause analysis that weren't visible without live data

Every one of these is raw material for a fresh problem statement — a new user story, a new pain point, potentially a new root cause. The discipline is treating this as a deliberate re-entry into Part 2, with its own alignment session in Part 4, rather than quietly patching the live system in response to informal requests. A maintenance cycle that skips straight to code, the same way the very first request in Part 2 warned against, reintroduces exactly the risk this whole framework was built to avoid.

This closes the loop: Problem Statement → Solution Design → Alignment → Development → Review → Deployment → Maintenance → back to Problem Statement. Part 9 walks one real, anonymized project through this entire loop end to end, with a checklist template you can copy directly into your own next project.
