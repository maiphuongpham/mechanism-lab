# Geoeconomic Mechanism Lab — 60–90 second demo

## 0:00–0:20 — What changed

Open **Geo-Graph**.

> Last month, CANet used a stylized positive-value auction. This month we feed
> signed country-level welfare effects from GTAP directly into a CAGraph-style
> policy selector. The alternatives are the status quo, three observed tariff
> shocks, and the observed joint shock.

## 0:20–0:55 — Show the learned selector

Move one or two country-report sliders and switch between **Global**, **U.S.**,
and **U.S. + Ally**.

> We train one objective-conditioned network on correlated 10 percent Gaussian
> perturbations around the GTAP table. Each slider scales one country's entire
> vector of package reports; 100 percent is its GTAP row. The bars are
> probabilities over policy packages—not fractional tariff rates.

Point to **CAGraph welfare**, **VCG benchmark**, and **Welfare upper bound**.

> On 4,096 held-out profiles, CAGraph selects the exact package 99.51 percent of
> the time. Its mean hard-decision optimality gap is 0.04 million dollars, with
> a worst observed gap of 15.33 million. The VCG column is a separate exact,
> truthful public-choice benchmark; it is not the learned network's payment.

## 0:55–1:15 — Interpretation

Point to the country report and **Pays (VCG)** table.

> A positive payment is an EV-equivalent concession to the U.S. designer. A
> country can pay even under the status quo because opting out may cause the
> designer to choose a policy that harms it. CAGraph itself is still a learned
> policy selector; a learned payment head and regret-constrained incentive audit
> remain the next layer.

## If limited to one minute

Use the first two paragraphs, move one report slider, cite **99.51% agreement**,
and state that **VCG pays are a separate exact benchmark**.
