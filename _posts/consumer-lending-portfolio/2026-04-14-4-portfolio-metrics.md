---
layout: post
title: "Portfolio Metrics"
subtitle: "Volume, credit quality, and profitability — the three layers every portfolio manager tracks"
tags: [consumer-lending, portfolio-management]
comments: true
math: true
series: "Consumer Lending Portfolio Management 101"
series_part: 4
---

If Part 1 defined the product and Parts 2–3 described how individual loans behave, this part assembles the view from above — the metrics that let a portfolio manager understand the health, scale, and economics of an entire book. These metrics are organized in three layers that answer three distinct questions: How big are we? How healthy are we? Are we making money?

## Why Three Layers

Each layer answers a different question, and you need all three:

- **Volume** tells you scale, but not quality. A rapidly growing portfolio can mask deteriorating credit.
- **Credit quality** tells you health, but not whether the business is viable. A pristine portfolio might be generating yield too low to cover costs.
- **Profitability** integrates both, but is a lagging indicator. By the time profitability deteriorates, the quality problems that caused it appeared months earlier.

The discipline of portfolio management is in reading all three layers simultaneously and understanding their lead/lag relationships.

## Layer 1: Volume Metrics

Volume metrics describe the scale and flow of the portfolio at a point in time.

| Metric | Definition | What It Tells You |
| --- | --- | --- |
| Origination Volume | Total principal disbursed in a period | Business growth pace |
| Outstanding Balance | Total principal owed across all active loans | Portfolio size |
| Active Loan Count | Number of loans currently in repayment | Portfolio breadth |
| Approval Rate | Approved applications / Total applications | Underwriting tightness |
| Take-up Rate | Accepted offers / Approved applications | Pricing competitiveness |
| Disbursement Rate | Disbursed loans / Accepted offers | Operational efficiency |

**Approval rate** is a credit policy signal. Dropping from 40% to 25% indicates tighter underwriting — either a deliberate policy change or an applicant population shift. Rising approval rates without improving credit quality is a warning sign.

**Take-up rate** reveals whether your offer terms are competitive. A low take-up rate on a good-credit segment means borrowers are finding better rates elsewhere. A high take-up rate on a bad-credit segment may mean you are the only willing lender — not a compliment.

**The funnel math matters:**

$$\text{Originations} = \text{Applications} \times \text{Approval Rate} \times \text{Take-up Rate} \times \text{Disbursement Rate}$$

A change in any stage affects volume. Attributing a volume shortfall to the right stage is the first step toward fixing it.

## Layer 2: Credit Quality

### DPD Distribution Snapshot

At any point in time, the portfolio can be segmented by current delinquency status. A healthy snapshot looks like a steep pyramid: a large majority of the portfolio is current, with progressively smaller shares in each DPD bucket.

| Status | Healthy Portfolio | Deteriorating Portfolio |
| --- | --- | --- |
| Current (DPD 0) | 88–93% | 75–82% |
| DPD 1–29 | 4–7% | 10–14% |
| DPD 30–59 | 1–3% | 3–6% |
| DPD 60–89 | 0.5–1.5% | 2–4% |
| DPD 90+ | 0.5–1% | 2–5% |

Reading this snapshot monthly reveals directional trends. A DPD 30+ rate that rises from 3% to 6% over two quarters is a concrete signal, not just a feeling.

### FPD Rate, DPD30 Rate, DPD90 Rate

These three rates are the standard headline metrics for credit quality, with different lead/lag characteristics:

- **FPD Rate**: Leading indicator. Measured within weeks of origination. Problems appear here first.
- **DPD30 Rate**: Concurrent indicator. Reflects current portfolio health.
- **DPD90 Rate**: Lagging indicator. Reflects loan quality from 3–6 months ago.

A portfolio manager tracking all three can identify whether a problem is new (FPD rising, DPD30/90 still stable), current (DPD30 rising, DPD90 lagging), or resolved (DPD30 recovering, DPD90 still elevated from a past episode).

### The Vintage Curve

The vintage curve is the central analytical tool of installment lending. It is the one visualization that no portfolio manager can do without.

**Definition:** A vintage is a cohort of loans originated in the same time period (typically a calendar month or quarter). The vintage curve plots cumulative loss rate (or cumulative DPD90+ rate) on the y-axis against Month-on-Book (MOB) on the x-axis. Each line represents one origination vintage.

$$\text{Cumulative Loss Rate}_{v,m} = \frac{\sum_{t=1}^{m} \text{Net Charge-offs}_{v,t}}{\text{Original Disbursed Balance}_v}$$

Where $v$ is the vintage cohort and $m$ is the MOB.

**How to read the vintage curve:**

- All vintages begin at (MOB 0, 0%) and curve upward as losses emerge
- Loss emergence is front-loaded in the first 12–18 MOB, then slows as surviving accounts mature
- Curves converge toward a terminal loss rate (also called "lifetime loss rate")
- Comparing vintages at the same MOB shows relative quality — a later vintage tracking above earlier vintages at MOB 6 is an early warning

**What good looks like:** Vintage curves that are tightly banded, with recent vintages tracking below or within historical ranges, indicate consistent underwriting quality.

**What an early warning looks like:** A recent vintage whose curve inflects upward sharply at MOB 3–6 and runs above the historical band. At this stage, the full loan lifecycle has not played out, but the trajectory is clear. This is when to tighten policy, not wait for MOB 12 confirmation.

The vintage curve's power comes from MOB normalization. By aligning all cohorts to their origination date rather than calendar date, you can compare loans of the same age regardless of when they were originated. This is what makes installment lending analytically tractable compared to revolving credit, where there is no fixed origination point.

### Roll Rate Matrix

The roll rate matrix formalizes the DPD transition probabilities discussed in Part 3. It shows, for each DPD bucket, the probability of being in each other bucket one period later.

A representative roll rate matrix:

| From \ To | Current | DPD 1–29 | DPD 30–59 | DPD 60–89 | DPD 90+ |
| --- | --- | --- | --- | --- | --- |
| Current | 95% | 5% | — | — | — |
| DPD 1–29 | 70% | 15% | 15% | — | — |
| DPD 30–59 | 35% | 10% | 25% | 30% | — |
| DPD 60–89 | 15% | 5% | 15% | 25% | 40% |
| DPD 90+ | 8% | — | — | — | 92% |

Reading this: a borrower currently in DPD 1–29 has a 70% probability of curing (returning to current) and a 15% probability of rolling forward to DPD 30–59. A borrower in DPD 90+ has an 8% cure rate and a 92% probability of staying there (toward charge-off).

The roll rate matrix is also a forward-loss projection tool. Given today's DPD distribution and historical roll rates, you can estimate next month's charge-off volume.

### Net Charge-off Rate (NCO)

NCO is the realized credit loss rate after recoveries. From Part 3:

$$NCO\ Rate = \frac{\text{Gross Charge-offs} - \text{Recoveries}}{\text{Average Outstanding Balance}}$$

NCO is typically reported on an annualized basis. An NCO rate of 6% means the portfolio is losing 6 cents per dollar of outstanding balance per year to credit loss. This is the number that flows directly into the P&L as Credit Loss provision.

## Layer 3: Profitability

### Yield and Cost of Risk

**Yield** is the annualized revenue rate on the portfolio:

$$\text{Yield} = \frac{\text{Annual Interest Income + Fee Income}}{\text{Average Outstanding Balance}}$$

**Cost of Risk (CoR)** is the expected credit loss provision as a percentage of outstanding balance. It is forward-looking — it reflects what you expect to lose, not just what you have already charged off. CoR is typically set by provisioning policy and lags NCO slightly when portfolio quality is changing.

### Net Interest Margin and Risk-Adjusted Margin

$$NIM = \text{Yield} - \text{Cost of Funds}$$

$$RAM = \text{Yield} - \text{Cost of Funds} - \text{OpEx} - \text{CoR}$$

**Risk-Adjusted Margin (RAM)** is the cleanest measure of portfolio profitability per unit of balance. It is the number that answers "are we making money on this book?" after accounting for all costs.

A RAM of 3% on a $100M portfolio generates $3M in annual economic profit. If RAM turns negative, the portfolio is destroying value regardless of how much interest income it generates.

### LTV of a Repeat Borrower

The Lifetime Value of a repeat borrower was introduced in Part 2. From a metrics perspective, it is the sum of RAM contributions across all loans in the relationship:

$$LTV = \sum_{k=1}^{K} \frac{RAM_k \times B_k / 12}{(1+d)^{t_k}}$$

Where $B_k$ is the average balance for loan $k$, $t_k$ is the time of loan $k$ in years from the current date, and $d$ is the discount rate. As behavioral risk decreases with each successful repayment, $CoR_k$ falls, increasing $RAM_k$.

This is why repeat borrower acquisition and retention strategy is a core profitability lever, not a nice-to-have. Reducing $CoR$ on repeat borrowers by even 2–3 percentage points drives substantial LTV improvement.

## MOB as the Analytical Spine

Every metric in this part — FPD, DPD rates, vintage curves, roll rates, NCO — is organized around Month-on-Book. MOB is not just a time variable; it is the framework that makes installment lending measurable.

**Why MOB works for installment but not for revolving credit:**

An installment loan has a fixed origination date, a fixed repayment schedule, and a fixed terminal date. Every loan of the same tenor has the same loss emergence timeline. A DPD90 event at MOB 3 on a 12-month loan is a very different signal than the same event at MOB 10. MOB normalizes for this.

Revolving credit (credit cards, lines of credit) does not have a fixed origination date in the same sense — the account may be opened but dormant, and the relevant question is often "when did the borrower start using the product seriously?" This makes vintage analysis more ambiguous.

For installment portfolios, MOB gives you a predictable loss emergence curve with defined inflection points, a consistent comparison basis across cohorts, and clear early warning thresholds. This is the analytical advantage that makes portfolio management tractable.

In Part 5, you will see how these metrics translate into management actions — specifically when to tighten policy, when to investigate, and how to manage the structural risks that even well-measured portfolios face.
