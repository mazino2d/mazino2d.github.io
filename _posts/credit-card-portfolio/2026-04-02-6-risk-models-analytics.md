---
layout: post
title: "Risk Models & Analytics"
subtitle: "Scoring, vintage analysis, roll rates, and CLTV — the quantitative foundation of portfolio management"
tags: [credit-card, portfolio-management]
comments: true
math: true
series: "Credit Card Portfolio Management 101"
series_part: 6
---

The strategies in Part 5 work because they are backed by models. Scoring tells you who to approve and at what terms. Vintage analysis tells you whether your approvals were good decisions. Roll rate analysis tells you where the portfolio is heading. CLTV tells you what a customer relationship is actually worth. This part covers the analytical infrastructure that makes portfolio management rigorous.

## Application Scoring vs Behavioral Scoring

### Application Scoring

Applied at origination. Uses bureau data, application attributes, and (where available) internal bank data to produce a probability of default estimate.

$$
P(\text{Default}) = f(\text{bureau score, income, DTI, derogatory history, ...})
$$

The output — a scorecard or model score — drives the approve/decline decision and APR assignment. Key properties:

- Built on historical applicant performance data
- Validated on out-of-time samples to prevent overfitting
- Must be monitored for population shift (the scorecard was built on customers from 2 years ago; today's applicants may be different)

### Behavioral Scoring

Applied to existing accounts on a rolling basis (monthly or more frequently). Uses internal transaction data — payment behavior, utilization trends, spend patterns, bureau refreshes — to produce an updated risk estimate for each account.

Behavioral scores are more predictive than application scores for existing accounts because they incorporate actual payment behavior. A customer with a mediocre application score who has paid on time for 24 months is a very different risk than their score at origination implied.

Use cases:

- Trigger for CLIs or CLDs
- Early risk intervention targeting
- Collections prioritization
- Retention offer eligibility

## Vintage Analysis

A vintage is a cohort of accounts originated in the same time period (typically the same month). Tracking each vintage's performance separately — rather than mixing all accounts together — isolates the effect of origination conditions and policy changes.

**Vintage loss curve** plots cumulative net charge-off rate (vertical axis) against months on book (horizontal axis) for each origination month.

Key properties:

- Loss curves are typically "S-shaped": low losses early (accounts too new to default), rising sharply at 12–24 months of age, then flattening as the remaining population stabilizes
- Comparing vintages at the same age reveals quality differences: a vintage that reaches 4% cumulative loss at month 12 vs. prior vintages at 2.5% is a clear deterioration signal
- Policy changes leave a visible signature: if underwriting was loosened in March, the March vintage will show a steeper curve than February and January

Vintage analysis answers: "Were the accounts we booked in that period good decisions?"

## Roll Rate Analysis

Roll rate analysis tracks the flow of accounts between delinquency states over time. It is the most sensitive real-time signal of portfolio deterioration.

Define states: Current (C), 1–29 DPD, 30–59 DPD, 60–89 DPD, 90–119 DPD, 120+ DPD, Charged-Off (CO), Cured.

$$
\text{Roll Rate}_{i \to j} = \frac{N_{j,\ t+1} \text{ that were in state } i \text{ at time } t}{N_{i,\ t}}
$$

A roll rate matrix, observed monthly, produces a transition probability matrix. When roll rates are stable, the matrix can be used to project future delinquency levels and loss estimates.

When roll rates spike — particularly the 30→60 and 60→90 transitions — it signals that current delinquent accounts are not curing and are progressing toward charge-off. A 5-point increase in the 30→60 roll rate translates directly into higher NCO rates 3–4 months forward.

Roll rate analysis also powers loss reserve calculations (CECL in the US requires forward-looking loss estimates).

## Customer Lifetime Value Modeling

CLTV estimates the present value of net cash flows expected over the life of a customer relationship.

$$
\text{CLTV} = \sum_{t=1}^{T} \frac{[\text{Revenue}_t - \text{Expected Loss}_t - \text{Variable Cost}_t] \times P(\text{Active}_t)}{(1+r)^t}
$$

Where:

- $T$ = expected relationship tenure
- $P(\text{Active}_t)$ = probability the customer remains active at time $t$ (accounts for attrition and default)
- $r$ = discount rate (hurdle rate or WACC)

CLTV is used to:

- Set maximum acquisition cost per segment (CAC < CLTV)
- Size retention investment (worth spending up to the NPV of at-risk future cash flows)
- Prioritize CLI decisions (higher-CLTV accounts justify larger credit line investments)
- Compare profitability across products and channels

Building a robust CLTV model requires assumptions about tenure distributions, revenue trajectories, loss rates by behavioral state, and discount rates. Even a simplified model — with conservative assumptions — substantially improves decision quality over flat per-account heuristics.

## Stress Testing & Scenario Planning

Stress testing asks: how does portfolio performance change under adverse macro conditions?

**Top-down approach**: Apply macroeconomic sensitivities derived from historical regressions. For example: for every 1-point rise in unemployment, roll rates increase by X basis points and charge-off rates rise by Y.

**Bottom-up approach**: Apply behavioral assumptions at the account level (probability of segment migration under stress) and aggregate up.

A well-structured stress test produces:

- A "base case" projection (current trajectory)
- A "moderate stress" scenario (recession-like conditions)
- A "severe stress" scenario (deep recession, e.g., GFC or COVID shock)

Each scenario outputs projected NCO rate, revenue compression, and capital consumption over a 12–24 month horizon.

Stress test outputs inform:

- Loss reserves (ALLL/CECL)
- Capital adequacy planning (regulatory and internal)
- Underwriting tightening decisions ("if this scenario materializes, do we have enough capital to absorb it?")

---

The analytical models in this part — scoring, vintage analysis, roll rates, CLTV, stress testing — are the connective tissue between the raw data a portfolio generates and the decisions a portfolio manager needs to make.

Together, the six parts of this series give you a complete framework for credit card portfolio management: from the economics of the product, through customer segmentation and lifecycle dynamics, to the metrics and strategies that drive outcomes, and the analytical models that make it rigorous.
