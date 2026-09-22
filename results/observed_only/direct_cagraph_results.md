# Direct GTAP-to-CAGraph sensitivity result

## Experiment

We use the signed GTAP `Total` equivalent-variation matrix as the input to one
objective-conditioned CAGraph-style policy selector. The matrix contains five
regions and five observed alternatives: the status quo, three separate 10%
heavy-manufacturing tariff shocks, and their observed simultaneous shock.

For training and testing, we generate sensitivity profiles by applying
correlated mean-one Gaussian perturbations with 10% relative scale to the GTAP
values. The perturbations have common, country, policy, and idiosyncratic
components, preserving both positive and negative outcomes. These profiles are
synthetic sensitivity draws around one GTAP calibration; they are not new GTAP
runs and should not be described as empirical uncertainty estimates.

The network receives:

- the perturbed signed region-by-policy valuation tensor; and
- one of three designer-objective vectors: Global, Blue, or Blue + Ally.

It outputs a probability distribution over the five observed packages. For the
hard decision, we select the package with the largest probability. Exact
enumeration of those same five packages supplies the finite-choice benchmark.

## Held-out result

The model was trained once and evaluated on 4,096 held-out sensitivity
profiles using seed 20260922.

| Metric | Result |
|---|---:|
| Held-out profiles | 4,096 |
| Exact-package agreement | **99.51%** |
| Mean hard-decision gap | **$0.04m** |
| 95th-percentile hard-decision gap | **$0.00m** |
| Maximum hard-decision gap | **$15.33m** |
| Mean probability assigned to exact package | **95.84%** |
| Mean differentiable-lottery gap | **$4.39m** |

The hard-decision gap is the exact objective value minus the objective value of
the CAGraph-selected package. The differentiable-lottery gap evaluates the
network's full probability mixture and is therefore distinct from the deployed
argmax decision.

## Base GTAP calibration

| Designer objective | CAGraph choice | Exact choice | CAGraph probability | Hard gap |
|---|---|---|---:|---:|
| Global | Status quo | Status quo | 89.31% | $0.00m |
| Blue | All three | All three | 100.00% | $0.00m |
| Blue + Ally | Red | Red | 100.00% | $0.00m |

## Country reports and payment benchmark

For the browser demonstration, Blue is the designer and the other four
regions are potential participants. A report control multiplies one country's
entire vector of five observed-package values; 100% is the GTAP row. This is a
restricted report parameterization, not an unrestricted combinatorial bid.

The displayed `Pays (VCG)` entries come from a separate exact affine-VCG
public-choice benchmark. They are not outputs of the trained CAGraph. For the
Global objective at the base profile, exact VCG selects the status quo and the
payments are:

| Participant | Pays, $m |
|---|---:|
| Red | 17,781.8 |
| Blue ally | 29,386.0 |
| Red ally | 1,126.2 |
| Rest of world | 532.2 |
| **Total** | **48,826.2** |

These positive payments at the status quo arise because the relevant outside
option is the public policy chosen without that participant, not zero exposure
to Blue policy. Each participant prefers its truthful VCG utility to its utility
under that opt-out policy. The total payment is a truthful benchmark, not a
general revenue lower bound. The exact maximum reported welfare over the five
packages is shown separately as the welfare upper benchmark.

## Admissible conclusion

The direct extension works as a small policy-selection experiment: a graph
network can ingest signed GTAP welfare outcomes and recover the exact ranking of
five observed packages under synthetic local perturbations. It does not yet
show incentive compatibility or individual rationality for the learned
CAGraph, robustness to a new GTAP calibration, or optimality over continuous
tariff intensities and unobserved policy combinations. The exact VCG overlay
has its own private-value, quasilinear truthfulness guarantee, which does not
transfer to CAGraph. Here, “CAGraph” denotes a CAGraph-style graph-attention
selector adapted to a global policy-package choice; it is not the original
auction architecture applied without modification.
