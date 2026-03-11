---
layout: post
title: "A/B Testing Series (Part 4): Pitfalls Part 1"
subtitle: "Lucky day traps, SRM, base-rate mismatch, and data loss"
tags: [ab-testing, experimentation, data-quality]
comments: true
series: "A/B Testing From Zero to Decision"
series_part: 4
---

Even perfect statistics cannot fix broken experiment data. In this lesson, we focus on high-impact quality failures.

## Lucky Day Trap

A result can appear significant mainly because of one anomalous day.

Warning signs:

- Most lift comes from a single date window
- Removing one day changes the conclusion entirely
- Traffic behavior looks structurally different on that day

Action:

- Investigate incident logs, campaigns, and outages
- Re-run analysis excluding anomaly as sensitivity check
- Extend test if needed

## Sample Ratio Mismatch (SRM)

If you planned 50/50 assignment but observe a meaningful imbalance, randomization may be broken.

Potential causes:

- Assignment bugs
- Event drop in one variant
- Redirect or rendering failures
- Bot filtering asymmetry

Action:

- Stop trusting outcome metrics
- Diagnose assignment and tracking path
- Fix and rerun from scratch

## Base-Rate Mismatch

If control baseline differs strongly from expected historical rate, your original power assumptions may be invalid.

Action:

- Compare baseline with recent stable periods
- Recompute expected duration and MDE if necessary
- Document context shifts (seasonality, campaigns, product changes)

## Data Loss and Differential Tracking

Missing data is dangerous when loss is asymmetric between variants.

Example risk:

- Heavier treatment page causes more tracking failures, making treatment look worse artificially

Action:

- Cross-check client-side and server-side counts
- Monitor funnel step consistency by variant
- Exclude affected windows or rerun experiment

## Data Quality Gate Before Analysis

Only interpret effect size after these checks pass:

- Assignment integrity (including SRM)
- Tracking completeness
- Baseline sanity
- Day-level stability review

## Key Takeaways

- Trustworthiness comes before significance
- SRM and differential loss can invalidate the entire test
- Sensitivity analysis helps detect fragile conclusions

In Part 5, we continue with advanced pitfalls: peeking, underpowered inference, and "too good to be true" results.
