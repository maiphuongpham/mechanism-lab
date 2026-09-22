# Geoeconomic Mechanism Lab — presenter script

Target length: 5–6 minutes.

## 1. Frame the extension (30 seconds)

Open **Geo-Graph → Deterministic GTAP**.

Say:

> Last month we demonstrated CANet on a deliberately stylized auction. This
> month we replace made-up positive values with policy outcomes from GTAP. That
> introduces three things immediately: economic structure, negative values,
> and effects on countries other than the policy target.

Point briefly to the three phrases under the title. Do not explain the network
yet.

## 2. Show why interdependence matters (90 seconds)

Keep **Global** selected. Toggle between **Independent** and
**Interdependent**.

Say:

> Independent is the old private-value-style abstraction: only the country
> directly exposed to a policy enters its own value. Interdependent restores
> the full GTAP incidence matrix, so a tariff aimed at one country changes the
> welfare of all five regions.

Return to **Interdependent**. Click the five policy-bundle cards one at a time.
Point to the country table changing.

Say:

> These cards are the policy choice set: status quo, three individual 10%
> heavy-manufacturing tariffs, and the observed simultaneous tariff package.
> Green and red entries are gains and losses in millions of dollars of
> equivalent variation.

End on **Status quo**.

## 3. Change the designer objective (60 seconds)

Click **U.S.**. The exact planner selects **All three**. Point to the exact
planner block and the country outcomes.

Say:

> If the designer maximizes only U.S. welfare, the preferred package changes
> to all three tariffs. But the same package creates large losses elsewhere.
> The compensation number is therefore an individual-rationality diagnostic,
> not a claim that those transfers are politically available.

Click **U.S. + Ally**.

Say:

> Adding the ally to the objective changes the preferred observed package
> again. The mechanism result depends on whose welfare is in the objective;
> that is an economic modeling decision, not a neural-network decision.

## 4. Move from one GTAP table to uncertainty (90 seconds)

Open **Uncertainty + Geo-Graph** and select **Global**.

Say:

> One GTAP table is deterministic, so a neural network adds nothing by itself.
> For a first sensitivity experiment, we perturb the valuation profile around
> that calibration and train one objective-conditioned Geo-Graph—not three
> separate networks.

Move **U.S. values**, **U.S. ally values**, and **Other-country values**. Start
with Other-country values at 80%, then move U.S. ally values to 120%.

Say:

> The browser is not running PyTorch. Each slider position reads a cached
> offline Geo-Graph evaluation. The probability bars, selected policy, exact
> planner control, and country outcomes update together.

Point to the exact comparison.

> Across 4,096 held-out sensitivity profiles, the learned hard choice matches
> exact enumeration 99.51% of the time. The remaining average hard-choice gap
> is 0.04 million dollars. These are synthetic sensitivity results—not new
> GTAP observations and not yet incentive-compatibility evidence.

## 5. Connect to last month (45 seconds)

Open **CANet → Trained CANet**.

Say:

> CANet is last month's auction baseline: agents receive goods, values are
> private, payments are defined, and VCG or first-price comparisons make sense.
> Geo-Graph is different: one public policy affects everyone, including through
> negative spillovers. That is why its controls are status quo, a myopic rule,
> and an exact policy planner—not VCG revenue.

## 6. Close (20 seconds)

Return to **Geo-Graph → Uncertainty + Geo-Graph**.

Say:

> The next step is to replace synthetic sensitivity with economically estimated
> uncertainty and then introduce strategic reports, participation constraints,
> and dynamic valuation updates. Today’s result establishes the data-to-policy
> pipeline and the signed, interdependent allocation architecture.

## Questions to anticipate

**Why not VCG on the GTAP table?**

VCG needs a defined allocation, reports, transfers, and quasilinear bidder
utilities. The current GTAP experiment is a public-policy package-selection
problem with affected stakeholders. Applying VCG before specifying those
objects would produce a number without a valid economic interpretation.

**Are the slider values new GTAP runs?**

No. They are cached sensitivity scenarios evaluated by the trained model.

**Were three models trained for the three objectives?**

No. One model receives the objective weights as an input condition.

**Is the browser running the neural network?**

No. Neural inference was run offline on a fixed slider grid and saved to JSON
for a reliable presentation.
