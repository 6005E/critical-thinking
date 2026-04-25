# Quantitative and Numerical Tasks

Load when the task involves calculation, estimation, unit conversion, capacity planning, scheduling, financial modeling, or any situation where the primary output depends on correctly setting up and executing numerical reasoning.

---

## Normalization and Reference Points

- Any step involving normalization, ratio, or relative scaling has a reference-point dependency. Before executing that step, state the reference explicitly. A procedure applied against the wrong reference produces confidently wrong output with no visible reasoning failure. Stating the reference before calculating forces commitment to it and surfaces wrong anchors before they propagate.

---

## Distribution and Extension Assumptions

- When a calculation requires extending a known quantity across time, scale, or frequency — through pro-ration, interpolation, extrapolation, or averaging — state the distribution assumption explicitly before calculating and flag it as unverified unless the problem specifies it. Assuming a discrete or periodic quantity behaves continuously or uniformly is a hidden premise, not a neutral operation.

---

## Silent Defaults

- When a calculation requires a value that isn't provided, state the assumed value explicitly and flag it as an assumption before using it. Silent defaults — assumed rates, baseline quantities, standard configurations — are unverified premises. The absence of a stated value is not permission to assume the most obvious one without disclosure.

---

## Input Reliability Tiers

When a calculation chain includes numerical inputs of different reliability, label each input's tier before calculating:
- **(1) Verified:** sourced from a primary datasheet, measurement, or specification this session
- **(2) Representative:** typical or nominal value from secondary sources; varies by supplier, grade, or instance
- **(3) Assumed:** design choice or placeholder not derived from any source

The output of a calculation carries the tier of its weakest input. A result derived from a Tier 3 assumption should not be presented at the confidence register of Tier 1 data even if the calculation itself is exact. When inputs span multiple tiers, state which input is weakest and how the result would shift if that input changes.

---

## Sensitivity Identification

In a multi-step calculation where each step's output feeds the next, identify which input the final result is most sensitive to before presenting conclusions. The most sensitive input is the one whose uncertainty most changes the output — not necessarily the most uncertain input. State: (a) which input dominates output variance, (b) by how much the output shifts per unit change in that input, and (c) what verification would most reduce total output uncertainty. This is most important when inputs span multiple reliability tiers — the binding uncertainty is often a Tier 2 input whose nominal precision obscures its actual variability.

---

## Ambiguous Formulas

- When a formula, rate, or rule in the problem admits multiple interpretations that would produce materially different results, enumerate the key outcome for each plausible interpretation before calculating any in depth. Do not calculate interpretation A, find it problematic, and switch to interpretation B — this is sequential adoption, not enumeration. If one interpretation produces an impossible result, that result is itself diagnostic information about the specification, not a reason to abandon the interpretation without stating what it reveals. If the difference between interpretations is material to the conclusion, seek clarification before committing.

---

## Non-Standard Orientation

- When a component, formula, or element is used in a non-standard orientation, reversal, or repurposed configuration, re-derive its properties from the actual configured state before making any claims that depend on those properties. Do not carry over assumptions from the standard use case.

---

## Imported Formula Factors

- When importing a formula from a related context, verify that each dimensionless factor applies to the current configuration before using it. State what physical condition each factor represents and confirm that condition holds. Do not carry factors forward from a source formula without this check.

---

## Dependency Mapping

- When a problem involves multiple sequential dependencies, map the full dependency graph before attempting to sequence steps. Identify whether any cycles exist — circular dependencies cannot be resolved by sequencing alone and require external intervention to break one link. Do not attempt to sequence a circular dependency; identify which link is most breakable and address that first.

---

## Backward Reasoning from Deadlines

- When a scheduling or capacity problem states a hard deadline, work backwards from the deadline before planning forward. Identify the latest start time for each preceding step, then verify the forward sequence fits. Do not default to forward planning when a deadline is stated — backward reasoning surfaces conflicts earlier and more directly.

---

## See Also (Universal Instructions)

- Anchoring → "When producing a numerical estimate by adjusting from an initial figure" in pre-execution-core.md blind spots
- Asymmetric error cost → pre-execution-core.md core checks
- Binding constraint identification → pre-execution-core.md assumptions
