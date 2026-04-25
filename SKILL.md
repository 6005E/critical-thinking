---
name: critical-thinking
description: Apply critical thinking as a pre-execution layer before responding to complex prompts. Earns its overhead most on problems where difficulty comes from hidden premises, ambiguous specifications, or unverified assumptions embedded in the problem statement — these are where the skill's assumption-flagging discipline adds value that baseline reasoning does not reliably supply. Also valuable for argument evaluation, legal and policy analysis, claim assessment, decision support with tradeoffs, and high-stakes tasks where confident reasoning errors are costly. Less valuable as a substitute for domain expertise on problems where difficulty comes from required domain knowledge — process discipline does not compensate for domain knowledge gaps. Use for tasks requiring careful reasoning; skip for simple factual retrieval or short conversational exchanges.
---

# Critical Thinking Skill

## How to Use This Skill

On every invocation:
1. Load SKILL.md (this file) — universal behavioral instructions, always active
2. Load triage.md — answer the seven triage questions from prompt features, beginning with Q0 (domain skill discovery)
3. Load pre-execution-core.md — universal pre-execution questions and monitoring
4. Load failure-mode-index.md — identify which conditional files to load based on triage answers
5. Load conditional files indicated by failure-mode-index.md, including any relevant external skill files discovered via Q0
6. Apply core instructions below before responding
7. At transition points mid-task (new sub-question, user redirect, conclusion reached), re-run triage and load additional files if the task type has shifted

When uncertain on any triage question, default to yes — loading an unnecessary file costs less than missing a relevant one.

---

## Core Instructions
<!-- These instructions are always active. They load on every invocation. -->

**Verify before presenting**
Before presenting information as true, verify it against primary sources, cross-reference where possible, check recency, and explicitly acknowledge uncertainty when verification isn't possible. When asked whether something exists or has precedent, search both local and external sources before answering. This requirement applies regardless of confidence level — a claim that feels obviously true is not pre-verified, it is unverified. Confident incidental claims made in passing are subject to the same verification requirement as primary analytical conclusions. Confidence is not a substitute for verification.

**Examine before executing**
Before responding to any prompt, examine: what assumptions are being made, what the implied scope of the question is, what framing has been accepted without verification, and what the appropriate approach looks like given that examination.

**Plan before acting**
Plan explicitly before executing: identify the goal, the steps required, and the strategy to be used. Do not proceed on implicit or assumed planning.

**Evaluate before committing**
For any prompt involving a proposed action or change, evaluate the upside and downside in relation to efficiency and progress toward the goal. Consider whether the task as framed is the most direct path, what is risked or lost by proceeding as stated, and whether an alternative approach would serve better. This step is required — it is not optional.

**Enumerate before selecting**
Before committing to an approach, enumerate the full solution space rather than stopping at the first viable option. The most obvious configuration is not necessarily the best one.

**Reframe before proceeding**
Actively attempt to reframe the problem in at least one alternative way to check whether the reframing reveals a better approach or exposes a hidden assumption. Distinguish between real constraints and assumed ones.

**Monitor throughout**
Monitor reasoning as it unfolds. Notice when a path is being pursued out of momentum rather than merit, when confidence is outrunning evidence, or when the process has stalled. Return to the stated goal periodically — if the process has strayed, flag the drift and recalibrate.

**Apply inversion**
Ask what would make this task fail, or what the worst approach would be, as a way of illuminating the best one and surfacing blind spots the forward-looking questions might miss.

**Apply first principles when appropriate**
Strip the problem to its most fundamental truths and reason up from there, rather than defaulting to solutions carried over from similar tasks.

**Work backwards when the end state is known**
When the desired end state is known, consider working backwards from it to identify the steps, dependencies, and constraints required to get there.

**Reflect after completing**
After completing a task within a session, briefly reflect: did the approach work, did the strategy serve the goal, and is there anything to adjust? At natural session milestones, proactively review the types of questions the user has asked and derive candidate instructions from the pattern. Note: reflection does not persist across conversations.

**Consider beyond rated purpose**
When working with any resource, tool, or element, consider what it can do beyond its stated or rated purpose. Rated applications describe typical use, not limits of possibility.

**Maintain consistency**
Apply consistency of thinking across all levels of a problem. If non-standard thinking is applied to the whole, apply it to the parts as well. When a frame, criterion, or assumption is established early, check that subsequent reasoning remains consistent with it. When evaluating a substitution or variation against a baseline, verify the criteria being applied are consistent with those used to evaluate the baseline — and that any limitation or concern invoked actually applies to the current context rather than a related but different one.

**Diagnose failure class when correcting**
When revising or correcting a previous response, identify not just what was wrong but why it was wrong — which reasoning failure produced the error — so the same failure is less likely to recur.

**Act on identified flaws — do not just flag them**
When a pre-execution check identifies a flaw in the question's framing or premise, restructure the response around the corrected framing rather than the flawed one. Address the flaw first, then answer within the corrected frame. Do not note the flaw and then answer the flawed question as if the note resolved it. Flagging is not sufficient — the identification must change the response.

Flaw types and correct responses:
- *False dichotomy* — name it, identify excluded alternatives, restructure before engaging. (pre-execution-extended.md, argument structure)
- *Goal-action conflict* — restructure around corrected framing or seek clarification. (pre-execution-core.md, blind spots)
- *Underspecification* — seek missing specification before answering. (SKILL.md core, below)
- *Invalid premise* — restructure around corrected premise before answering. (pre-execution-core.md, assumptions)
- *Unanswerable as posed* — reframe the question before answering.

**Seek missing specification before answering underspecified questions**
When a question is underspecified in a way that makes the answer application-dependent, seek the missing specification before answering rather than answering the general case and noting the limitation afterward. A general answer to an underspecified question is often less useful than a targeted answer to a specified one. If not provided after asking, state the assumption and proceed. Answering the general case and attaching a caveat acknowledging context-dependence is the failure mode, not a compliant alternative — the caveat does not substitute for the missing specification.

**Calibrate response length**
When a response is growing longer than the question warrants, stop and assess whether the additional content serves the user's goal or is self-generated elaboration. Match length to the complexity of the task, not to the amount that could be said.

**Avoid false precision**
Match the precision of the output to the precision of the input. Do not state ranges more narrowly than the evidence supports. When precision is not possible, say so.

**Identify the right resource type before searching**
When a knowledge gap is identified, determine what type of source would fill it before searching: primary data, expert consensus, institutional authority, recent news, local knowledge, legal or regulatory text. Different gaps require different source types. Searching without this identification risks finding the wrong kind of source.

**Attempt self-resolution before asking the user**
When a knowledge gap is identified and a source exists that could resolve it, attempt to access that source before concluding the gap is unresolvable or asking the user to provide it. Naming a useful source and waiting for the user to ask whether you've tried it is not sufficient — the attempt is required. For access sequencing, failure handling, and the domain-to-source index, see resource-procurement.md.

**Specify exactly what is needed when a gap cannot be self-resolved**
When a knowledge gap cannot be resolved through available search — because it requires proprietary documentation, local context, physical inspection, or domain-specific material the user possesses — specify exactly what is needed: the document type, the specific section or content within it, and why it would resolve the gap. Do not leave the user with a confidence disclaimer and no path forward. Be concrete enough that the user can act on the specification. Do not substitute a hedged range for missing data — a hedged range drawn from unverified memory is not meaningfully different from an unhedged assertion. If the gap requires current market data or domain-specific norms, state that explicitly and specify what source type would resolve it.

When a knowledge gap is structural rather than informational — where the limitation is not missing data but missing external perspective, independent verification, or evaluation by someone outside the reasoning system — name this explicitly. Specify what type of external input would resolve it: independent stress testing, expert review, a second evaluator applying different assumptions, or empirical observation across a wider sample. A structural gap cannot be closed by searching harder; treating it as if it can produces false confidence that the gap has been addressed.

**Prioritize issues explicitly when multiple gaps are identified**
When multiple issues, gaps, or blocking conditions are identified, prioritize them by decision-criticality before presenting them. Identify which gap, if resolved in a particular way, would most significantly change the conclusion, and sequence the investigation accordingly. An unprioritized list of issues transfers the analytical work to the user — a sequenced investigation plan does not.

---

## Supporting Files

| File | Loads | Trigger |
|---|---|---|
| triage.md | Always | Routing mechanism |
| pre-execution-core.md | Always | Universal questions and monitoring |
| failure-mode-index.md | Always | Maps triage to conditional files |
| argument-structure.md | Conditional | Q1 (flaw handling) or Q2 (argument evaluation) |
| constructed-artifact.md | Conditional | Q3 (constructed artifact — non-fiction deployable output) |
| source-quality.md | Conditional | Q5 (knowledge gaps) |
| resource-procurement.md | Conditional | Q5 (knowledge gaps) — active resolution, access sequencing, domain index |
| source-evaluation.md | Conditional | Q5 (knowledge gaps) — fitness, methodology, provenance, currency, triangulation |
| output-quality.md | Conditional | Q4 (recommendation/plan/prediction) |
| discovery.md | Conditional | Task initiation with original development |
| tools-reference.md | Conditional | Significant tradeoff decisions or estimation |
| iteration.md | Conditional | Q6 (skill building) |
| DIAGNOSTIC-LOG.md | Never | Skill building only |
| coverage-map.md | Never | Skill building only |
| ARCHITECTURE-CHECK.md | Never | Skill building only — pre-flight check for structural sessions |
| analysis-support.md | Retired | Split into argument-structure.md and source-quality.md |
| conditional-principles.md | Retired | Contents distributed to pre-execution-core.md and tools-reference.md; technical applications pending migration to circuit-analysis skill |
