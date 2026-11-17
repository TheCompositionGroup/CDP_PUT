# 02 — Measurement Protocol | CDP_PUT

**Version:** 0.1 | **Status:** Draft — requires preregistration before evaluation.

## 1. Unit of analysis
A **forecast** is a binary, exactly worded question with a probability p in [0,1], a frozen information cutoff, one resolution rule and a target resolution date ≤90 days from cutoff. Forecasts share an **event-family ID** when outcomes, evidence or causal mechanisms overlap. For inference, event families—not merely rows—may be the effective independent units.

Separate classes: **ACTOR**, **EVENT**, **TRANSMISSION**, **MARKET**. Do not average across classes without a preregistered rationale.

## 2. Admission gate (before knowing outcomes)
A question is accepted only if it is:
- Relevant to the development decision.
- Non-degenerate under a **documented, independent** baseline estimate between 5% and 95%.
- Objectively resolvable by a named source and adjudication rule.
- Scheduled for resolution no more than 90 days after cutoff.
- Open/unresolved at information cutoff.

Record all rejection reasons in the question register. A 5–95% admission filter can change the population being tested; report this selection rule and never infer skill outside it.

## 3. Data collection and controls
For each admitted forecast:
1. Assign a unique forecast ID and event-family ID.
2. Capture exact question, class, cutoff (UTC), resolution deadline, source hierarchy and fallback/void rule.
3. Save a contemporaneous evidence packet with URLs, retrieval times and source classification: **P** primary, **S** secondary, **A** analytical, **E** estimate, **R** protocol-generated, **X** excluded/unverified.
4. Record methodology used, analyst, assumptions and strongest red-team objection.
5. Specify **Baseline A** reference class and its probability derivation before forecast evaluation; prevent retrospective baseline selection.
6. For eligible market forecasts, separately capture **Baseline B** option-chain snapshot, extraction method, instrument terms, timestamp, liquidity limits and hash using a blinded process where feasible.
7. Freeze the forecast **before** its information cutoff and before its outcome is known.

Do not overwrite frozen probabilities. New material information requires a **new forecast ID**, linked to the predecessor.

## 4. Freeze and audit trail
- Serialize forecast packet as UTF-8 with LF line endings and no trailing whitespace, using a documented deterministic field order.
- Calculate SHA-256 and store the exact file and digest.
- Obtain an independent timestamp proof (e.g., RFC 3161 or OpenTimestamps), then verify it.
- Commit the record to version control; a Git commit alone is **not** equivalent to a trusted independent timestamp.
- Append outcome and score in a separate resolution record; preserve the original frozen file.

The CSV is an **index/template**, not by itself a cryptographically frozen packet. Future tooling should validate schema and automate canonicalization.

## 5. Resolution policy
Resolution adjudicators use the preregistered source hierarchy and exact criterion. Outcomes are **1**, **0**, or **UNRESOLVED/VOID**, with reasons and dated evidence. Distinguish a genuinely open future outcome from an ambiguous or missing resolution. Report unresolved rates; do not exclude ambiguous cases without displaying them and conducting a sensitivity analysis.

## 6. Scoring
For resolved binary forecast i, **Brier_i = (p_i − y_i)²**. Lower is better.

Aggregate Brier score: mean of eligible resolved Brier values under the preregistered weighting rule.

Against Baseline A, **Brier Skill Score = 1 − (BS_CDP / BS_A)** when BS_A > 0. Positive is better than A; zero indicates equality. Report uncertainty intervals and event-family clustering as appropriate. Calibration requires both graphical comparison and a preregistered numeric criterion. Resolution must report denominators and coverage.

For Baseline B, state explicitly that option-derived **risk-neutral** probabilities encode risk premia and microstructure, and are not direct physical-event probabilities. Only compare clearly matched underlying events and horizons with documented mapping uncertainty.

## 7. Reproducibility
A second independent analyst receives the approved cutoff-time evidence and written method without seeing the original forecast probability. Compare completion, probabilities, derivations and disagreements against **predefined** thresholds. Record disagreements and failed replications, not only successes.

## 8. Preplanned reporting
- Forecast count and effective event-family count by class and horizon.
- Admitted, rejected, unresolved and voided counts.
- Brier/CDP versus A; B only where a comparable economic proxy exists.
- Calibration, resolution, uncertainty and sensitivity to dependencies.
- Method provenance and red-team objections.
- Gatekeeper kill status K1–K7 and recommended action.

## 9. Critical limitation
No historical analysis, Brier result, statistical power value, or validated economic edge is represented as completed here. The N-Gate worksheet must be filled and approved before confirmatory inference.
