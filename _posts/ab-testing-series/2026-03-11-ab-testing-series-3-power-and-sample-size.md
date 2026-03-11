---
layout: post
title: "A/B Testing Series (Part 3): Power and Sample Size"
subtitle: "How to design experiments that can actually detect real effects"
tags: [ab-testing, power-analysis, statistics]
comments: true
series: "A/B Testing From Zero to Decision"
series_part: 3
---

Many teams run experiments that cannot detect meaningful effects. This is a planning failure, not an analysis failure.

## What Is Statistical Power?

Power is the probability of detecting a real effect of a specific size:

$$
\text{Power} = 1 - \beta
$$

Typical target: 80% or 90%.

Low power means you can easily miss wins and wrongly conclude "no effect".

## Inputs for Sample Size

To calculate required sample size per variant, specify:

- Baseline conversion rate
- Minimum detectable effect (MDE)
- Significance level $\alpha$
- Desired power

Smaller MDE requires much larger sample.

## MDE: The Product Lens

MDE is the smallest effect worth detecting.

Set MDE based on business value, not wishful thinking.

- If MDE is too small, tests become impractically long
- If MDE is too large, you may miss meaningful improvements

A good MDE balances decision value and experiment cost.

## Duration Planning

If required sample is 20,000 users total and traffic is 1,000 users/day, run at least 20 days.

Do not stop early just because interim results look promising.

## Why Underpowered Tests Waste Time

Underpowered tests increase:

- False negatives
- Unstable conclusions
- Team disagreement and retest cycles

They often produce inconclusive outcomes that still consume engineering and opportunity cost.

## Practical Planning Checklist

- Define primary metric and MDE
- Compute sample size before launch
- Estimate duration from traffic realistically
- Freeze analysis plan (including stopping rule)
- Share assumptions with stakeholders

## Key Takeaways

- Power planning is mandatory for credible experimentation
- MDE should reflect real business decisions
- No sample-size plan usually means unreliable outcomes

In Part 4, we move from theory to common failure modes that invalidate otherwise well-planned tests.
