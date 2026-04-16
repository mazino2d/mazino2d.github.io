---
layout: post
title: "Portfolio Management Strategies"
subtitle: "Policy levers, vintage monitoring, concentration risk, and stress testing"
tags: [consumer-lending, portfolio-management]
comments: true
math: true
series: "Consumer Lending Portfolio Management 101"
series_part: 5
---

Measuring a portfolio is not the same as managing it. Part 4 gave you the instruments; this part describes how to use them. Portfolio management is fundamentally about making calibrated decisions under uncertainty — when to tighten credit policy, when to investigate an anomaly, how to distribute risk across channels and segments, and how to understand the portfolio's exposure to macroeconomic shocks.

## Credit Policy Levers

A portfolio manager has three primary dials to adjust the risk/return profile of new originations:

| Lever | What It Controls | Portfolio Effect |
| --- | --- | --- |
| Score cutoff | Who gets approved | Shifts credit quality distribution of incoming loans |
| Credit limit | How much each borrower receives | Affects exposure per account and loss-given-default |
| Pricing tier | What APR is charged | Affects yield, take-up rate, and segment composition |

These levers interact in non-trivial ways:

**Raising the cutoff** improves average credit quality but reduces volume and approval rate. If raised too sharply, it may cut into the cash-flow-constrained segment that was actually profitable — because their cure rates were high and their yield contribution significant.

**Reducing credit limits** lowers exposure per account and improves loss-given-default (LGD), but it may also reduce take-up rate if borrowers find the amount insufficient for their purpose. A lower average balance also dilutes fixed origination costs as a percentage of the loan.

**Tiered pricing** is the most surgical lever. Rather than a single rate for all approved borrowers, tiered pricing assigns different APRs based on risk score or segment. Risky borrowers pay more, subsidizing competitive rates for low-risk borrowers and improving take-up in that segment. The risk: if pricing is mis-calibrated, the high-rate tier attracts the most desperate borrowers (adverse selection within the approved population).

The key insight is that these levers should be adjusted together based on what the vintage data is telling you, not optimized in isolation.

## Vintage Monitoring: When to Act

Vintage monitoring (introduced in Part 4) is not just a diagnostic tool — it is the trigger mechanism for policy changes. The question is not just "what does the curve show?" but "what should I do about it?"

**Tighten policy when:**

- A new vintage's cumulative loss rate at MOB 3–6 is running materially above the historical band (e.g., 20%+ higher than same-MOB average of prior 4 vintages)
- FPD rate has risen for two consecutive origination months
- Multiple signals align: FPD up, DPD30 up on recent cohorts, take-up rate suspiciously high

**Investigate before acting when:**

- One vintage is an outlier but adjacent vintages are normal (suggests channel-specific issue, fraud cluster, or data quality problem — not a systemic underwriting failure)
- Loss curve inflects but other leading indicators (FPD) are stable

**Consider loosening when:**

- Three or more consecutive recent vintages are tracking below historical bands at MOB 6+
- Approval rate has been suppressed for 6+ months with no corresponding improvement in NCO
- Competitive intelligence suggests the market has moved and your cutoffs are overcorrected

**The key discipline:** Vintage monitoring creates accountability for policy decisions. If you tighten in Q1 and the Q2 vintage still runs elevated, the issue is not the cutoff — it is something else (fraud vector, channel partner, macro). If Q2 is clean, the tightening worked. The vintage is the ledger.

## Concentration Risk

A portfolio can be technically well-underwritten at the individual loan level and still carry systemic risk at the portfolio level through concentration.

**Channel concentration** is the most common trap. If 60% of originations come from a single partner channel (a fintech referral partner, an employer scheme, a single distribution app), that channel's problems become your portfolio's problems. A partner that changes its user acquisition strategy, gets acquired, or faces regulatory action can disrupt your origination flow overnight. Concentration should be measured and capped deliberately.

**Segment concentration** occurs when the portfolio is heavily weighted toward one borrower archetype or loan purpose. A portfolio that is 70% cash-flow-constrained borrowers is highly sensitive to unemployment shocks. A portfolio that is 60% business working capital loans is exposed to economic cycle volatility. Diversification across segments is a genuine risk management technique, not just good optics.

**Geographic concentration** creates macro shock exposure. A portfolio concentrated in one city or region will be disproportionately affected by local economic downturns, natural disasters, or regulatory changes targeting that geography.

**Measuring concentration:** The Herfindahl-Hirschman Index (HHI) is useful:

$$HHI = \sum_{i=1}^{n} s_i^2$$

Where $s_i$ is the share of the portfolio in segment $i$. HHI ranges from $1/n$ (perfectly equal distribution) to 1 (complete concentration in one segment). An HHI above 0.25 in any dimension (channel, segment, geography) typically warrants explicit monitoring and limit-setting.

## Restructuring and Rescheduling Policy

When a borrower signals distress — through a late payment, a partial payment, or a direct request — the lender faces a decision: escalate to collection, or offer a modification.

**Rescheduling** is a minor adjustment: changing the payment due date to align with the borrower's pay cycle. It does not change the total obligation. It is the lowest-cost intervention and has high acceptance rates.

**Restructuring** is a substantive modification: extending the tenor, reducing the interest rate, or reducing the outstanding balance (in severe cases). It acknowledges that the original loan terms are no longer serviceable for this borrower and negotiates a revised contract.

The economics of restructuring:

| Outcome | Revenue Impact | Loss Impact |
| --- | --- | --- |
| Restructuring accepted, borrower cures | Yield reduced; CoF extended | Avoids charge-off |
| Restructuring accepted, borrower re-defaults | Yield reduced; delayed charge-off | Charge-off at higher DPD |
| Restructuring declined, borrower self-cures | No impact | No impact |
| No intervention, borrower defaults | — | Full charge-off at original terms |

The expected value calculation depends on the probability of cure given restructuring versus cure without restructuring. For DPD 30–60 borrowers with a history of previous cure, restructuring is usually value-creating. For DPD 90+ borrowers who have not responded to contact, it rarely is.

**Policy questions to resolve:**

- At which DPD bucket should proactive restructuring offers be made?
- What is the maximum tenor extension allowed?
- How many times can a single loan be restructured?
- What documentation is required (income verification, hardship proof)?

The answers to these questions define a restructuring policy that can be consistently applied, monitored, and optimized over time.

## Stress Testing

A portfolio that looks healthy under current macroeconomic conditions may not survive a shock. Stress testing is the practice of estimating portfolio impact under adverse but plausible scenarios.

**The stress testing framework:**

1. **Define macro scenarios.** At minimum: base case, mild stress, severe stress. Variables: unemployment rate, GDP growth, inflation, interest rates.

2. **Map macro variables to portfolio inputs.** Historical regression or expert judgment: e.g., a 2% rise in unemployment historically correlates with a 1.5% increase in DPD30 rate on this portfolio.

3. **Re-run portfolio metrics under each scenario.**

    | Scenario | Unemployment | NCO Rate | RAM |
    | --- | --- | --- | --- |
    | Base | 4% | 6% | 4.2% |
    | Mild stress | 6% | 9% | 1.8% |
    | Severe stress | 9% | 14% | −1.2% |

4. **Identify the breaking point.** At what scenario does RAM turn negative? At what scenario does the portfolio breach regulatory capital requirements?

5. **Set policy buffers accordingly.** If severe stress is within a plausible range given macroeconomic conditions, consider raising credit standards proactively rather than reactively.

Stress testing is not prediction — it is preparing the organization to understand consequences before events occur.

In Part 6, you will see how the risk models that underlie all of these decisions are built, monitored, and connected back to portfolio outcomes — closing the loop from data to model to policy to measurement.
