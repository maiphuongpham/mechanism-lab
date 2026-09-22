# Geoeconomic Mechanism Lab — 60–90 second demo

## 0:00–0:20 — What changed

Open **Geo-Graph**.

> Last month, CANet used a stylized positive-value auction. This month we feed
> signed country-level welfare effects from GTAP directly into a CAGraph-style
> policy selector. The alternatives are the status quo, three observed tariff
> shocks, and the observed joint shock.

## 0:20–0:55 — Show the learned selector

Move one or two valuation sliders and switch between **Global**, **U.S.**, and
**U.S. + Ally**.

> We train one objective-conditioned network on correlated 10 percent Gaussian
> perturbations around the GTAP table. The bars are probabilities over policy
> packages—not fractional tariff rates. The screen compares CAGraph with exact
> enumeration of the same five observed packages.

Point to the two choices and the gap.

> On 4,096 held-out profiles, CAGraph selects the exact package 99.51 percent of
> the time. Its mean hard-decision optimality gap is 0.04 million dollars, with
> a worst observed gap of 15.33 million.

## 0:55–1:15 — Interpretation

Point to the country outcome table.

> This shows why signed, cross-country values matter: one package can benefit
> the designer while imposing losses elsewhere. It is a policy-selection
> result, not yet an incentive-compatible mechanism. Pricing, strategic reports,
> IR, dynamics, and richer GTAP counterfactuals are the next layer.

## If limited to one minute

Use the first two paragraphs, move one slider, cite **99.51% agreement** and the
**$0.04m mean gap**, then end with the final sentence.
