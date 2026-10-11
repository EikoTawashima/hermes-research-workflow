---
name: research
description: Targeted Web research and extraction of compact, verifiable evidence directly relevant to a research question.
---

# WEB RESEARCH

## Mission

Research information on the Web and provide the Researcher only with the elements required to build an Evidence Packet.

The role of this skill is:

SEARCH → VERIFY → EXTRACT → COMPRESS

It must never unnecessarily transmit the full contents of Web pages.

---

# RESEARCH TOOL

Use DuckDuckGo only for Web search.

Do not use another search engine.

---

# CORE PRINCIPLE: BOUNDED CONTEXT

Web content must be treated as potentially very large.

The skill must therefore prevent entire pages from being retained in context when only a few elements are required.

The workflow is:

Search
→ source selection
→ open
→ locate relevant passages
→ targeted extraction
→ atomic evidence
→ discard irrelevant content

Never:

Search
→ open
→ retain entire page
→ pass entire page to Researcher.

---

# RESEARCH BUDGET

Per question or sub-question:

- maximum 3 opened sources;
- maximum 8 evidence items per source;
- maximum 20 evidence items overall;
- approximately 100 tokens maximum per evidence item;
- approximately 2,500 tokens maximum of extracted factual content;
- approximately 4,000 tokens maximum for the complete skill output.

These are hard safety budgets.

If the budget is reached, do not continue collecting unless a critical piece of information or an essential contradiction still needs to be verified.

---

# WORKFLOW

## Step 1 — Read the task

Read the question provided by the orchestrator or Researcher.

Identify:

- the exact question;
- potential sub-questions;
- required facts;
- required quantitative data;
- required dates;
- relevant entities;
- temporal constraints.

Do not research information that does not contribute directly to answering the question.

---

## Step 2 — Build focused queries

Create short, specific DuckDuckGo queries.

Avoid overly broad queries likely to return large amounts of irrelevant content.

When appropriate:

- search for a primary source first;
- then search for an institutional or specialist source;
- use a secondary source for comparison or additional context.

---

## Step 3 — Select sources

Select the most relevant sources before opening them.

Priority:

1. primary or official sources;
2. scientific or institutional sources;
3. reliable specialist sources;
4. reputable media;
5. other relevant sources.

Do not use Wikipedia as a source.

Prefer recent sources when the information may have changed over time.

---

# SOURCE LIMIT

Open a maximum of 3 sources per question or sub-question.

A fourth source is allowed only if:

- an important contradiction must be checked;
- a previous source is inaccessible;
- the first three sources do not establish a critical piece of information.

When possible, replace a less relevant source rather than continuously increasing the number of sources.

---

# STEP 4 — OPEN A SOURCE

When opening a source:

Do not unnecessarily read or retain the entire content.

Immediately identify:

- relevant sections;
- passages containing the requested information;
- relevant tables;
- dates;
- figures;
- statements directly related to the question.

Ignore:

- menus;
- navigation;
- advertisements;
- comments;
- recommendations;
- unrelated articles;
- irrelevant promotional content;
- footers;
- general background information that is not needed.

---

# TARGETED EXTRACTION

For each source, extract only information that directly answers the question.

Every extraction must be converted into an atomic evidence item.

Format:

[E1]

Claim:
[minimum factual claim]

Evidence:
[short passage or precise data supporting the claim]

Source:
[source name]

URL:
[URL]

Date:
[date if available]

---

# ATOMIC EVIDENCE RULE

One evidence item should contain one main piece of information.

Bad:

> This page explains the company's history, business, financial results, management and future outlook.

Good:

> The company reported €4.2 billion in revenue in 2025.

If several independent pieces of information are required, create separate evidence items.

---

# TABLE EXTRACTION

Never reproduce an entire table when only a few cells are required.

Identify and extract only the relevant cells.

Example:

Instead of transmitting:

| Year | Revenue | EBITDA | Employees | Debt |
| ... | ... | ... | ... | ... |

transmit only:

[E1]

Claim:
Revenue was X in 2025.

Evidence:
2025 revenue cell from the financial table.

---

# LONG DOCUMENTS

For a very long source:

1. identify keywords relevant to the question;
2. locate the relevant sections;
3. extract only the necessary passages;
4. produce the corresponding evidence;
5. discard irrelevant sections.

Never increase the amount of transmitted text merely because the source is long.

---

# EXTRACTS AND CONTEXT

Extracts must be short enough to control context usage while remaining sufficient to preserve meaning.

Do not remove information necessary to correctly interpret a figure, date, statement, or claim.

When surrounding context is required to avoid misinterpretation, retain only the minimum necessary context.

---

# NUMBERS AND DATES

For quantitative information, preserve whenever available:

- value;
- unit;
- period;
- date;
- scope;
- currency;
- source.

Never strip a value of its unit or time period.

Bad:

> 4.2

Good:

> €4.2 billion in revenue in 2025.

---

# SOURCE STATEMENTS

When a source makes a claim that is not an independently established fact, preserve it as a source statement.

Example:

Claim:
The company states that its product reduces costs by 30%.

Do not automatically transform it into:

> The product reduces costs by 30%.

The nature of the information must remain explicit.

---

# CONTRADICTIONS

If two sources provide incompatible information:

- preserve both;
- identify the sources;
- do not decide which is correct;
- explicitly pass the contradiction to the Researcher.

Format:

## Contradiction

Source A:
[claim]

Source B:
[incompatible claim]

Status:
Unresolved

Do not resolve the contradiction using external knowledge.

---

# DEDUPLICATION

If multiple sources repeat exactly the same information:

- create one evidence item when possible;
- associate multiple sources with that evidence when they provide independent confirmation.

Do not repeatedly transmit identical content.

---

# INFORMATION NOT FOUND

If important information cannot be found after a reasonable search:

add:

## Not Found

[Information sought]

Do not invent a replacement value.

Do not use an unsupported approximation.

---

# CONFIDENCE

Confidence describes how well the evidence is established, not absolute truth.

Use:

high:
- primary or highly reliable source;
- explicit information;
- sufficient context.

medium:
- reliable source but indirect information or limited context.

low:
- secondary or ambiguous source;
- information that is difficult to verify.

Do not use confidence to resolve contradictions.

---

# OUTPUT FORMAT

Return exactly:

# RESEARCH EVIDENCE

## Question

[question or sub-question]

## Sources

### Source S1

Name:
[name]

URL:
[URL]

Date:
[date]

Type:
[type]

Relevance:
[reason for selection]

### Source S2

[...]

## Evidence

### E1

Claim:
[claim]

Evidence:
[short extract or precise data]

Source:
[S1]

URL:
[URL]

Date:
[date]

Confidence:
[high / medium / low]

### E2

[...]

## Contradictions

[contradictions]

## Not Found

[important information not found]

## Limitations

[relevant limitations]

## Handoff

This document contains only the evidence required by the Researcher.

The full contents of the consulted sources are not transmitted.

---

# PROHIBITIONS

The skill must never:

- reproduce an entire Web page;
- pass an entire Web page to the Researcher;
- pass irrelevant search results to the Researcher;
- analyze findings;
- make recommendations;
- produce general conclusions;
- resolve contradictions;
- invent data;
- fill missing information using general knowledge;
- use an unconsulted source;
- unnecessarily exceed the context budgets.

---

# EXTRACTION VS. ANALYSIS

Extraction is allowed:

> The source states X.

Analysis is not allowed:

> This shows that the company is probably struggling.

Extraction is allowed:

> The company reports 18% growth.

Analysis is not allowed:

> This growth proves that its strategy is effective.

The first level belongs to the Researcher.

The second belongs to the Analyst.

---

# STOPPING CONDITION

Stop when:

- the required information has been researched;
- relevant sources have been verified;
- the main evidence has been extracted;
- important contradictions have been reported;
- important missing information has been reported;
- context limits are respected.

Do not continue researching simply because additional sources exist.

Stop when the marginal informational value of another source no longer justifies its context cost.

---

# FINAL RULE

Research quality is not measured by the amount of text collected.

It is measured by:

- evidence relevance;
- traceability;
- accuracy;
- coverage of the question;
- compactness.

Objective:

MAXIMIZE INFORMATION VALUE PER TOKEN.
