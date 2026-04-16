---
layout: post
title: "The Lending Product: Economics & Structure"
subtitle: "How installment loans work, where the money comes from, and the two risks that shape every lending decision"
tags: [consumer-lending, portfolio-management]
comments: true
math: false
series: "Consumer Lending Portfolio Management 101"
series_part: 1
---

Before you can manage a lending portfolio, you need to understand the product itself — how an installment loan is structured, where revenue comes from, why the margin is thinner than it looks, and what structural risks sit underneath every lending decision. This part builds the economic foundation that every subsequent part will reference.

## How an Installment Loan Works

You lend a fixed amount — the **principal** — and the borrower repays it over a fixed number of months, called the **tenor**. Each month, they make the same fixed payment called **EMI** (Equated Monthly Installment). Part of it covers the **interest** on the outstanding balance; the rest reduces the principal. This is amortization.

One nuance worth knowing: lenders often quote a **flat rate** (interest on *the original principal* for the full tenor), but your true cost is **APR** (interest on *the remaining balance* each month, which shrinks as you repay). Because you're not using the full amount for the entire year, APR is always higher — a 12% flat rate on a 12-month loan works out to roughly 21–22% APR.

## Revenue Structure

So where does the money come from? An installment lender has three sources:

| Revenue Source | How It Accrues | Key Point |
| --- | --- | --- |
| Interest income | Monthly, on outstanding balance | Dominant source; declines as borrowers repay principal |
| Origination fee | At disbursement | Upfront cash; if deducted from principal, it inflates the effective APR |
| Penalty / late fee | On missed payments | A signal of portfolio stress — not a reliable revenue stream to plan around |

## Cost Structure

Revenue alone doesn't tell you whether the business makes money. Three costs eat into that revenue:

| Cost Component | Typical Range (% of portfolio) | What Drives It |
| --- | --- | --- |
| Cost of Funds (CoF) | 8–12% | Funding structure: deposits, bonds, warehouse lines |
| Operating Expense (OpEx) | 5–8% | Staff, technology, collections, compliance |
| Credit Loss (CoL) | 5–12% | Borrower default; the most volatile component |

## The P&L Waterfall

Stack those costs against the revenue and you get the P&L waterfall:

| Line Item | % of Portfolio |
| --- | --- |
| Gross Yield | 22–30% |
| − Cost of Funds | 8–12% |
| = Net Interest Margin (NIM) | 12–18% |
| − Operating Expense | 5–8% |
| − Credit Loss | 5–12% |
| = **Pre-tax Margin** | **2–8%** |

A 2–8% pre-tax margin is structurally thin for a high-risk, capital-intensive product. The core reason: revenue is entirely interest-driven, and it stops the moment a borrower repays. There is no recurring revenue, no transaction fee, no lock-in. The only way to sustain income is to keep originating new loans — which means continuous customer acquisition cost.

**Credit loss is the swing factor.** A portfolio at 5% NCO (net charge-off) can be marginally profitable. The same portfolio at 10% NCO is underwater. Credit risk management is not a support function in installment lending — it is the core operational competency.

## The Two Risks That Define the Business

Two structural risks sit underneath every lending decision:

**Adverse selection** happens before the loan is made. Borrowers who most urgently need credit are, on average, riskier than those who have alternatives. A lender that approves broadly and prices uniformly will attract a disproportionate share of high-risk borrowers. This is why underwriting exists: to identify and price risk before disbursement.

**Moral hazard** happens after the loan is made. Once funds are disbursed, the lender cannot take them back. A borrower under financial stress has an incentive to prioritize rent, food, and secured debts over an unsecured installment loan. The lender has limited recourse.

These two forces shape the entire architecture of the business: underwriting models respond to adverse selection; early intervention programs catch moral hazard in motion; collection operations recover value after it has played out.

In Part 2, you will see how borrower segmentation is the answer to adverse selection — identifying which applicants belong to which risk tier before the first payment is ever due.
