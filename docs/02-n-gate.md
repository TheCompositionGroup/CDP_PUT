# 02 — N-Gate | Sample Feasibility and Power

**Status:** OPEN / NOT CLEARED  
**Purpose:** Determine whether the project can obtain enough *independent* prospective evidence to justify a confirmatory validation study. Merely generating many correlated forecasts does not clear this gate.

## Protocol decision worksheet
| Parameter | Proposed/approved value | Evidence or rationale |
|---|---|---|
| Primary endpoint | **TBD** | Recommended candidate: paired Brier-score difference vs Baseline A |
| Null hypothesis | **TBD** | E.g., mean paired improvement ≤0 |
| Minimum useful effect | **TBD** | Must be justified by decision utility, not observed test data |
| One-/two-sided test | **TBD** | Choose before outcomes |
| Type I error alpha | **TBD** | Approve in analysis plan |
| Statistical power | **TBD** | Approve in analysis plan |
| Unit of inference | **TBD** | Event family or dependency-adjusted equivalent |
| Variance assumption | **TBD** | Pilot or defensible literature; include uncertainty |
| Correlation/design effect | **TBD** | Within-family and cross-market dependencies |
| Planned exclusions | **TBD** | Resolution failure, missing baselines, voids |
| Resolution loss allowance | **TBD** | Avoid overstated attainable N |
| Calendar recruitment rate | **TBD** | Independent resolvable events per month |
| Obtainable effective N | **TBD** | Forecast window and recruitment estimate |
| Required effective N | **TBD** | Reproducible calculation/simulation |
| Gate result | **NOT CLEARED** | Required N must be obtainable under stated assumptions |

## Recommended analysis design
Choose a prospective paired comparison, since each eligible forecast can be compared to the same event's preregistered Baseline A. Let **d_i = (p_A,i − y_i)² − (p_CDP,i − y_i)²**; positive d_i favors CDP. Estimate uncertainty using **event-family-level** resampling or a justified cluster-aware method. If N is small, rare event distributions and selection can make normal approximations unreliable; use simulation/pilot distributions and sensitivity analyses.

**Illustrative only, not a power calculation:** 100 forecast rows from 10 highly correlated event families are not equivalent to 100 independent observations.

## Feasibility test
1. List forecast-generating event families within the next study horizon.
2. Estimate admission rate, objective-resolvability rate, baseline coverage and attrition.
3. Model correlations and calculate an effective independent N range.
4. Calculate required N across plausible effect sizes and variance assumptions.
5. Compare obtainable N with required N and project resources.
6. Document an approval decision.

## Decision mapping
- **CLEAR:** credible attainable N meets preregistered power target under reasonable sensitivity bounds.
- **REFINE:** endpoint, recruitment or clustering assumptions can realistically be improved.
- **HOLD:** missing data prevent a credible assessment.
- **STOP/PIVOT:** adequate independent evidence cannot realistically be obtained for this test article.

**Gatekeeper decision:** Pending  
**Reviewer:** Unassigned  
**Date:** Unassigned  
**Next action:** Specify endpoint, minimum useful effect, variance assumptions and forecast-family recruitment estimate.
