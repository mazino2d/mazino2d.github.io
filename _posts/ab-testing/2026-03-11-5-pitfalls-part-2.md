---
layout: post
title: "Pitfalls Part 2"
subtitle: "Twyman's Law, underpowered tests, peeking, and overdue experiments"
tags: [ab-testing]
comments: true
series: "A/B Testing"
series_part: 5
---

This lesson covers the mistakes that often look harmless in the moment but can quietly destroy decision quality.

## Twyman's Law: Too Good to Be True

When a result looks extraordinary, suspect instrumentation before celebrating.

Signals:

- Unrealistically large uplift
- Extremely tiny p-values with weak business rationale
- Sudden jumps inconsistent with historical variance

Action:

- Audit event definitions and pipelines
- Validate segmentation and exclusion logic
- Replicate before full rollout

## Underpowered Experiments

A non-significant result from a low-power test is usually not evidence of no effect.

Action:

- Quantify achieved power post-hoc
- Inspect confidence interval width
- Decide whether to extend, redesign, or stop with explicit uncertainty

## Peeking and Early Stopping

Repeatedly checking results and stopping at first significance inflates false positives.

Safer alternatives:

- Fixed-horizon analysis
- Sequential methods designed for continuous monitoring
- Pre-registered decision thresholds

## Overdue Experiments

Running far beyond planned horizon can invite p-hacking and context drift.

Risks:

- Seasonality shifts
- Product environment changes
- Stakeholder pressure to force significance

Action:

- Anchor decisions to the preplanned analysis window
- Treat extension as a new, documented phase

## Discipline Framework

Before launch, define:

- Sample size and duration
- Primary endpoint
- Stopping rule
- Handling for anomalies and monitoring cadence

Strong process discipline prevents weak inference.

## Key Takeaways

- Extraordinary results require extraordinary validation
- Non-significance without power context is incomplete
- Monitoring discipline is a core part of experiment design

In Part 6, we combine everything into a practical decision framework: Trust, Implement, Follow-up.
