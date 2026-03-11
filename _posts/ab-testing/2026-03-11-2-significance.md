---
layout: post
title: "Statistical Significance"
subtitle: "P-values, confidence intervals, and Type I/II errors"
tags: [ab-testing]
comments: true
series: "A/B Testing"
series_part: 2
---

In Part 1, we defined the mechanics of an A/B test. Now we answer the hard question: when is a difference convincing?

## P-Value in Plain Language

A p-value answers:

If the null hypothesis were true, how likely is data this extreme (or more extreme)?

Small p-values indicate that the observed difference is unlikely under $H_0$.

Common rule:

- If $p < 0.05$, reject $H_0$
- If $p \ge 0.05$, do not reject $H_0$

Important: p-value is not the probability that $H_0$ is true.

## Confidence Intervals Add Magnitude

A 95% confidence interval for uplift gives a plausible range for the true effect.

Interpretation pattern:

- Interval fully above 0: likely positive effect
- Interval includes 0: inconclusive
- Interval fully below 0: likely negative effect

Confidence intervals are decision-friendly because they combine significance and practical impact.

## Type I and Type II Errors

Every test design is a trade-off.

- Type I error ($\alpha$): false positive, detecting an effect that is not real
- Type II error ($\beta$): false negative, missing a real effect
- Power: $1 - \beta$, probability of detecting a true effect of a given size

Reducing one error usually increases the other unless you increase sample size.

## One-Tailed vs Two-Tailed

Two-tailed tests are usually safer in product work because they detect both improvement and harm.

Use one-tailed tests only when:

- You pre-register the directional hypothesis
- Harm in the opposite direction is not operationally relevant

## Common Misinterpretations

- "p = 0.03 means 97% chance treatment wins" (incorrect)
- "Non-significant means no effect" (incorrect, could be underpowered)
- "Significant means large impact" (incorrect, effect could be tiny)

## Practical Decision Rule

For most product experiments:

- Require data quality checks to pass
- Use two-tailed test at predefined $\alpha$
- Evaluate 95% confidence interval for practical significance
- Decide based on impact, not only significance

## Key Takeaways

- P-values quantify surprise under the null
- Confidence intervals quantify plausible effect size
- Sound decisions require both statistical and practical significance

In Part 3, you will learn how to choose sample size and power before launching a test.
