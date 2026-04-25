# Triage

Load on every invocation, immediately after SKILL.md. Answer all questions from prompt features before loading anything else. When uncertain on any question, default to yes — the cost of loading an unnecessary instruction cluster is lower than the cost of missing a relevant one. This rule governs file-loading decisions within an active session. The prior decision — whether to invoke the skill at all — is governed by the deployment description in SKILL.md.

**Simple prompt gate:** Before running triage questions, assess whether the prompt is a simple factual question, single-word or single-fact retrieval, or casual conversational exchange with no analytical content, hidden premises, or decision at stake. If yes — confirm briefly that the pre-execution check was run, answer directly, and load no conditional files. If uncertain, proceed with triage.

Based on answers, load the corresponding files from failure-mode-index.md before responding.

---

## Triage Questions

**Q0 — Domain skill discovery**
Does this task involve a specialized domain, technique, or document type that a dedicated skill file might address?

If yes: use the view tool to check /mnt/skills/user/ and /mnt/skills/public/ for relevant skill files. Read the frontmatter description of any candidate skill file to assess relevance. Load the skill file if it is relevant to the task. Do this before answering. A file can be found, assessed, and correctly not loaded — relevance assessment is the decision point, not file discovery. A domain-adjacent file whose purpose doesn't match the task type should be noted and not loaded.

This applies broadly — circuit analysis, hydraulic/pneumatic schematics, document creation, figure descriptions, file reading, frontend design, and any other domain where specialized instructions would improve accuracy or reliability. Do not assume a skill file doesn't exist; check first.

**Q1 — Flaw handling**
Does the question contain a binary framing, an unstated assumption that may not hold, or a missing specification that would significantly change the answer?

**Q2 — Argument structure**
Is there an explicit argument, position, or chain of reasoning to evaluate — either presented in the prompt or embedded in a source being analyzed?

**Q3 — Constructed artifact**
Is the primary output a non-fiction artifact the user will deploy — an argument, explanation, positioning statement, briefing document, speech, or similar constructed deliverable? Exclude conversational answers, recommendations, plans, and creative works — those are covered by Q4 and creative.md respectively.

**Q4 — Output calibration**
Does the response involve a recommendation, plan, prediction, or multi-step deliverable?

**Q5 — Knowledge gaps**
Does the task require domain-specific expertise, recently updated information, or evaluation of sources?

**Q6 — Skill building**
Is this a skill-building, diagnostic, or structural review task?

---

## Always-Load Content (regardless of triage answers)

- SKILL.md core — universal behavioral instructions
- pre-execution-core.md — universal pre-execution questions and monitoring
- triage.md (this file)

## Conditional Loading (based on triage answers)

See failure-mode-index.md for file mappings per question.

---

## Pre-Response Gate

Before telling the user you don't know something, can't do something, or need information from them — stop. Attempt to resolve the gap first using files, tools, and context already available in the session. This applies regardless of task type, including delivery, packaging, and administrative steps that feel routine. Asking the user or declaring a limitation is only appropriate after self-resolution has been attempted and failed.

---

## Mid-Execution Routing

During execution, when an instruction fires that appears in the Co-Firing Index (FIRING-LOG.md), check whether the associated file is already loaded. If not, load it before continuing.

This supplements pre-execution triage — prompt features don't always signal which domain files will be needed. Co-firing patterns are a more reliable signal once reasoning is underway.

Apply judgment: load the associated file when the co-firing instruction is genuinely active in the response, not merely mentioned. A response that touches on causal direction in passing does not warrant loading analytical.md; a response where causal direction is load-bearing does.
