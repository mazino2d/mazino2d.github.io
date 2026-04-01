---
layout: post
title: "The Credit Card Product: Economics & Ecosystem"
subtitle: "How credit cards work, who profits, and why the risk is two-sided"
tags: [credit-card, portfolio-management]
comments: true
math: true
series: "Credit Card Portfolio Management 101"
series_part: 1
---

Before you can manage a credit card portfolio, you need to understand what you are actually managing: a financial product that sits at the intersection of consumer credit, payment infrastructure, and multi-party economics.

## How a Credit Card Works

A credit card is a revolving credit facility. The bank extends a credit limit, the cardholder spends against it, and the balance is billed monthly.

Three mechanics drive the economics:

**Billing cycle** — typically 30 days. All transactions within the cycle appear on a single statement.

**Grace period** — the window between statement close and payment due date, usually 21–25 days. If the cardholder pays the full statement balance before the due date, no interest is charged.

**Interest accrual** — if the cardholder carries a balance past the due date, the bank charges interest on the average daily balance (ADB) at the Annual Percentage Rate (APR):

$$
\text{Monthly Interest} = \text{ADB} \times \frac{\text{APR}}{365} \times \text{Days in Cycle}
$$

The grace period is the issuer's strategic lever: it keeps transactors happy (they never pay interest) while generating substantial revenue from revolvers who carry balances.

## The Four-Party Ecosystem

Every credit card transaction passes through four parties:

| Party | Role |
| --- | --- |
| **Cardholder** | Spends against a credit limit; repays (or revolves) the balance |
| **Issuer** | The bank that underwrites and funds the credit; owns the customer relationship |
| **Network** | Visa, Mastercard, Amex — sets rules, routes transactions, guarantees settlement |
| **Merchant** | Accepts payment; pays a fee on each transaction |

The money flow on a $100 purchase looks roughly like this:

- Merchant receives ~$97.50 (after a ~2.5% merchant discount rate)
- Issuer keeps ~$2.00 (interchange)
- Network keeps ~$0.10–$0.15 (network assessment fee)
- Acquirer keeps the remainder

Amex and Discover operate as both issuer and network ("closed loop"), capturing both sides.

## Issuer Revenue Model

An issuer earns from four primary sources:

**Interchange income** — a percentage of each purchase, paid by the acquiring bank (and ultimately passed to the merchant). Interchange rates vary by card tier, merchant category, and network. Premium rewards cards carry higher interchange (~2–3%) to fund their rewards programs.

**Interest income** — the dominant revenue source. Revolvers pay APR on their carried balance. With average APRs in the 20–28% range, even modest revolving balances generate significant yield.

$$
\text{Net Interest Income} = \text{Average Revolving Balance} \times (\text{APR} - \text{Cost of Funds})
$$

**Fee income** — annual fees, late payment fees, over-limit fees, cash advance fees, foreign transaction fees.

**Other income** — co-brand partnership fees, balance transfer fees.

## Issuer Cost Structure

Running a card portfolio is expensive. The main cost categories:

**Cost of funds** — the bank borrows money (deposits, wholesale funding) to lend to cardholders. Cost of funds is the floor below which no card can be profitable.

**Credit losses** — charged-off balances that are never recovered. This is typically the largest cost item for mass-market portfolios, ranging from 3–8% of outstanding balances depending on risk appetite.

**Fraud losses** — unauthorized transactions absorbed by the issuer. Grows with transaction volume and card-not-present channels.

**Servicing cost** — call center, statements, disputes, technology, compliance. Often $80–$150 per account per year.

**Rewards cost** — for rewards cards, the cost of points, miles, and cashback. Can reach 1–2% of spend, and must be fully covered by interchange income.

**Acquisition cost** — marketing, underwriting, card production, and onboarding. Typically $50–$200 per new account.

## The Two-Sided Risk Problem

Credit cards are unusual because the issuer faces two distinct and partially conflicting risks:

**Acquisition risk** — approving too few good customers means leaving profitable relationships on the table. Approving too many bad customers means absorbing credit losses.

**Credit risk** — a customer who looks good at application may deteriorate after booking. Income shocks, over-leverage, or behavioral shifts can turn a transactor into a defaulter within months.

This creates a fundamental tension: the strategies that maximize approval rates tend to increase credit losses, and the strategies that minimize credit losses tend to suppress growth.

Managing this tension — across the full customer lifecycle, at the portfolio level — is what credit card portfolio management is about.

In Part 2, you will learn how to classify the customers already in your portfolio: who they are, how they behave, and what they are actually worth.
