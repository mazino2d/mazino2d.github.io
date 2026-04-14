---
layout: post
title: "Loan Lifecycle & Account Management"
subtitle: "From origination to charge-off — and why the first payment is the strongest signal you have"
tags: [consumer-lending, portfolio-management]
comments: true
math: true
series: "Consumer Lending Portfolio Management 101"
series_part: 3
---

Every installment loan traces the same arc: it is originated, disbursed, repaid (or not), and eventually closed — either through full repayment or through the accounting event called charge-off. Understanding this lifecycle is not just theoretical. Each stage generates different risk signals and calls for different management responses.

## The Lifecycle Stages

```plain
Origination → Disbursement → Repayment (in-life) → Close / Default → Recovery → Charge-off
```

**Origination** is the underwriting and approval decision. The borrower applies; the lender scores, prices, and decides whether to offer credit and at what terms. All the tools from Part 2 (segmentation, scoring) operate here.

**Disbursement** is when funds are transferred to the borrower. This is the point of no return — once the money is out the door, the lender can only collect, not withdraw. Disbursement rate (the share of approved-and-accepted borrowers who receive funds) is a pipeline metric, not a credit metric, but it affects portfolio composition.

**Repayment** is the in-life stage. The borrower makes (or misses) payments over the loan tenor. This is where the majority of account management activity occurs — monitoring, behavioral triggers, early intervention, and restructuring offers.

**Close / Default** is the terminal event. A performing loan closes when the final EMI is received. A defaulting loan transitions into recovery when the borrower stops paying for long enough to trigger charge-off.

**Recovery** is the post-default stage. The lender pursues collection through its own operations or sells the debt to a third-party collector. Recovery rates vary significantly by vintage quality and time elapsed since default.

**Charge-off** is an accounting event, not a credit event. The loan balance is removed from the books as an unrecoverable asset. In most markets this occurs at DPD 90–180, depending on regulatory requirements. Charge-off does not stop recovery activity — collections on charged-off accounts can continue.

## First Payment Default: The Strongest Signal

First Payment Default (FPD) occurs when a borrower misses the very first scheduled EMI. It is the most informative single event in the entire loan lifecycle.

Why is it so predictive? Three reasons:

1. **Fraud.** Some borrowers never intended to repay. They provided falsified documents to obtain disbursement. Missing payment #1 is the first moment the fraud becomes observable.

2. **Stated-income inflation.** A borrower overstated their income to qualify. The approved EMI is above what they can actually service. They learn this when the first due date arrives.

3. **Behavioral intent.** Some borrowers, facing multiple obligations, make deliberate triage decisions. A lender they are willing to prioritize below others will experience FPD.

FPD rate is typically calculated as:

$$FPD\ Rate = \frac{\text{Loans with first payment missed}}{\text{Total originated loans}}$$

A healthy consumer installment portfolio runs FPD rates of 1–4%. Above 5% indicates an underwriting problem, a fraud exposure, or both. FPD loans almost never recover — their eventual charge-off rate is 80–95%.

**The month in which FPD is observed also matters.** A loan originated in January that misses its February payment is a January vintage FPD. Tracking FPD by vintage (origination cohort) is the earliest available signal of vintage quality. You know in month 2 whether something went wrong at origination in month 1.

## In-Life Monitoring

Between origination and resolution, the lender has continuous visibility into borrower behavior at each Month-on-Book (MOB). Payment behavior is tracked at every cycle:

| Payment Status | Definition | Action Trigger |
| --- | --- | --- |
| Prepaid / Early | Paid before due date | Monitor for rate-sensitive behavior |
| On-time | Paid within grace period | No action; baseline |
| Grace period | Paid 1–5 DPD | Soft reminder if pattern persists |
| Early delinquency | DPD 6–29 | Outbound call; assess cure probability |
| Late delinquency | DPD 30–59 | Intensified contact; restructuring assessment |
| Deep delinquency | DPD 60–89 | Legal demand; last-resort intervention |
| Pre-charge-off | DPD 90+ | Charge-off preparation; handoff to recovery |

**Behavioral triggers** are pre-defined rules that escalate a case to a collection action. The trigger design matters as much as the action: triggering too early is expensive (false positives); triggering too late allows accounts to slide into deeper delinquency where cure rates are far lower.

The cure rate drops sharply with DPD progression:

| DPD Bucket | Typical Cure Rate |
| --- | --- |
| DPD 1–29 | 60–80% |
| DPD 30–59 | 30–50% |
| DPD 60–89 | 15–25% |
| DPD 90+ | 5–10% |

This table is the core reason for early intervention programs. Catching an account at DPD 15 instead of DPD 45 is worth more than any collection technique applied later.

## Delinquency Stages and DPD Buckets

**Days Past Due (DPD)** is the number of days since a payment was due but not received. It is the universal currency of consumer lending risk measurement.

**Roll forward** is when an account moves from a lower DPD bucket to a higher one (deteriorating). **Cure** is when an account returns to current (DPD = 0) from any delinquency stage.

The roll rate matrix (covered in depth in Part 4) formalizes this: it shows the probability of transitioning from each DPD bucket to every other bucket over a one-month period. A healthy portfolio shows high cure rates from early DPD buckets and low roll-forward rates. A deteriorating portfolio shows the opposite.

**DPD 30 and DPD 90 are the standard reporting thresholds** used in portfolio management, investor reporting, and regulatory filings. DPD 30+ rate (share of portfolio 30 or more days past due) is the most common headline delinquency metric. DPD 90+ is the standard definition of "non-performing."

## Recovery and Charge-off

Once an account crosses DPD 90–180 (market-dependent), the lender writes it off the balance sheet. This is the charge-off event. From a P&L perspective, the loan's outstanding balance moves from assets to loss.

**Post-charge-off recovery** generates credit back against losses. The lender can:

- Continue internal collections (agent calls, payment plans)
- Sell the debt to a third-party collector (debt sale), receiving cents on the dollar
- Pursue legal judgment (for larger balances where legal cost is justified)

Recovery rates range widely — from 5–10% on old, deepened defaults to 25–40% on recently charged-off accounts where the borrower still has assets or income. Vintage quality heavily influences recovery: defaults from aggressive origination vintages tend to be deeper and harder to recover.

**Net Charge-off Rate (NCO)** adjusts for recoveries:

$$NCO\ Rate = \frac{\text{Gross Charge-offs} - \text{Recoveries}}{\text{Average Outstanding Balance}}$$

NCO is the credit loss measure that flows directly into P&L as Credit Loss provision. It is the metric that makes or breaks the margin calculation from Part 1.

## Payday Note

The payday loan lifecycle collapses to two events: disbursement and repayment/default. There is no in-life stage.

- No behavioral triggers to set
- No early intervention opportunities
- No restructuring options
- No DPD curve to monitor

The entire observable lifecycle is 30–45 days. If the borrower repays, the loan closes. If the borrower cannot repay, the lender has one choice: roll over the loan (extend it, usually with an additional fee) or write it off.

**Rollover policy** is the only management lever in payday. Whether to allow rollovers, how many, and at what cost is the equivalent of a restructuring policy in installment lending — but applied uniformly at the product level, not individually at the account level.

This compresses the analytical problem dramatically: since you can observe nothing in-life, everything depends on the origination decision. And since most payday borrowers are thin-file or unscored, that origination decision is made under severe information constraints.

In Part 4, you will see how portfolio-level metrics are built from aggregated loan lifecycle data — and why MOB (Month-on-Book) is the organizing dimension that makes installment lending measurable in a way that payday never can be.
