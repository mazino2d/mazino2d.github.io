---
layout: post
title: "Customer Segmentation: Who's in Your Portfolio?"
subtitle: "Transactors, revolvers, hibernators, and defaulters — the four archetypes that shape portfolio economics"
tags: [credit-card, portfolio-management]
comments: true
math: true
series: "Credit Card Portfolio Management 101"
series_part: 2
---

Not all cardholders behave the same way. A portfolio that looks healthy in aggregate can contain a very different mix underneath. Understanding that mix — and how it shifts — is the foundation of effective portfolio management.

## The Four Behavioral Archetypes

### Transactor

A transactor pays the full statement balance every cycle. They never carry revolving debt.

- Generate interchange income on every purchase
- Generate zero interest income
- Generally low credit risk
- High-engagement customers, often with premium cards

Transactors are profitable through spend volume and interchange, but margin per dollar is thin. Issuers subsidize their rewards programs hoping transactors will occasionally revolve — or refer others who do.

### Revolver

A revolver carries a balance month-to-month, paying only minimum or partial payments.

- Generate substantial interest income (APR × ADB)
- Generate interchange on purchases
- Higher credit risk than transactors
- The primary profit engine of most mass-market portfolios

The revolver segment is heterogeneous. A stable revolver with a manageable balance and consistent payments is highly profitable. A stress-revolving customer who just lost their job is a loss event waiting to happen.

### Hibernator (Dormant)

A hibernator holds an open account but makes little to no use of it — no or near-zero spend over an extended period (typically 3–6+ months).

- Generate no interchange
- Generate no interest income
- Consume servicing cost
- Represent an unactivated or lapsed relationship

Hibernators are a drag on the portfolio. They occupy credit exposure (committed but undrawn limit) and generate costs. The management question is whether to reactivate them or close the accounts.

### Defaulter

A defaulter has stopped making payments and is trending toward charge-off.

- Generate no current income
- Are generating active losses (missed interest accruals, collection costs)
- Will ultimately result in a write-off if not cured

Some defaulters cure — they resume payments after a period of delinquency. Many do not. The goal is to identify this segment early and intervene before the loss is realized.

## How to Identify Each Segment

Segmentation is based on behavioral signals from account data:

| Signal | Transactor | Revolver | Hibernator | Defaulter |
| -------- | ----------- | --------- | ----------- | ---------- |
| Payment ratio (payment / statement balance) | ≥ 100% | < 100% | N/A | 0% or missing |
| Utilization rate | Low–Moderate | Moderate–High | Near 0% | Often high before default |
| Days past due | 0 | 0 | 0 | 30+ DPD |
| Spend activity | Regular | Regular | Absent or rare | Declining |

**Payment ratio** is the most reliable single signal: a customer paying 100%+ of their statement balance is a transactor by definition.

## Unit Economics per Segment

$$
\text{Profit per Account} = \text{Interest Income} + \text{Interchange Income} + \text{Fee Income} - \text{Credit Losses} - \text{Fraud Losses} - \text{Rewards Cost} - \text{Servicing Cost}
$$

In practice, unit economics by segment look roughly like:

| Segment | Interest Income | Interchange | Credit Loss | Net Margin |
| --------- | --------------- | ----------- | ----------- | ---------- |
| Transactor | Low | High | Very Low | Moderate |
| Revolver | High | Moderate | Moderate | High (if stable) |
| Hibernator | None | None | Low | Negative |
| Defaulter | None | None | Very High | Severely Negative |

The revolver-transactor split in your portfolio is one of the most important strategic parameters. A portfolio skewed too heavily toward transactors is margin-thin. A portfolio skewed too heavily toward revolvers carries elevated loss risk.

## Segment Migration

Customers move between segments over time. Common migration paths:

- **Transactor → Revolver**: income shock, increased spending, holiday season
- **Revolver → Defaulter**: over-leverage, job loss, medical expense
- **Transactor → Hibernator**: competitive offer, changed spending behavior
- **Defaulter → Revolver (cure)**: resolved hardship, payment plan

Migration matrices (also called flow-state matrices) track what percentage of each segment transitions to another segment month-over-month. A rising rate of Revolver → Defaulter migration is an early warning signal that the portfolio is deteriorating.

## Portfolio Composition Health

There is no universally "correct" mix — it depends on the bank's risk appetite, funding cost, and product strategy. But some benchmarks apply:

- A healthy mass-market portfolio typically has 40–60% revolvers by balance
- Dormancy rate above 20% of accounts is a utilization problem
- Charge-off rate above 6–8% annualized on a mature portfolio signals credit quality issues

Tracking segment composition over time, by vintage and product, tells you whether your portfolio is moving in the right direction — before the P&L tells you it isn't.

In Part 3, you will see how these segments map onto the credit card lifecycle, and what management actions are available at each stage.
