---
layout: post
title: "Deployment: Go-Live Is Not the Finish Line"
subtitle: "Pre-deploy checklist, why data products decay from day one, and rolling out safely"
tags: [data-product, product-management, data-science]
comments: true
series: "Data Product Design for Data Scientists"
series_part: 7
---

It is tempting to treat the approval from Part 6 as the finish line — the hard part, surely, is behind you. It isn't. A data product that goes live without monitoring, a rollback plan, and a clear owner is a liability the moment it starts making real decisions, and the failures that follow are usually invisible until they've already cost something.

## The Pre-Deploy Checklist

Before flipping the switch, confirm these three things exist — not "will exist soon," but actually exist and have been tested:

- **Monitoring is live, not planned.** At minimum, you need visibility into input data health (is the pipeline still delivering what it promised in the Part 3 requirements doc?) and output distribution (is the model's output distribution stable relative to what you saw in development?). If monitoring is still "on the roadmap for next sprint," you are not ready to deploy — you are ready to deploy blind.
- **A rollback plan exists and has an owner.** Define, explicitly, what triggers a rollback (a specific threshold breach, a specific complaint volume, a specific business metric moving the wrong way) and who has the authority to pull the trigger without waiting for a committee. A rollback plan that requires a meeting to activate is not a rollback plan.
- **Ownership is unambiguous.** Someone specific — by name, not by team — owns this product after launch: watching the monitors, responding to alerts, deciding when retraining is needed. If the answer to "who owns this once it's live" is "the team," it is nobody's job, and it will be neglected exactly when it matters most.

If any of these three is missing, that is itself grounds to delay deployment — even after a successful Part 6 approval. Approval to build was not approval to run unmonitored, and treating it as such is where day-one confidence turns into a quiet three-month decay nobody notices until a stakeholder does.

## Data Products Decay From Day One — Design for It

A piece of software, once shipped and bug-free, generally stays correct. A data product does not have that property, and pretending otherwise is the single biggest mismatch between data product deployment and standard software deployment.

- **Data drift** — the statistical properties of the input data change over time (new customer segments, seasonal shifts, a policy change upstream that alters what the input fields even mean). A model trained on last year's distribution is quietly answering questions about a population that no longer exists in quite the same way.
- **Model decay** — even with stable inputs, the relationship between inputs and outcome can shift (a fraud pattern evolves specifically to evade the model that was built to catch it; a macroeconomic shift changes what "risky" means). Decay here is often adversarial in a way software bugs never are.
- **Both start on day one**, not after some grace period. The moment a model is trained, its snapshot of the world begins going stale — sometimes slowly over months, sometimes fast if the underlying environment is volatile (fraud, market-linked risk). Treat monitoring as running from the moment of deployment, not from whenever someone first notices a problem.

This is precisely why the pre-deploy monitoring checklist above is not optional infrastructure — it is the mechanism by which decay that starts immediately gets caught before it becomes damage. A dashboard built after the fact, in response to a complaint, has already let the decay run unmeasured for however long it took someone to notice and ask.

## Soft Launch and A/B Before Full Rollout

Full rollout on day one — every affected account, every decision, all at once — maximizes the blast radius of anything you got wrong in development, no matter how careful Parts 2 through 6 were. A staged rollout costs a little time and buys a lot of safety:

- **Soft launch to a limited segment or shadow mode.** Run the new solution in parallel with the existing process (or on a small, low-risk segment) without letting it drive real decisions yet. Compare its outputs against what actually happened, or against the old process's decisions, before trusting it with real consequences.
- **A/B against the existing process**, where feasible, rather than a full cutover. This gives you a clean, contemporaneous comparison — the same time period, the same environment — rather than a before/after comparison that could be confounded by anything else that changed at the same time.
- **Widen gradually, with a checkpoint at each stage.** Move from a small pilot segment to a larger one only after confirming the monitoring signals from the pre-deploy checklist look healthy at the current scale — don't treat the initial pilot success as license to skip straight to 100%.

The instinct to rush straight to full rollout usually comes from the same place as skipping alignment in Part 4: it feels like progress, and staging feels like a delay. In practice, a staged rollout catches the kind of surprises — a data field that behaves differently for a segment you didn't test, a downstream system that chokes on volume — that would otherwise surface for the first time at full scale, where they're most expensive to fix.

Deployment is where the product starts actually creating (or destroying) value in production. Part 8 covers what keeps that value alive: the three observability pillars that determine whether a product quietly degrades or stays healthy long after the launch excitement has faded.
