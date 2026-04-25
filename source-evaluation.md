# Source Evaluation

Load when Q5 (knowledge gaps) fires in triage, alongside source-quality.md and resource-procurement.md.

Covers the evaluation process for a source that has been found and accessed but whose quality and fitness for the task are uncertain. This sits between resource-procurement.md (finding and accessing sources) and source-quality.md (preference hierarchy). Use when a source is in hand and the question is whether and how much to rely on it.

---

## Fitness for Purpose

Before drawing on a source, verify it actually addresses the specific question — not a related but different one.

- **Population match:** Does the source's population match the one in question? A study on hospitalized patients may not generalize to outpatients. A dataset from one country may not apply to another. A benchmark constructed to test one model may have structural biases when applied to a different model. State the population explicitly and flag any mismatch.
- **Construct match:** Is the source measuring what the question is actually asking about? "Productivity" measured by hours worked is different from "productivity" measured by output. "Default rate" for SBA 7(a) loans is different from default rate across all small business loans. Check that the construct in the source matches the construct in the question before treating them as the same.
- **Level of analysis match:** Does the source operate at the right level — individual, organization, population, country? Evidence at one level does not automatically transfer to another. A country-level correlation does not establish an individual-level effect; a lab finding does not automatically generalize to field conditions.
- **Scope match:** Does the source address the specific claim, or only a related claim? A meta-analysis covering a broad intervention may not speak to the specific variant being evaluated. A general policy analysis may not address the jurisdiction in question. Name the scope explicitly and flag where the source falls short of the specific question.

- **Representative physical dimensions:** When using dimensional values for commercially available components — core geometries, package sizes, connector spacings — that were not sourced from a specific manufacturer's datasheet for a specific part number this session, label them as Tier 2 (representative) rather than presenting them as datasheet values. Precise-looking numbers suppress uncertainty signals because specificity implies verification. Name the specific product whose datasheet would confirm the dimension, or describe the bench measurement that would verify it. A calculation using representative dimensions for a component the user will purchase is a design starting point, not a specification.

---

## Methodological Quality

For empirical sources, assess whether the study design was appropriate for the claim being made.

**Study design hierarchy (approximate, varies by domain):**
- Systematic reviews and meta-analyses of RCTs: highest quality for causal claims
- Randomized controlled trials: strong causal evidence within study conditions
- Prospective cohort studies: good for incidence and association, weaker for causation
- Retrospective cohort and case-control: useful but susceptible to selection and recall bias
- Cross-sectional studies: association only, no temporal ordering
- Case reports and expert opinion: lowest evidentiary weight for general claims

When a source's design is weaker than the claim it's being used to support, flag the mismatch explicitly. A cross-sectional study cannot establish causation; a case report cannot establish frequency.

**For datasets and benchmarks, assess construction methodology:**
- How was data collected? Self-report, observation, administrative records, and instrumentation have different error profiles.
- What are the known limitations documented by the source creators themselves? If the creators flagged limitations, weight them.
- What was the benchmark designed to test, and does that design transfer to the current use case? A benchmark designed adversarially against one model may have structural biases when applied to another. A test constructed from a specific population may not cover the full range of cases relevant to the task.
- Are there ceiling or floor effects? A benchmark where most instances cluster at one end of the difficulty distribution provides less information about performance in the rest of the range.

**For benchmark stress tests specifically:**
- High pass rates on an external benchmark are weaker evidence of genuine coverage if the benchmark's categories overlap substantially with the self-designed tests it's meant to supplement. Flag this overlap rather than treating external validation as independent.
- A benchmark constructed by the same methodology as the system being tested provides less independent validation than one constructed by different methods or by a different team.

---

## Provenance and Incentive Structure

Who produced the source, and what incentives shaped its production?

- **Funding source:** Research funded by a party with a stake in the outcome requires heightened scrutiny — not automatic dismissal, but explicit acknowledgment. Industry-funded trials are not inherently invalid, but their effect sizes are systematically larger in favorable directions than independent replications.
- **Institutional incentives:** Sources produced by agencies measuring their own performance (government statistics on program effectiveness, corporate disclosures on financial performance) have different credibility profiles than independent audits. Note the difference.
- **Publication incentives:** Published studies are subject to publication bias — positive results are more likely to appear than null results. A single published positive finding should be interpreted in the context of how many unpublished studies may exist. Pre-registered studies are more credible than post-hoc analyses of the same data.
- **Advocacy and commercial sources:** When a source is produced by an entity with a clear advocacy position or commercial interest, treat it as potentially providing the best case for its position rather than a balanced assessment. It may still be accurate — but verify key claims against independent sources before relying on them.
- **Secondary vs. primary source:** A secondary source summarizing primary research may introduce distortions in summarization, emphasis, or interpretation. When a claim is important, check the primary source rather than relying on the summary.

---

## Currency and Stability

Recency matters differently depending on how fast the relevant facts change.

**Fast-changing (verify currency carefully):**
- Market prices, interest rates, exchange rates — can change daily
- Regulatory status, legal requirements — can change with legislation or court decisions
- Software versions, API specifications, platform features — can change with releases
- Political positions, organizational leadership, company ownership — can change at any time
- Epidemiological data during active outbreaks — can change weekly

**Moderate-changing (flag if over 2-3 years old):**
- Clinical guidelines and treatment recommendations
- Technology landscape assessments
- Economic and demographic statistics
- Organizational best practices in fast-moving fields

**Slow-changing (recency less critical):**
- Established scientific consensus (physics, chemistry, well-replicated biology)
- Historical facts and established records
- Mathematical results and formal proofs
- Foundational frameworks and theories with decades of replication

When a source's age is uncertain relative to a fast-changing claim, state this explicitly rather than presenting the information as current. Do not present data with a known collection date as if it reflects current conditions without noting the gap.

---

## Triangulation

When does a single source suffice, and when are multiple independent sources required?

**Single source may suffice when:**
- The claim is a well-established fact with no meaningful dispute
- The source is primary, authoritative, and directly addresses the specific claim
- The claim has low stakes and the cost of error is low
- The source is the only available evidence and its limitations have been flagged

**Multiple independent sources required when:**
- The claim is contested or the single source is isolated
- The stakes of error are high — medical, legal, financial, or safety-critical decisions
- The source has known limitations that a second source could compensate for
- The claim involves quantitative precision (a single figure stated with confidence requires corroboration)
- The source has incentive structure concerns that independent corroboration would address

**Independence matters:** Two sources that both derive from the same underlying data are not independent. Two news articles reporting the same study are not independent confirmation of the study's findings. Two industry reports citing each other's statistics are not independent. Independence requires different data collection, different methodology, or different analytical teams. When "multiple sources" are found but share a common origin, treat them as a single source.

---

## Calibrated Confidence

Match confidence in conclusions to the quality of the sources supporting them.

- A conclusion supported by a single, unfunded, peer-reviewed RCT warrants moderate confidence with explicit uncertainty.
- A conclusion supported by multiple independent replications across different populations warrants higher confidence.
- A conclusion supported by a single secondary source, an advocacy publication, or a source with incentive concerns warrants low confidence — state this rather than presenting the conclusion at full register.
- A conclusion where the best available evidence is expert opinion or case reports warrants explicit acknowledgment that stronger evidence is absent.
- When the evidence base is thin but the claim feels intuitively obvious, treat the intuition as a reason to seek verification rather than a substitute for it.

**The confidence statement should match the evidence statement.** If the evidence is qualified, the conclusion must be qualified. Stripping qualifications from a conclusion when summarizing a source's findings is a form of misrepresentation, even when unintentional. When sources themselves hedge, preserve the hedge rather than converting it to a definitive claim.

---

## Maintenance

When a source is evaluated during a session and its quality characteristics are informative for future use, note key findings in the session record. Sources that appeared credible but turned out to be mismatched, outdated, or compromised by incentive concerns are worth flagging in resource-procurement.md's domain index for future reference.
