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
- one of three designer-objective vectors: Global, U.S., or U.S. + Ally.

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
| U.S. | All three | All three | 100.00% | $0.00m |
| U.S. + Ally | China | China | 100.00% | $0.00m |

## Admissible conclusion

The direct extension works as a small policy-selection experiment: a graph
network can ingest signed GTAP welfare outcomes and recover the exact ranking of
five observed packages under synthetic local perturbations. It does not yet
show incentive compatibility, individual rationality, pricing, robustness to a
new GTAP calibration, or optimality over continuous tariff intensities and
unobserved policy combinations. Here, “CAGraph” denotes a CAGraph-style graph
attention selector adapted to a global policy-package choice; it is not the
original auction architecture applied without modification.
