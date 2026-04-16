---
layout: post
title: "Risk Models & Analytics"
subtitle: "Label design, scorecards, vintage deep-dives, and closing the loop from score to portfolio outcome"
tags: [consumer-lending, portfolio-management]
comments: true
math: true
series: "Consumer Lending Portfolio Management 101"
series_part: 6
---

Every decision discussed in this series — who to approve, at what limit, at what rate, when to intervene, when to tighten policy — is ultimately informed by a model. This final part connects the analytical tools behind those decisions to the portfolio outcomes they are designed to influence. The goal is not to make you a model builder, but to make you a sophisticated consumer of models: someone who knows what to ask, what to trust, and when to override.

## Label Design: Defining "Bad"

Before any model can be trained, you must define what you are predicting. In credit risk, this means choosing a **label** — a binary definition of which borrowers are "bad" (default) and which are "good" (perform). This choice is consequential: different labels capture different risks and have different implications for policy.

Three standard label definitions in installment lending:

| Label | Definition | Characteristics |
| --- | --- | --- |
| `fpd1` | Missed first payment | Aggressive; catches fraud and intent-to-default early; narrow signal |
| `dpd30_within_mob3` | 30+ DPD at any point in first 3 months | Industry standard; balanced between early signal and loan coverage |
| `dpd90_at_mob6` | 90+ DPD at month 6 | Conservative; captures full loss; requires waiting 6 months for labels |

**Choosing a label depends on three factors:**

**Tenor.** For a 3-month short-term product, `dpd90_at_mob6` cannot be computed — the loan has already resolved. Use `fpd1` or `dpd30_within_mob3`. For a 24-month installment product, `dpd90_at_mob6` captures enough of the risk curve to be meaningful.

**Portfolio strategy.** If fraud prevention is the primary concern, `fpd1` is appropriate. If you are optimizing for lifetime credit performance, `dpd90_at_mob6` aligns incentives better.

**Data availability.** Training a model requires enough historical loans that have seasoned to the label observation point. For `dpd90_at_mob6`, you need loans originated at least 6 months ago. For new lenders or new products, `fpd1` is often the only feasible starting point.

**One critical caution:** Labels and model performance are inseparable. A model with a Gini of 65% on `fpd1` and a model with a Gini of 58% on `dpd90_at_mob6` are not directly comparable — they are predicting different things. Comparing model quality across different label definitions requires caution.

## Scorecard Fundamentals

A scorecard is a credit model that assigns a numerical score to each applicant, where higher scores indicate lower default probability (or vice versa, depending on convention). Portfolio managers do not need to build scorecards, but they need to understand how they work to interpret model outputs and challenge model recommendations.

**Weight of Evidence (WoE)** is the standard transformation used to convert a raw variable into a model-ready feature:

$$WoE_i = \ln\left(\frac{\text{Distribution of non-events in bin } i}{\text{Distribution of events in bin } i}\right)$$

Where "events" are bads (defaults) and "non-events" are goods. WoE transforms categorical and continuous variables into a consistent scale, handles missing values naturally, and reveals the monotonic relationship between a variable and default probability.

**Information Value (IV)** measures the total predictive power of a variable:

$$IV = \sum_{i} (\text{Dist}_{non-events,i} - \text{Dist}_{events,i}) \times WoE_i$$

Standard IV interpretation:

- IV < 0.02: Useless for prediction
- 0.02–0.1: Weak
- 0.1–0.3: Medium
- 0.3–0.5: Strong
- IV > 0.5: Suspiciously strong (possible data leakage)

**Gini coefficient** measures overall model discrimination — the ability to rank borrowers from lowest to highest default probability:

$$Gini = 2 \times AUC - 1$$

Where AUC is the Area Under the ROC Curve. A Gini of 0 means the model performs no better than random. A Gini of 1 means perfect discrimination. Typical consumer credit scorecards achieve Gini of 40–65%.

**What a portfolio manager needs to monitor:**

- Is the Gini stable month-over-month on new applicants? (Performance stability)
- Is the score distribution shifting in the approved population? (Population stability)
- Are recent vintages performing as the model predicted? (Calibration)

You do not need to understand the model internals to ask these questions. You need the model team to answer them with data.

## Vintage Deep-Dive: Reading the Curve

Introduced in Part 4, vintage curves deserve deeper treatment here as an analytical instrument for detecting model and underwriting failures.

**Three curve patterns and their diagnoses:**

**Parallel shift upward** — all recent vintages are elevated relative to historical vintages by roughly the same amount at each MOB.

*Diagnosis:* Systemic change — either macroeconomic deterioration affecting all borrowers simultaneously, or a broad underwriting policy change that was made too aggressively. Not a single-vintage problem.

*Response:* Tighten policy; model may need recalibration if it was trained on pre-shift data.

**Fan-out (diverging vintages)** — vintages approved under a looser policy progressively underperform, with the most recent being the worst.

*Diagnosis:* Gradual underwriting degradation, often associated with a period of policy loosening or a new channel that attracted lower-quality borrowers. The loosening experiment is failing.

*Response:* Reverse the policy changes; identify and clean up the problematic channel or segment.

**Early inflection on a single vintage** — one vintage inflects sharply upward at MOB 2–4 while adjacent vintages remain normal.

*Diagnosis:* Origination-period-specific event: fraud spike, specific channel failure, batch of falsified income documents, or an operational error in underwriting during that period.

*Response:* Investigate the specific vintage's origination data; if fraud, file reports and tighten fraud controls; the model itself may be fine.

**The MOB 3 rule of thumb:** For a 12-month loan, the shape of the vintage curve at MOB 3 explains roughly 60–70% of the variance in the eventual lifetime loss rate. This means early warning is real — you do not need to wait for the loan to mature to know if a vintage is bad. Developing quantitative thresholds for "MOB 3 curve above historical P90" is a concrete early warning system that any portfolio can implement.

## Behavioral Model

The origination scorecard answers "will this borrower default?" before disbursement. The behavioral model answers "will this borrower default in the next N months?" after the loan is in-life, using observed payment behavior.

**When to trigger the behavioral model:**

The model should be run at each billing cycle from MOB 2 onward, once at least one payment cycle has been observed. Running it before any payment data is available produces a model that is nearly identical to the origination score — you have nothing new to work with.

**Input signals for a behavioral model:**

| Signal | Type | Why It Matters |
| --- | --- | --- |
| Payment ratio | Continuous | Partial payment is a strong early distress signal |
| Days since last payment | Continuous | Staleness of last contact suggests disengagement |
| Partial payment flag | Binary | More predictive than payment ratio alone for some segments |
| DPD at last billing | Ordinal | Current delinquency status |
| Contact responsiveness | Binary | Did borrower respond to last collection call? |
| Change in payment pattern | Derived | Deteriorating trend more predictive than current level |

**Output:** Probability of reaching DPD 90+ within the next 3 MOB. This score drives collection prioritization — which accounts get proactive contact today, which get a restructuring offer, which go to legal.

**The behavioral model is the link between Parts 3 and 5.** Part 3 described behavioral triggers as management concepts; the behavioral model operationalizes them quantitatively. Instead of triggering at "DPD 15," you trigger at "behavioral score below threshold X," which is a better predictor of eventual default than DPD alone.

## Model Monitoring: PSI and Gini Decay

A model trained on 2023 data may not perform well on 2025 applicants. The population has shifted, macroeconomic conditions have changed, or the underwriting policy has moved. Model monitoring exists to detect these shifts before portfolio damage occurs.

**Population Stability Index (PSI)** measures whether the score distribution has changed between the training period and the current scoring period:

$$PSI = \sum_{i=1}^{n} \left(\text{Actual\%}_i - \text{Expected\%}_i\right) \times \ln\left(\frac{\text{Actual\%}_i}{\text{Expected\%}_i}\right)$$

Where each bin $i$ represents a score range (e.g., decile).

Standard PSI thresholds:

- PSI < 0.10: Stable; no action required
- 0.10 ≤ PSI < 0.25: Moderate shift; investigate
- PSI ≥ 0.25: Significant shift; retrain likely required

PSI detects population drift — the model is being applied to a different population than it was trained on. This does not necessarily mean model performance has degraded, but it increases the probability that it has.

**Gini decay** is the direct performance measure. It tracks whether the model's discrimination ability (Gini on new originations) is declining over time. Computing Gini requires waiting for outcomes to emerge — typically 6–12 months after origination, depending on the label definition.

A model with a Gini that has declined from 58% to 44% over 18 months is a model in decay. It is still better than random, but it is ranking borrowers less accurately than before. The question is whether the decay is gradual (acceptable; plan a rebuild) or sudden (investigate; a structural shift may have occurred).

**Retrain triggers:**

- PSI ≥ 0.25 sustained for 2+ months
- Gini decay of 10+ percentage points from peak
- Vintage performance deviating from model predictions by more than 20% for 2+ cohorts consecutively

## Closing the Loop: Score → Policy → Portfolio

This series has covered product economics, borrower behavior, loan lifecycle, portfolio metrics, management strategy, and now risk models. The final piece is connecting them into a cycle.

```plain
Risk Model → Credit Policy → Origination Mix → Vintage Performance → Portfolio Metrics → Policy Review → Risk Model
```

**Step by step:**

1. **Risk model** (origination scorecard) assigns a default probability to each applicant.

2. **Credit policy** uses the score to determine approval (cutoff), limit, and pricing tier. The policy translates a score into an action.

3. **Origination mix** is the result: the distribution of loan sizes, APRs, and risk segments in each vintage.

4. **Vintage performance** tracks how each cohort evolves over MOB — FPD, DPD curves, eventual NCO.

5. **Portfolio metrics** aggregate vintage performance into current portfolio health: DPD distribution, NCO rate, RAM.

6. **Policy review** compares actual vintage performance to model predictions. If recent vintages are outperforming predictions, the model is conservative — consider loosening. If underperforming, the model is optimistic — tighten or retrain.

7. **Model update** incorporates new data from recent vintages, recalibrates WoE bins, updates IV rankings, and — if PSI or Gini triggers are hit — retrains the model entirely.

This cycle runs continuously. The vintage curve is its ledger. The origination scorecard is its engine. The portfolio metrics are its dashboard. Policy decisions are its output.

**A final note on the MOB framework.** Throughout this series, every major concept has been anchored to MOB: FPD as an MOB 1 signal, DPD buckets tracked at each MOB, vintage curves plotted over MOB, behavioral models triggered from MOB 2, PSI computed on recent cohorts by origination MOB. This is not accidental. MOB is the dimension that makes installment lending measurable, comparable across time, and responsive to management intervention.

The closest equivalent in revolving credit is the account age or cycle count — useful, but less precise because the account balance and utilization fluctuate. Installment lending's fixed amortization schedule gives you something revolving credit never has: a clock that started at the same moment for every loan in a cohort, ticking at the same rate, toward the same terminal event. That is the analytical foundation everything else in this series rests on.
