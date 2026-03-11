---
layout: post
title: "A/B Testing Series (Part 1): Foundations"
subtitle: "Core concepts: hypotheses, conversion rates, and random variation"
tags: [ab-testing, experimentation, statistics]
comments: true
series: "A/B Testing From Zero to Decision"
series_part: 1
---

A/B testing is a disciplined way to make product decisions using evidence instead of intuition.

In this first lesson, you will build the mental model needed for every experiment that follows.

## What Is an A/B Test?

An A/B test compares two variants:

- Variant A: current experience (control)
- Variant B: new experience (treatment)
- Outcome metric: the behavior you care about (for example, conversion rate)

The objective is simple: estimate whether the observed difference is likely a real effect or just noise.

## Why Random Assignment Matters

Randomization is the protection layer of experimentation.

- It balances observed and unobserved user characteristics across groups
- It reduces systematic bias
- It allows valid statistical inference

Without random assignment, you can still compare metrics, but you cannot claim a causal effect confidently.

## Null and Alternative Hypotheses

Before running any test, define your hypotheses:

$$
H_0: p_A = p_B
$$

$$
H_1: p_A \neq p_B
$$

Where $p_A$ and $p_B$ are true conversion probabilities for control and treatment.

This framing prevents post-hoc storytelling and keeps analysis honest.

## Conversion Rate Basics

For binary outcomes, conversion rate is:

$$
\text{Conversion Rate} = \frac{\text{Conversions}}{\text{Visitors}}
$$

Example:

- Control: 147 conversions out of 2450 visitors = $6.00\%$
- Variant: 167 conversions out of 2380 visitors = $7.02\%$
- Absolute lift: $1.02$ percentage points
- Relative lift: $\frac{7.02 - 6.00}{6.00} \approx 17\%$

Both absolute and relative lift are useful. Report both.

## Random Variation Is Normal

Even if two groups have identical true conversion rates, observed rates will differ due to sampling noise.

This is why:

- Small differences are expected
- Single-run outcomes can be misleading
- Statistical testing is required before decisions

## Practical Checklist Before You Launch

- Define the primary metric and guardrail metrics
- Specify $H_0$, $H_1$, and significance level $\alpha$
- Ensure randomization is implemented correctly
- Confirm event tracking quality
- Decide sample size and stopping rule in advance

## Key Takeaways

- A/B testing is causal inference under random assignment
- Hypotheses and predefined rules protect decision quality
- Random variation makes raw differences insufficient on their own

In Part 2, you will learn how p-values and confidence intervals turn noisy observations into defensible decisions.
