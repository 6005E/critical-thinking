# Failure Mode Index

Load after triage.md. Maps triage answers to instruction files. Load all files whose trigger condition is met. When multiple conditions are met, load the union of their files.

---

## DOMAIN SKILL DISCOVERY [Q0]
*Trigger: task involves a specialized domain, technique, or document type*

Action: use the view tool to inspect available skill files before answering.

Discovery sequence:
1. View /mnt/skills/user/ — lists user skill directories
2. View /mnt/skills/public/ — lists public skill directories
3. For any candidate directory, view its SKILL.md frontmatter to assess relevance
4. If relevant: load the skill file and apply its instructions alongside the critical thinking files
5. If not relevant: note why the file was assessed and rejected — finding a file does not obligate loading it. A domain-adjacent file whose purpose doesn't match the task type should be explicitly not loaded, not silently skipped.

Known skill file locations (not exhaustive — always check directories for new additions):
- Electronics / circuit analysis: /mnt/skills/user/circuit-analysis/SKILL.md
- Hydraulic/pneumatic schematics: /mnt/skills/user/hydro-pneuma-update/SKILL.md
- Figure descriptions: /mnt/skills/user/figure-descriptions/SKILL.md
- Document creation (.docx): /mnt/skills/public/docx/SKILL.md
- PDF creation/manipulation: /mnt/skills/public/pdf/SKILL.md
- Presentations (.pptx): /mnt/skills/public/pptx/SKILL.md
- Spreadsheets (.xlsx): /mnt/skills/public/xlsx/SKILL.md
- Frontend/web UI: /mnt/skills/public/frontend-design/SKILL.md
- File reading: /mnt/skills/public/file-reading/SKILL.md

Note: the known list is a shortcut — do not treat it as exhaustive. When a task domain is not on the list, check the directories. New skills may have been added since this file was last updated.

Relationship to critical thinking files: domain skill files are complementary, not replacements. Load both — critical thinking handles reasoning structure, domain skill handles domain-specific verification, workflows, and failure modes.

---

## FLAW HANDLING [Q1]
*Trigger: question contains binary framing, unstated assumption, or missing specification*

Always-load content covers:
- SKILL.md core: flaw typology and act-on-identified-flaws instruction
- pre-execution-core.md: blind spots section (goal-action conflict)

Additionally load:
- argument-structure.md: false dichotomy instruction

Note: false dichotomy loads via flaw handling regardless of whether Q2 fires — it applies to direct questions, not only argument analysis tasks.

---

## ARGUMENT STRUCTURE [Q2]
*Trigger: explicit argument, position, or chain of reasoning to evaluate — presented in the prompt or embedded in a source being analyzed*

Load:
- argument-structure.md (full file)

Also trigger:
- FLAW HANDLING — arguments frequently contain flawed framing

---

## CONSTRUCTED ARTIFACT [Q3]
*Trigger: primary output is a non-fiction artifact the user will deploy — argument, explanation, positioning statement, briefing document, speech, or similar constructed deliverable. Exclude conversational answers, recommendations, plans, and creative works.*

Load:
- constructed-artifact.md (full file)

Note: Q3 and Q2 can co-fire when the task involves both constructing and evaluating an argument (e.g., draft a rebuttal to this position). Load both files when both conditions are met. Q3 and Q4 can co-fire when a recommendation is being packaged as a deployable artifact — load both and apply upstream framing checks before downstream quality checks.

---

## OUTPUT CALIBRATION [Q4]
*Trigger: recommendation, plan, prediction, or multi-step deliverable*

Load:
- output-quality.md (full file)

---

## KNOWLEDGE GAPS [Q5]
*Trigger: domain-specific expertise, recently updated information, or source evaluation*

Always-load content covers:
- pre-execution-core.md: assumptions section (domain gap, jurisdiction, currency)

Additionally load:
- source-quality.md (full file — source preference hierarchy, four-dimension evaluation)
- resource-procurement.md (full file — access sequencing, failure handling, domain index)
- source-evaluation.md (full file — fitness for purpose, methodological quality, provenance, currency, triangulation)

---

## SKILL BUILDING [Q6]
*Trigger: skill-building, diagnostic, or structural review task*

Load:
- iteration.md
- DIAGNOSTIC-LOG.md
- ARCHITECTURE-CHECK.md (if structural changes are being made or reviewed)
- coverage-map.md (if generating candidates or reviewing gaps)
- FIRING-LOG.md (if reviewing instruction efficiency or breadth)
- DESIGN-RATIONALE.md (if evaluating structural changes or considering reversing an architectural decision)

---

## DOMAIN FILES

*Trigger: task involves a specific domain with its own failure mode patterns*

| Domain | File | Trigger signals |
|---|---|---|
| Interpersonal / communication | interpersonal.md | Delivering difficult messages, navigating conversations, giving feedback, managing relationships, "what should I say," behavioral change conversations, disciplining or correcting someone, getting someone to do something differently |
| Strategic / planning | strategic.md | Resource allocation, business strategy, runway/budget decisions, hiring decisions, constraint analysis, "should we do X" under real constraints |
| Analytical / research | analytical.md | Literature review, evidence interpretation, data analysis, research synthesis, "what does the evidence show" |
| Creative tasks | creative.md | Fiction writing, screenwriting, narrative structure, character development, world-building, poetry, game design, "how do I write X" |
| Quantitative / numerical | quantitative.md | Calculation, estimation, capacity planning, scheduling, unit conversion, financial modeling, logistics, any task where the primary output depends on correctly setting up numerical reasoning |

---

## Scaling Note

To add new instruction clusters: create a new file, add a triage question or extend an existing one, add an entry here. Always-load content (SKILL.md, pre-execution-core.md, triage.md) does not change when new clusters are added.
