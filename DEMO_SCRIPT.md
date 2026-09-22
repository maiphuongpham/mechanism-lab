# Geoeconomic Mechanism Lab — 75–90 second demo

## 0:00–0:15 — What changed

Open **Geo-Graph → Deterministic GTAP** with **Interdependent / Global** selected.

> Last month we used a stylized positive-value auction. Geo-Graph now injects
> GTAP outcomes, allows welfare losses, and models how one policy affects every
> country—not only its target.

## 0:15–0:40 — Deterministic policy choice

Click **China**, then **All three**, so the country outcomes change. Return to
**Status quo**, then select the **U.S.** objective.

> These are the five policy bundles actually observed in GTAP. Under global
> welfare, the exact planner retains the status quo because every tariff bundle
> has negative aggregate equivalent variation. If the objective changes to U.S.
> welfare, all three tariffs are selected—but the table exposes large losses
> elsewhere and the compensation needed for participation.

## 0:40–1:10 — Uncertainty and learning

Open **Uncertainty + Geo-Graph**. Move **Other-country values** to 80%, then move
**U.S. ally values** to 120%.

> A single GTAP table is deterministic, so we introduce sensitivity around the
> calibration and train one objective-conditioned Geo-Graph. The sliders read
> cached offline neural evaluations: learned probabilities, the exact control,
> optimality gap, and country outcomes update together. Across 4,096 held-out
> profiles, Geo-Graph matches the exact package 99.51% of the time, with a mean
> hard-choice gap of only 0.04 million dollars.

## 1:10–1:25 — Close

Briefly click **CANet**, then return to **Geo-Graph**.

> CANet remains our auction baseline, where bids, payments, VCG, and regret are
> defined. Geo-Graph extends it to signed, interdependent public-policy effects.
> Next we replace synthetic sensitivity with estimated uncertainty and add
> strategic reporting and dynamics.

## If limited to exactly one minute

Skip the policy-card clicks and CANet tab. Show only:

1. **Global → U.S.** in Deterministic GTAP.
2. One slider movement in Uncertainty + Geo-Graph.
3. The 99.51% agreement result and closing sentence.
