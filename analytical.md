# Analytical and Research Tasks

Load when the task involves interpreting evidence, conducting or evaluating a literature review, analyzing data, drawing conclusions from a body of research, or any situation where the primary output depends on correctly reading what a set of evidence actually shows.

---

## Sample and Selection Bias

- Published literature is not a representative sample of conducted research. Studies with positive or significant results are more likely to be published than null or negative results. When interpreting a body of published studies, account for publication bias before drawing conclusions — the observed distribution of results is not the true distribution.
- Whenever a sample is drawn through a process that selects for a particular outcome — publication, complaint submission, incident reporting, voluntary survey response — the distribution within the sample systematically overstates that outcome relative to the population. Treat the sample as evidence of the selected-for phenomenon, not as a representative picture of the whole.
- Funnel plot asymmetry, registered report comparisons, or grey literature searches are the appropriate tools for assessing publication bias — flag their absence when they're relevant.

---

## Heterogeneity Before Pooling

- Before aggregating or comparing studies, characterize what varies across them: populations, interventions, comparison conditions, outcome measures, follow-up periods. Pooling heterogeneous studies as if they answer a single question produces a meaningless average.
- If positive and null studies differ systematically on any dimension, that pattern is the finding — not the overall ratio of positive to null.
- "X intervention" and "Y outcome" are often not single constructs. Check whether the studies are actually studying the same thing before treating them as a coherent body of evidence.

---

## Effect Size and Clinical Significance

- Statistical significance is not clinical significance. A result can be statistically significant and practically meaningless. Always assess effect sizes, not only directional findings.
- When studies report only p-values or significance, flag the missing effect size information explicitly. Conclusions about whether something "works" require magnitude, not just direction.

---

## Null Results as Signal

- Null results in published literature are harder to get through peer review — they likely have stronger designs or larger samples than average. They deserve disproportionate analytical attention, not discounting.
- When null studies differ from positive studies in a systematic way, investigate the difference before pooling them. The difference may be the finding.

---

## Inferential Limits

- A literature review describes what was studied under specific conditions. Conclusions should be bounded by those conditions — not generalized to populations, settings, or variants not represented in the literature.
- When a body of evidence supports a conclusion within a bounded domain, state the bounds explicitly rather than presenting the conclusion as general.
- When a policy or intervention recommendation is derived from observational data showing that X correlates with Y, check whether a third variable could plausibly cause both X and Y. If a common cause exists, the correlation does not support intervening on X as a means of changing Y — the intervention may produce no effect while the common cause remains unchanged. Identify candidate confounders before accepting a causal interpretation of observational data.

---

## Experimental Validity

- When interpreting experimental results, check whether a stopping rule was pre-specified and followed. If results were checked during the experiment and the test was stopped when significance was reached, the reported p-value is inflated by multiple comparisons — the false positive rate rises with each interim check. Valid significance requires either a pre-specified stopping point or a sequential testing correction.
- When an experiment runs for a short period, check whether the duration covers at least one full user behavior cycle and whether a novelty effect could explain the result. Effects that reflect user curiosity about something new rather than genuine preference decay over time and do not persist after rollout.
- When an experiment produces an average effect, check whether the effect is uniform across key segments or concentrated in one. An average improvement that masks opposite effects in different segments produces worse outcomes when rolled out universally than when targeted. Segment the results before recommending universal rollout.

---

## Causal and Statistical Reasoning

- When an argument infers that A causes B from evidence that A and B co-occur, or that A preceded B, check whether B causes A is equally consistent with the evidence. Co-occurrence establishes neither direction; temporal precedence establishes sequence but not causation. State which causal direction is being assumed and whether the assumption is independently warranted.
- When an argument uses aggregate-level data to justify an individual- or sub-group-level intervention, check whether the aggregate pattern holds at the level of the intervention. A correlation observed across countries, cities, or populations does not establish that the same relationship holds within them — the units of analysis are different and the inference does not transfer without additional evidence.
- When aggregate metrics move, check whether the movement is widespread or concentrated before diagnosing a systemic cause. A large average shift can be produced by a concentrated issue affecting a subset rather than broad dissatisfaction or failure. Segment the metric before attributing it to a pervasive cause.
- When aggregate performance is maintained or improved, check whether it is being driven by increased concentration in fewer sources. Concentration that produces good aggregate results creates structural vulnerability — the loss of one major source can produce outsized damage that average performance conceals. Assess both the aggregate metric and its compositional distribution.
- When a rate or frequency metric is proposed as a mandate — reviews within 24 hours, calls per day, patients per hour — check whether hitting the target is achievable by reducing quality per instance rather than improving the underlying process. Rate metrics measure how fast; they don't measure how well. When speed becomes the target, thoroughness is the variable that adjusts.
- When a decision-maker draws conclusions about the predictive validity of their own selection criteria from their own portfolio of decisions, check whether their differential treatment of selected candidates is part of the causal chain. A decision-maker who systematically supports, develops, or favors selected candidates may be producing some of the outcomes they attribute to the selection criterion — the criterion appears predictive but the treatment effect is confounded with it.
- When an unusually strong or weak result is followed by a more moderate one, check whether the change reflects a genuine shift or regression to the mean — the tendency of extreme results to be followed by results closer to the underlying average, because extreme outcomes partly reflect random variation that doesn't persist. Regression to the mean predicts moderation after extremes regardless of any intervention or change in circumstances.
- When an intervention is evaluated as ineffective, check whether the implementation matched the dosage required for the intervention to work. A minimal-dose failure — a brief workshop, a short course, a single session — does not establish that the intervention is ineffective; it establishes that this dose was insufficient. Dosage is a variable in the intervention's effectiveness, not a fixed property of whether it was implemented.
- When evaluating a performance record, check whether the observed outcome has been compared to the base rate of similar outcomes by chance in the relevant population. Evaluating a record in isolation — without knowing how often it occurs by luck — produces systematic overattribution of skill. The relevant question is not "did this happen?" but "how often does this happen to someone without the attributed cause?"
- When an argument moves from an observed correlation to a recommended intervention, check whether the causal mechanism has been specified. Without a mechanism, the intervention is attached to the evidence rather than derived from it. Different mechanisms imply different interventions; an intervention designed without specifying the mechanism may address the wrong pathway entirely.
- When an argument draws a conclusion from a subset of a larger dataset, check: (1) whether the subgroup was defined before or after seeing the data — post-hoc subgroups inflate false positive risk; (2) whether the subgroup is large enough to support the confidence level implied by the conclusion; and (3) whether confounding variables co-vary with subgroup membership in ways that could explain the observed difference.
- When an argument dismisses an observed effect by citing the mechanism — "it's just placebo," "it's just expectation," "it's just social desirability" — check whether the dismissal conflates mechanism with efficacy. Mechanism and efficacy are separate questions: an effect can be real and persistent regardless of its mechanism. "It's just placebo" shifts the question from whether an effect exists to how it works, but does not answer whether the effect exists, how large it is, or whether it persists. Treat mechanism dismissals as prompts to examine the evidence for the effect directly, not as refutations of it.

---

## See Also (Universal Instructions)

These domain-specific checks have general counterparts in the always-load files:
- Selection bias → "biased evidence pool" instruction in pre-execution-core.md assumptions (general form)
- Inferential limits → "hasty generalization" in argument-structure.md
- Causal direction and mechanism → causal reasoning section above (formerly in analysis-support.md, now in analytical.md)
- Effect size vs. significance → "confidence matching evidence strength" in pre-execution-core.md uncertainty
- Aggregate movement → causal and statistical reasoning section above
