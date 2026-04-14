---
layout: post
title: "Borrower Segmentation"
subtitle: "The four archetypes that determine how your portfolio performs under stress"
tags: [consumer-lending, portfolio-management]
comments: true
math: true
series: "Consumer Lending Portfolio Management 101"
series_part: 2
---

A lending portfolio is not a single homogeneous pool of risk. It is a mixture of borrower types, each with different repayment behaviors, different responses to hardship, and different long-term value to the business. Treating them as identical is the first mistake a portfolio manager can make.

## Why Segmentation Matters

Consider two borrowers with the same credit score. One has a stable government salary, low debt-to-income ratio, and took the loan to renovate a kitchen. The other is a freelancer with volatile income, already carrying two other loans, and used the funds to cover a rent gap. Same score, very different risk profile and behavioral trajectory.

A homogeneous approval policy — same cutoff, same rate, same limit for everyone above a score threshold — embeds this blindness. Segmentation is the practice of uncovering structure that a single number does not capture. It informs pricing, limit-setting, collection strategy, and early intervention triggers.

## Four Behavioral Archetypes

Experienced portfolio managers recognize four recurring borrower types. Bureau signals can identify them at origination; behavioral signals confirm or update the classification in-life.

| Archetype | Bureau Signals | Behavioral Signals | Risk Profile |
| --- | --- | --- | --- |
| Responsible | Low DTI, clean history, established credit age | Pays early or on time, no contact | Low risk, low yield |
| Cash-flow-constrained | Irregular income, moderate utilization, some late marks | Occasional late payment, cures quickly with contact | Medium risk, needs monitoring |
| Rate-sensitive | Strong bureau, multiple open accounts, short tenure per lender | Full prepayment or churn if rates rise | Low credit risk, high attrition risk |
| Chronic defaulter | Thin file or derogatory history, high utilization, recent charge-offs | Misses first or second payment, unresponsive to contact | High risk, should not be approved |

**Responsible borrowers** are the backbone of a healthy portfolio. They generate steady interest income with minimal collection cost. The risk with this segment is mispricing — if your rate is uncompetitive, they will refinance elsewhere. Retention, not acquisition, is the management challenge.

**Cash-flow-constrained borrowers** are the most important segment to manage actively. They can and do repay — but their repayment is sensitive to timing. A collection call at the right moment converts a DPD 15 into a cure. Ignoring them converts a DPD 15 into a DPD 60. They represent a large share of a typical consumer portfolio and disproportionate collection revenue.

**Rate-sensitive borrowers** create a portfolio management paradox. They have excellent credit quality but low retention. Approving them improves your credit metrics but costs you yield — they prepay when rates drop and churn when alternatives appear. Understanding the share of rate-sensitive borrowers in your book matters for NIM forecasting.

**Chronic defaulters** should not be in the portfolio. If they appear in meaningful numbers, it indicates an underwriting failure or fraud. FPD rate (see Part 3) is the earliest signal.

## Loan Purpose and Default Behavior

The stated purpose of a loan influences the default probability and the shape of the default — not just whether a borrower defaults, but when and why.

| Loan Purpose | Default Profile | Notes |
| --- | --- | --- |
| Debt consolidation | Predictable, if misused becomes worse | Borrower takes loan to pay off other debt; works if behavior changes |
| Medical emergency | One-time shock, low moral hazard | Borrower generally wants to repay; income usually intact |
| Business working capital | Outcome-dependent | Default tied to business performance, not personal willingness |
| Lifestyle / consumption | Highest default risk | No asset purchase, no income improvement; pure consumption |

Medical emergency loans have an important characteristic: the moral hazard is low. The borrower did not choose to have a medical event, and they typically have stable employment. The cash-flow shock is one-time. Contrast this with lifestyle consumption loans, where the borrower is using credit to fund spending they cannot sustain — a fundamentally different risk profile.

Debt consolidation is deceptive. It looks safe (borrower is paying off higher-rate debt) but frequently fails because the underlying behavior that created the debt has not changed. A borrower who consolidates and then re-accumulates revolving debt is heading toward a worse position than before.

## Repeat Borrowers vs. First-Time Borrowers

This distinction matters more in consumer lending than in most other financial products because the information asymmetry between lender and borrower collapses dramatically after the first loan.

**First-time borrowers** present the full adverse selection problem. The lender has only bureau data and application data — both of which the borrower has some ability to game. Stated income cannot always be verified. Bureau scores reflect historical behavior under different conditions. Approval decisions are made under uncertainty.

**Repeat borrowers** have demonstrated behavior within your own system. You know their actual payment pattern, not just the bureau's summary of it. You know whether they cured delinquencies, whether they responded to contact, whether their income was consistent with stated amounts. This is significantly better information.

The risk-adjusted economics of repeat borrowers are almost always superior:

$$LTV_{repeat} = \sum_{k=1}^{K} \frac{RAM_k}{(1+d)^k}$$

Where $RAM_k$ is the risk-adjusted margin on the $k$-th loan and $d$ is the discount rate. As $k$ increases, $CoR_k$ typically decreases (behavioral risk is better understood) while retention cost is lower than acquisition cost. The repeat borrower is the highest-LTV customer in the portfolio.

The implication for strategy: acquisition economics must be evaluated not just on the first loan but on the expected loan sequence. A first-time borrower who is borderline-acceptable may become a strong long-term customer. The question is whether the first loan's economics justify the uncertainty.

## Payday Note

Payday lending compresses the segmentation problem to almost nothing. With a 30–45 day tenor, there is no in-life behavior to observe. The lender must make the entire risk decision — approval, amount, pricing — before disbursement, using only:

- Bureau data (where available; thin-file borrowers are common in payday)
- Application data (income, employment)
- Possibly alternative data (bank account transaction history)

The four behavioral archetypes still exist in a payday population, but the lender cannot observe them in-life. The responsible borrower and the chronic defaulter look identical at origination if their bureaus happen to be similar. Behavioral models — a powerful tool in installment lending — are simply not available.

This is one reason payday lenders operate at very high rates: not only are the borrowers higher-risk on average, but the lender has no opportunity to observe and adjust. All the risk is priced at the front door.

In Part 3, you will see how the loan lifecycle creates the observational opportunities that installment lending depends on — starting with the single most predictive event in the entire loan life: the first payment.
