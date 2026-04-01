---
layout: post
title: "Portfolio Metrics: What to Measure at Every Stage"
subtitle: "The KPI framework for managing a credit card book from acquisition to charge-off"
tags: [credit-card, portfolio-management]
comments: true
math: true
series: "Credit Card Portfolio Management 101"
series_part: 4
---

A credit card portfolio generates enormous amounts of data. The challenge is not measuring everything — it is knowing which metrics matter, when they matter, and what they tell you. This part builds the complete measurement framework across the lifecycle.

## Acquisition Metrics

**Approval rate** — the percentage of applications that result in an approved account.

$$
\text{Approval Rate} = \frac{\text{Approved Applications}}{\text{Total Applications}}
$$

Approval rate is a policy output, not a target. Moving it requires changing underwriting criteria with direct consequences for future credit quality.

**Booking rate** — the percentage of approvals that result in an activated, funded account. Applicants sometimes abandon after approval.

**Yield-on-book** — the weighted average APR of newly booked accounts. A leading indicator of future interest income potential.

**New user vs repeated user split** — a critical segmentation at the application level:

- **New user**: an applicant who has never held a credit card from any issuer. Thin-file or no-file on the bureau. Higher uncertainty on credit behavior; requires more conservative underwriting or alternative data.
- **Repeated user**: an applicant with prior card history — either from this issuer or from others. Observable credit behavior allows more precise risk assessment.

The new/repeated mix affects average approval rates, average APRs, and the shape of the loss curve. A portfolio growing predominantly through new users will see higher early-vintage losses; repeated users typically have more predictable default patterns.

## Activation & Usage Metrics

**Activation rate** — percentage of booked accounts that make at least one purchase within the defined activation window (typically 30, 60, or 90 days).

**Active rate** — percentage of open accounts with at least one transaction in the trailing 30 days. A portfolio-level health indicator.

**Purchase volume** — total spend across the portfolio per period. Drives interchange income.

**Spend per active account** — average spend among accounts that made at least one transaction. Separates engagement quality from activation quantity.

**Utilization rate** — balance as a percentage of credit limit.

$$
\text{Utilization Rate} = \frac{\text{Outstanding Balance}}{\text{Credit Limit}}
$$

At the portfolio level, average utilization indicates how much of the committed credit exposure is drawn. Rising utilization can signal increased revenue OR increased credit stress — context determines the interpretation.

## Revenue Metrics

**Net Interest Margin (NIM)** — the spread between yield earned on balances and cost of funds.

$$
\text{NIM} = \text{Yield on Receivables} - \text{Cost of Funds}
$$

**Revenue per active account** — total net revenue (interest + interchange + fees − fraud losses − rewards cost) divided by active account count. The cleanest per-unit revenue measure.

**Interchange income rate** — interchange dollars as a percentage of purchase volume. Tracks the effective interchange yield of the portfolio.

## Credit Quality Metrics

**Delinquency rate** — percentage of accounts or balances in each DPD bucket at a point in time.

$$
\text{Delinquency Rate (30+ DPD)} = \frac{\text{Balances 30+ Days Past Due}}{\text{Total Balances}}
$$

Track both account-based and balance-based delinquency — a small number of high-balance accounts can skew the balance view.

**Roll rate** — percentage of accounts in delinquency bucket X that move to bucket X+1 in the next period.

$$
\text{Roll Rate}_{30 \to 60} = \frac{\text{Accounts that were 30 DPD last month and are now 60 DPD}}{\text{Accounts that were 30 DPD last month}}
$$

Roll rates are the most sensitive early warning metric for credit deterioration.

**Net charge-off (NCO) rate** — annualized net write-offs as a percentage of average outstanding balances.

$$
\text{NCO Rate} = \frac{\text{Gross Charge-offs} - \text{Recoveries}}{\text{Average Receivables}} \times \frac{12}{\text{Months}}
$$

**Delinquency rate by cohort (vintage analysis)** — instead of tracking delinquency at a point in time across the entire portfolio, cohort analysis tracks accounts by their origination month and measures their cumulative bad rate at each month of age.

This is critical for detecting policy change impact. If underwriting was loosened in January, a cross-sectional delinquency rate may not show the problem for 6–12 months — but a vintage view will show the January cohort's bad rate diverging from prior cohorts at 3–6 months of age. Early identification, before losses materialize at scale.

## Efficiency Metrics

**Cost per account** — total operating cost (servicing, technology, compliance, collections) divided by open accounts.

**Collections recovery rate** — dollars recovered as a percentage of delinquent or charged-off balances worked. Measures collections effectiveness.

**Collections cost per dollar recovered** — unit economics of the collections function.

## Profitability Metrics

**Return on assets (ROA)** — net income as a percentage of average receivables. The primary portfolio-level profitability measure in card management.

$$
\text{ROA} = \frac{\text{Net Income}}{\text{Average Receivables}}
$$

Industry benchmarks: top-quartile portfolios achieve 3–5% ROA; mass-market portfolios typically target 2–3%.

**Economic profit** — profit after deducting the cost of equity capital allocated to the portfolio. An account with positive accounting profit but negative economic profit is destroying shareholder value.

**Customer lifetime value (LTV)** — present value of all future net cash flows from a customer relationship.

$$
\text{LTV} = \sum_{t=1}^{T} \frac{\text{Net Revenue}_t - \text{Expected Loss}_t - \text{Servicing Cost}_t}{(1 + r)^t}
$$

LTV is the theoretically correct basis for acquisition spend, credit limit decisions, and retention investments. In practice it requires assumptions about tenure and behavior migration, but even simplified versions improve decision quality.

## The Portfolio Dashboard

A well-run portfolio is monitored through a tiered dashboard:

- **Weekly** — early warning signals: roll rates, DPD buckets, fraud spike, approval rate
- **Monthly** — full P&L drivers: NIM, NCO rate, active rate, spend per account, vintage delinquency
- **Quarterly** — strategic view: ROA, LTV by segment, cohort performance vs prior vintages, competitive benchmarks

No single metric tells the whole story. The combination — revenue, utilization, delinquency, and profitability together — gives the full picture of portfolio health.

In Part 5, you will see how these metrics translate into actionable management strategies across the lifecycle.
