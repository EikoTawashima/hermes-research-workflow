# Research Workflow

## Overview

Hermes Research Workflow turns a research request into a structured report intended for storage in Obsidian.

The process is organized around five specialized roles:

**Manager → Researcher → Analyst → Critic → Obsidian Publisher**

The Manager coordinates the process, while the other agents contribute specific capabilities at different stages.

The sequence below describes the intended end-to-end workflow. The precise execution order and any review loops depend on the actual agent instructions.

## Step 1 — Define the Research Objective

The process starts with a research request.

The request should describe the topic to investigate and, where relevant, the questions to answer, the desired level of detail, and any constraints.

The Manager organizes the request into research objectives that can guide the subsequent work.

A well-defined objective helps keep the research focused and makes it easier to evaluate whether the final report answers the original question.

**Expected outcome:** A clear research objective and scope.

## Step 2 — Gather Information

The Researcher investigates the topic using available online information sources.

This stage focuses on collecting relevant evidence rather than immediately producing final conclusions.

Depending on the topic and available sources, the research may include:

- Finding relevant webpages and documents.
- Extracting facts, arguments, and supporting details.
- Recording source URLs and other useful references.
- Identifying conflicting statements or missing information.
- Noting uncertainties that require further investigation.

Sources should be treated as evidence to evaluate, not as automatically reliable statements.

**Expected outcome:** A collection of relevant findings with traceable sources and identified uncertainties.

## Step 3 — Analyze the Findings

The Analyst transforms the collected information into a structured analysis.

This stage may include grouping related findings, comparing different perspectives, identifying patterns, and evaluating how the evidence relates to the original research objectives.

The analysis should distinguish between:

- Information directly supported by sources.
- Interpretations derived from that information.
- Conclusions that remain uncertain.
- Questions that cannot be answered confidently with the available evidence.

The quality of the analysis depends on both the relevance of the sources and the care taken when interpreting them.

**Expected outcome:** A coherent analysis with evidence-based conclusions and explicit limitations.

## Step 4 — Critically Review the Analysis


The Critic reviews and amends the Analyst's work before publication. It identifies weaknesses, unsupported claims, inconsistencies, and missing context, then incorporates appropriate corrections into the analysis.

The Critic does not initiate another research cycle. The amended analysis is passed forward as part of the existing workflow, coordinated by the Manager.

## Step 5 — Prepare and Publish the Report

O## Step 5 — Integrate the Report into Obsidian

After the Critic has amended the analysis, the Manager passes the resulting report to the Obsidian Publisher.

The Publisher examines the research topic and takes the vault's existing folder structure into account to determine where the report should be added.

The vault is organized into five main categories:

- `Organizations/` — Research about organizations, companies, institutions, and similar entities.
- `Persons/` — Research focused on individuals.
- `Places/` — Research about geographical locations and places.
- `Technologies/` — Research about technologies, technical concepts, and technological developments.
- `Hardware/` — Research about physical computing equipment and other hardware.

These descriptions indicate the intended scope of each category; the Publisher's actual classification behavior is defined by its `SKILL.md`.

### Publication Process

1. The Publisher receives the analysis report.
2. It identifies the report's primary research subject.
3. It considers the existing vault structure and selects the most appropriate category.
4. It adds the report to the corresponding folder.
5. It preserves the report's relevant findings and source references.

For example, a report about an organization is added to `Organizations/`, while a report about a specific technology is added to `Technologies/`.

The goal is to maintain a coherent and navigable knowledge base in which research is organized by subject.

**Expected outcome:** The report is integrated into the appropriate folder of the existing Obsidian vault.

## Workflow Quality Criteria

The workflow should be evaluated against the following criteria:

| Criterion | What to look for |
|---|---|
| Relevance | The report answers the original research question. |
| Traceability | Important claims can be traced to their sources. |
| Analytical quality | Conclusions are supported by the evidence. |
| Critical depth | Weaknesses and alternative interpretations are considered. |
| Transparency | Uncertainties and limitations are made explicit. |
| Readability | The report is organized and easy to navigate. |
| Publication integrity | The output is saved to the intended Obsidian location. |

## Important Considerations

A multi-agent workflow does not automatically guarantee more accurate results. Agents may share the same mistaken assumptions, rely on overlapping sources, or fail to detect an error during review.

For this reason, the workflow should prioritize traceable evidence, explicit uncertainty, and a clear distinction between sourced facts and interpretation.

The final report should be treated as a structured research aid, not as a substitute for independent verification when decisions require a high level of confidence.


