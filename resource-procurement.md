# Resource Procurement

Load when Q5 (knowledge gaps) fires, or when the task involves gathering external information for problem-solving — not just evaluating sources already in hand.

Covers four capabilities: active resolution, access sequencing, failure handling, and source landscape by domain. For evaluating sources once found, see source-quality.md.

---

## Active Resolution Before Asking

When a knowledge gap is identified and a source type has been identified that could resolve it, attempt to access that source before concluding the gap is unresolvable or asking the user to provide it.

The sequence:
1. Identify what type of source would resolve the gap (see source-quality.md and "Identify the right resource type" in SKILL.md)
2. Attempt access — search, fetch, or check available tools
3. If access succeeds — **verify that the content is fit for the specific task before extracting and proceeding.** A source can be accessible and wrong for the purpose simultaneously. Check: does what's actually here match what was needed, not just the source category? A dataset of raw experimental measurements is not the same as a collection of administrable test items, even if both are described as "cognitive task data." If the content doesn't fit, treat this as a fitness failure and continue searching rather than using a mismatched source.
4. If access fails — diagnose why (network restriction, paywall, format, URL not in search results) and try a fallback path
5. Only after fallback also fails — escalate to the user with a specific request

Naming a useful source and waiting for the user to ask whether you've tried it is not sufficient. The attempt is required.

**What counts as an attempt:** Running a web search for the source, fetching a specific URL that appeared in search results, trying an alternative format or mirror of the same content, or using a bash tool to access a file. Knowing a source exists is not the same as having tried to reach it.

---

## Access Sequencing

For most external resources, the fastest path is:

1. **Search first** — use web_search with specific terms (dataset name, institution, course number). This surfaces the canonical URL and confirms current availability.
2. **Fetch the landing page** — use web_fetch on the URL from search results to get the actual content or confirm structure.
3. **Navigate to the specific content** — follow links from the landing page to the specific section, dataset, or problem set needed. Don't stop at the index page.
4. **Extract what's relevant** — pull only what's needed for the task, not the entire document.

For files uploaded by the user: check the file extension, apply the appropriate reading method from the file-reading skill, extract the relevant content. Don't assume the file is readable without checking format first.

**Common sequencing errors to avoid:**
- Stopping at search results without fetching — snippets are often insufficient
- Fetching the index page without navigating to the specific content
- Attempting to load a dataset directly without checking whether the URL appeared in search results (web_fetch only accepts URLs from search results or provided by the user)
- Assuming a format is readable without checking (e.g., .numbers files require numbers-parser, not pandas)

---

## Access Failure Handling

When access fails, diagnose before escalating.

| Failure type | Diagnosis signal | Fallback path |
|---|---|---|
| Network block | 403 Forbidden, proxy error | Try alternative host — GitHub raw vs Hugging Face, mirror vs original |
| URL not fetchable | "URL not provided by user or search results" error | Search for the specific page first, then fetch the URL from results |
| Paywall | Login required, purchase prompt | Look for preprint (arXiv), institutional open access version, or author's personal page |
| Format unreadable | Binary output, parse error | Check file extension, apply correct tool (numbers-parser for .numbers, xlrd for .xls, pandoc for .docx) |
| Content not in expected location | Index page only, no data | Navigate deeper — follow links from landing page to the specific section |
| Dataset too large | Memory error, timeout | Sample rather than load fully — use nrows, head, or grep to extract relevant subset |

Only after fallback fails: escalate to the user. Specify the exact failure type, what was attempted, and what the user would need to provide — the specific file, a direct URL, or pasted content.

---

## Proactive Sourcing

Don't wait to be asked whether a source has been tried. When any of these conditions are present, attempt resource access as part of the response — not as a follow-up:

- The task requires external data to be answerable (quantitative problem with missing parameters, factual claim requiring verification, stress test needing independent prompts)
- A specific dataset, archive, or repository is named or strongly implied by the task type
- The response would be materially better with external content than without it
- The user has expressed a goal (stress testing, finding problem sets, verifying a claim) that is served by external resources

The test: would a capable human problem-solver go look something up at this point, or wait to be asked? If the former, attempt access.

---

## Domain-to-Source Index

Maps problem types to known useful sources. Status labels: **[verified]** — accessed and confirmed fit for stated purpose; **[accessible, not fit]** — accessed but content does not serve the stated need; **[verified — blocked]** — confirmed inaccessible; **[unverified]** — not yet tested. Never promote a source to [verified] without confirming both access and fitness.

### Stress Testing and Benchmark Prompts

| Need | Source | Access path | Status |
|---|---|---|---|
| Misconception/false premise prompts | TruthfulQA | GitHub: github.com/sylinrl/TruthfulQA — TruthfulQA.csv (filter by Category column) | **[verified]** — GitHub accessible; Hugging Face blocked |
| Clinical reasoning under uncertainty | SCT-Bench | concor.dance / github.com/SCT-Bench/sctpublic — 750 Script Concordance Test questions, expert-panel scored | **[verified]** — both landing pages accessible |
| Medical diagnostic reasoning (real cases) | MedCaseReasoning | arxiv.org/abs/2505.11733 — 14K+ cases from PubMed Central open-access articles | **[verified]** — arXiv page accessible; dataset via PubMed Central |
| Cognitive task datasets (human psychology) | OpenCogData | nimh-dsst.github.io/OpenCogData — NIMH/DSST curated collection, MIT license, data on OSF/GitHub | **[accessible, not fit]** — contains raw experimental data (reaction times, EEG, behavioral measures), not administrable test items or reasoning problems |
| Cognitive bias prompts for LLM evaluation | BiasBuster | arxiv.org/abs/2403.00811 — 13,465 prompts across bias types, constructed with psychologists | **[verified]** — arXiv accessible; GitHub data access unconfirmed |
| Cognitive bias decision scenarios (hand-curated) | "Bias is in the Details" | arxiv.org/abs/2509.22856 — 220 scenarios, 8 biases, multiple-choice format | **[verified]** — arXiv accessible |
| Adversarial NLU prompts | AdvGLUE | GitHub: github.com/causalNLP/adv-glue | [unverified] |
| Logical reasoning problems | LogiQA | GitHub: github.com/lgw863/LogiQA-dataset | [unverified] |

### Operations Management and Logistics

| Need | Source | Access path | Status |
|---|---|---|---|
| Process analysis, capacity, inventory, supply chain cases | MIT OCW 15.761 | ocw.mit.edu/courses/15-761-introduction-to-operations-management-spring-2013 | **[verified]** — case preparation questions fully accessible |
| Transportation, scheduling, routing problems | MIT OCW 15.060 (Data, Models, Decisions) | ocw.mit.edu — search "15.060" | [unverified] |
| Operations research problem sets | INFORMS student competition archives | informs.org/community/student-chapters | [unverified] |

### Research and Evidence Evaluation

| Need | Source | Access path | Status |
|---|---|---|---|
| Peer-reviewed papers | arXiv (preprints) | arxiv.org — search by topic or paper title | [unverified — access likely works but not tested this session] |
| Clinical evidence | Cochrane Reviews | cochranelibrary.com — summaries publicly available | [unverified] |
| Government statistics | US: data.gov, census.gov; UK: ons.gov.uk | Direct fetch | [unverified] |

### Legal and Policy Reasoning

| Need | Source | Access path | Status |
|---|---|---|---|
| Case law | Google Scholar (scholar.google.com/scholar?as_sdt=4) | Search by case name or topic | [unverified] |
| US regulations | Code of Federal Regulations | ecfr.gov | [unverified] |
| Bar exam questions | NCBE (multistate bar) | ncbex.org — sample questions publicly posted | [unverified] |

### Quantitative and Mathematical Problems

| Need | Source | Access path | Status |
|---|---|---|---|
| Statistics problems | ISLR (Introduction to Statistical Learning) exercises | statlearning.com — book and exercises freely available | [unverified] |
| Mathematical optimization | Project Euler | projecteuler.net — problems fully public | [unverified] |
| Probability problems | OpenIntro Statistics | openintro.org/book/os/ | [unverified] |

### File Format Handling

| Format | Tool | Notes | Status |
|---|---|---|---|
| .numbers (Apple) | numbers-parser (pip) | Extracts via protobuf; only Question column present if Category not exported | **[verified]** |
| .csv | pandas read_csv | Use nrows for large files | **[verified]** |
| .xlsx | openpyxl (read_only=True) | See file-reading skill | **[verified]** |
| Hugging Face datasets | datasets library | Blocked by network egress proxy (403); use GitHub mirror instead | **[verified — blocked]** |
| GitHub raw files | web_fetch | Only works if URL appeared in search results first | **[verified]** |

---

## Maintenance

Update the domain index after each session where a new source is successfully accessed or confirmed blocked. Change [unverified] to [verified] only after actual access **and fitness confirmation** — the content must serve the specific stated need, not just be accessible. A source that is accessible but does not fit the stated purpose should be marked **[accessible, not fit]** with a note explaining the mismatch.

Status labels:
- **[verified]** — accessed this session and confirmed fit for the stated purpose
- **[accessible, not fit]** — accessed this session; accessible but content does not serve the stated need
- **[verified — blocked]** — confirmed inaccessible due to network/paywall
- **[unverified]** — not yet tested

When a source type is needed that isn't in the index, add it after attempting access — whether successful or not. A failed attempt with a documented failure mode is more useful than a gap in the index.
