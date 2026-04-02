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

A credit card is a revolving credit product — the bank grants the cardholder a credit limit, the cardholder spends within that limit, and repays on a monthly cycle. Unlike an installment loan where the repayment schedule is fixed upfront, a credit card is reusable: once you repay, the limit is restored and you can spend again.

Three mechanics define how the product works:

**Billing cycle** — typically 30 days. All transactions within the cycle appear on a single statement.

**Grace period** — the window between statement close and payment due date. In Vietnam, this is typically 15 days — e.g., statement closes on the 20th, payment due on the 5th of the following month. If the cardholder pays the full statement balance before the due date, no interest is charged.

**Interest accrual** — if the cardholder carries a balance past the due date, the bank charges interest on the average daily balance (ADB) at the Annual Percentage Rate (APR):

$$
\text{Monthly Interest} = \text{ADB} \times \frac{\text{APR}}{365} \times \text{Days in Cycle}
$$

The grace period is the issuer's strategic lever: customers who always pay in full never pay interest, while customers who carry a balance past the due date generate the bulk of interest revenue.

## The Four-Party Ecosystem

Every credit card transaction involves four key players:

| Party | Role |
| --- | --- |
| **Cardholder** | Spends against a credit limit; repays (or revolves) the balance |
| **Merchant** | Accepts card payment; pays a fee on each transaction |
| **Issuer** | The bank that underwrites and funds the credit; owns the customer relationship |
| **Acquirer** | The bank that serves the merchant; receives and settles card payments on the merchant's behalf |

Networks — Visa, Mastercard, JCB, Napas — are the infrastructure layer connecting issuers and acquirers. They set the rules, route transactions, and guarantee settlement, but they do not issue cards or hold customer credit risk.

Each transaction triggers a fee split across all four parties. When a cardholder pays 1,000,000 VND at a merchant, the money flows like this (using a typical ~2% MDR for Visa/Mastercard; domestic Napas transactions run lower at ~1.5%):

- Cardholder's account is debited 1,000,000 VND
- Merchant receives ~980,000 VND (after ~2% merchant discount rate)
- Issuer keeps ~15,000–18,000 VND (interchange fee)
- Network keeps ~1,000–2,000 VND (network assessment fee)
- Acquirer keeps ~2,000–4,000 VND (the remainder)

## Issuer Revenue Model

An issuer earns from four primary sources, ordered by typical impact:

**Interest income** — the dominant revenue source. Cardholders who carry a balance pay APR on the outstanding amount. In Vietnam, APRs typically range from 25–35% per year, making even modest revolving balances a significant yield driver.

$$
\text{Net Interest Income} = \text{Average Revolving Balance} \times (\text{APR} - \text{Cost of Funds})
$$

**Interchange income** — a percentage of each purchase, paid by the acquiring bank (and ultimately passed to the merchant). In Vietnam, interchange rates are capped and regulated, typically around 0.8–1.1% for domestic Napas transactions and 1.5–2% for international network (Visa/Mastercard) transactions. Premium cards generally carry higher interchange to fund their rewards programs.

**Fee income** — annual fees, late payment fees, over-limit fees, cash advance fees, foreign transaction fees.

**Other income** — co-brand partnership fees, balance transfer fees.

## Issuer Cost Structure

Running a card portfolio is expensive. The main cost categories, ordered by typical impact:

**Credit losses** — charged-off balances that are never recovered. This is typically the largest cost item for mass-market portfolios, ranging from 3–8% of outstanding balances depending on risk appetite.

**Cost of funds** — the bank borrows money (deposits, wholesale funding) to lend to cardholders. Cost of funds is the floor below which no card can be profitable.

**Rewards cost** — for rewards cards, the cost of points, miles, and cashback. Can reach 1–2% of spend, and must be fully covered by interchange income.

**Servicing cost** — call center, statements, disputes, technology, compliance. Costs vary significantly by bank scale and digital maturity.

**Acquisition cost** — marketing, underwriting, card production, and onboarding. Costs vary by channel; digital acquisition via app or partner tends to be significantly cheaper than traditional branch-based onboarding.

**Fraud losses** — unauthorized transactions absorbed by the issuer. Grows with transaction volume and card-not-present channels.

## The Two-Sided Risk Problem

Credit cards are unusual because the issuer faces two distinct and partially conflicting risks:

**Acquisition risk** — approving too few good customers means leaving profitable relationships on the table. Approving too many bad customers means absorbing credit losses.

**Credit risk** — a customer who looks good at application may deteriorate after booking. Income shocks, over-leverage, or behavioral shifts can turn a low-risk customer into a defaulter within months.

This creates a fundamental tension: the strategies that maximize approval rates tend to increase credit losses, and the strategies that minimize credit losses tend to suppress growth.

Managing this tension — across the full customer lifecycle, at the portfolio level — is what credit card portfolio management is about.

In Part 2, you will learn how to classify the customers already in your portfolio: who they are, how they behave, and what they are actually worth.
