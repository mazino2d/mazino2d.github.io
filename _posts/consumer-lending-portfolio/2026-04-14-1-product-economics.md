---
layout: post
title: "The Lending Product: Economics & Structure"
subtitle: "Installment loan anatomy, revenue model, cost structure, and why this is a thin-margin business"
tags: [consumer-lending, portfolio-management]
comments: true
math: true
series: "Consumer Lending Portfolio Management 101"
series_part: 1
---

Before you can manage a lending portfolio, you need to understand the product itself — how money moves, where revenue comes from, what it costs to run, and why the margin is thinner than it looks. This part builds the economic foundation that every subsequent part will reference.

## Anatomy of an Installment Loan

An installment loan has four defining parameters:

- **Principal (P):** The amount disbursed to the borrower.
- **Tenor (n):** The number of payment periods (typically months).
- **Interest rate (r):** The periodic rate applied to the outstanding balance.
- **EMI (Equated Monthly Installment):** The fixed payment amount per period.

The EMI formula for a fully amortizing loan is:

$$EMI = P \cdot \frac{r(1+r)^n}{(1+r)^n - 1}$$

Each EMI contains two components: an interest portion (declining over time as the balance decreases) and a principal repayment portion (increasing over time). This is the amortization schedule — a deterministic repayment plan baked in at origination. It is what makes installment lending analytically tractable.

**APR vs. flat rate.** Lenders often quote a flat rate — interest calculated on the original principal for the full tenor. A 12% flat rate on a 12-month loan sounds reasonable, but because the borrower is repaying principal each month, the effective annual rate (APR) is roughly double — closer to 21–22%. Regulators and sophisticated borrowers care about APR; portfolio managers must track both to understand unit economics accurately.

## Revenue Model

An installment lender has three sources of revenue:

| Revenue Source | Timing | Notes |
| --- | --- | --- |
| Interest income | Accrues monthly over tenor | Dominant source; tied to outstanding balance |
| Origination fee | Recognized at disbursement | Upfront cash; may be deducted from principal |
| Penalty / late fee | Triggered by missed payments | Signal of distress, not a reliable revenue stream |

**Interest income** is the engine. For a portfolio with average outstanding balance of $B$ and yield $y$, monthly interest income ≈ $B \times y / 12$. The yield is not the stated rate — it includes fee income amortized over the loan life, adjusted for prepayments and defaults.

**Origination fees** create an interesting tension. They improve short-term P&L but do not reduce the borrower's debt burden — the principal is the same. In many markets, fees are deducted upfront ("fee-in-advance"), meaning the borrower receives less than the stated principal. This inflates the effective APR.

**Penalty fees** should never be modeled as a steady revenue stream. Chronic late fees signal a deteriorating portfolio. If penalty fee income is growing as a share of total revenue, that is a warning sign, not a success.

## Cost Structure

Running an installment lending business has three cost buckets:

| Cost Component | Typical Range (% of portfolio) | What Drives It |
| --- | --- | --- |
| Cost of Funds (CoF) | 8–12% | Funding structure: deposits, bonds, warehouse lines |
| Operating Expense (OpEx) | 5–8% | Staff, technology, collections, compliance |
| Credit Loss (CoL) | 5–12% | Borrower default; the most volatile component |

The resulting economics look like this for a typical consumer lender:

| Line Item | % of Portfolio |
| --- | --- |
| Gross Yield | 22–30% |
| − Cost of Funds | 8–12% |
| = Net Interest Margin (NIM) | 12–18% |
| − Operating Expense | 5–8% |
| − Credit Loss | 5–12% |
| = **Pre-tax Margin** | **2–8%** |

## Why the Margin Is Thin

A 2–8% pre-tax margin on a high-risk, capital-intensive product is structurally thin. To understand why, compare installment lending to credit cards:

Credit card issuers earn interchange income (1–2% of every transaction) and benefit from revolving behavior — a borrower who carries a balance indefinitely generates interest income indefinitely. The product is sticky by design.

Installment lenders have none of this. Revenue is entirely interest-driven. The loan has a fixed end date. Once a borrower repays, revenue stops. The only way to sustain income is to originate new loans — which requires continuous customer acquisition cost.

**Credit loss is the swing factor.** A portfolio running at 5% NCO (net charge-off) can be marginally profitable. The same portfolio at 10% NCO is underwater. This is why credit risk management is not a support function in installment lending — it is the core operational competency.

## Payday Lending: The Degenerate Case

Payday loans are installment loans with $n = 1$: a single lump-sum repayment at the end of a 14–45 day term. There is no amortization schedule because there is only one payment.

Fee structures are typically flat: borrow $100, repay $115–$120. When annualized, this implies an APR of 200–400%. Regulators find this alarming; lenders argue that the dollar cost of credit is low and the product serves a genuine short-term need.

From a portfolio management perspective, payday has structural differences that affect almost every concept in this series:

- No in-life monitoring (the loan resolves before you can observe behavior)
- No restructuring or rescheduling options
- Rollover policy (re-lending to borrowers who cannot repay) is the primary lever
- All risk decisions concentrate at origination

Throughout this series, payday will appear as a footnote wherever its behavior diverges meaningfully from installment. The contrast often clarifies why installment lending is designed the way it is.

## Adverse Selection & Moral Hazard

Two fundamental risks define unsecured consumer lending:

**Adverse selection** occurs before the loan is made. Borrowers who most urgently want credit are, on average, riskier than those who have alternatives. A lender that prices uniformly and approves broadly will attract a disproportionate share of high-risk borrowers — the "lemons problem" in credit markets. This is why underwriting exists: to identify and price for risk before disbursement.

**Moral hazard** occurs after the loan is made. Once funds are disbursed, the borrower's incentive changes. The lender can no longer withdraw the money — they can only pursue repayment. A borrower facing financial stress now has an incentive to prioritize other obligations (rent, food, secured debts) over an unsecured installment loan. The lender has limited recourse.

Together, these two forces explain the entire architecture of consumer lending: underwriting models (combat adverse selection), collateral requirements (reduce moral hazard), early intervention programs (respond to moral hazard in motion), and collection operations (recover value after moral hazard has played out).

In Part 2, you will see how borrower segmentation operationalizes the response to adverse selection — identifying which applicants belong to which risk tier before the first payment is ever due.
