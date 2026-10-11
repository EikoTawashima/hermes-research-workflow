# Architecture

## Overview

Hermes Research Workflow is a skill-driven, multi-agent research workflow designed for Hermes CLI.

The project uses specialized agents, defined through natural-language instructions in their respective `SKILL.md` files, to transform an initial research topic into a structured report that can be published to an Obsidian vault.

Rather than relying on a single agent to perform every task, the workflow separates research, analysis, critical review, coordination, and publication into distinct responsibilities.

## Design Principles

The workflow is built around five principles:

- **Separation of responsibilities:** Each agent has a specific role and set of objectives.
- **Structured research:** Information gathering and analysis are handled as distinct stages.
- **Critical review:** Research findings and conclusions are reviewed before publication.
- **Knowledge preservation:** Final reports are intended to be stored in Obsidian for future reference.
- **Skill-driven behavior:** Agent responsibilities and instructions are defined in natural language through `SKILL.md` files.

## Agent Roles

### 1. Manager

The Manager orchestrates the research workflow and explicitly invokes the specialized agents.

Its responsibilities include:

- Understanding and organizing the initial research request.
- Calling the Researcher to gather relevant information.
- Calling the Analyst to process the collected findings.
- Calling the Critic to review and amend the analysis.
- Coordinating the progression of the workflow.
- Passing the resulting content to the Obsidian Publisher for publication.

The Manager is responsible for coordinating the agents and maintaining consistency across the research process. Each specialized agent performs its assigned task according to the instructions defined in its `SKILL.md` file.

### 2. Researcher

The Researcher gathers information relevant to the research topic.

Its intended responsibilities include:

- Identifying relevant online sources.
- Collecting information related to the research objectives.
- Extracting relevant facts, claims, and supporting evidence.
- Preserving source references so that findings can be checked.
- Identifying gaps or uncertainties in the available information.

The objective is to provide the other agents with a useful body of sourced information, rather than an unsupported summary.

### 3. Analyst

The Analyst processes the information gathered during research.

Its intended responsibilities include:

- Organizing the collected findings.
- Identifying patterns, relationships, and relevant differences.
- Comparing information from different sources.
- Distinguishing evidence from interpretation.
- Developing conclusions supported by the available information.

The Analyst transforms collected information into a coherent analysis.

### 4. Critic

The Critic reviews and amends the analysis produced by the Analyst.

Its responsibilities include:

- Identifying unsupported claims and logical gaps.
- Highlighting contradictions and missing context.
- Challenging conclusions that go beyond the available evidence.
- Identifying weaknesses in the reasoning.
- Amending the analysis to address identified issues and improve its quality.

The Critic's role is to improve the existing analysis. It does not independently restart the research process or trigger another research cycle. Its contribution is an amended analysis that can be passed to the next stage of the workflow.

Critical review helps improve the quality of the report, but it does not guarantee that every error will be detected.

### 5. Obsidian Publisher

The Obsidian Publisher integrates the analysis report into the existing Obsidian vault.

Rather than saving every report to a single predefined location, the agent takes the vault's organization into account and selects a destination based on the nature of the research topic.

Its responsibilities include:

- Receiving the analysis report produced by the research workflow.
- Taking the existing vault structure into account.
- Identifying the appropriate destination folder based on the subject of the research.
- Adding the report to the relevant location in the vault.
- Preserving the vault's organizational conventions as much as possible.

For example, when the research focuses on an organization, the agent places the report in the `Organization` folder.

This approach helps keep research results organized within the existing knowledge base instead of creating a disconnected collection of reports.

The Obsidian Publisher is therefore responsible not only for publishing the report, but also for integrating it into the vault's existing information architecture.

## Obsidian Vault Organization

The Obsidian Publisher integrates research reports into the existing vault structure. It determines the appropriate destination based on the subject of the research and the organization of the vault.

The vault contains five main categories:

| Research subject | Destination folder |
|---|---|
| Organizations | `Organizations/` |
| Persons | `Persons/` |
| Places | `Places/` |
| Technologies | `Technologies/` |
| Hardware | `Hardware/` |

The Publisher uses these categories to organize research reports according to their primary subject.

For example, a report investigating a company or institution belongs in `Organizations/`, while research about a person belongs in `Persons/`.

This organization allows research outputs to become part of a structured knowledge base rather than remaining isolated documents in a generic reports directory.

When a research topic spans multiple categories, the Publisher should use the most relevant destination according to its instructions and the context of the research.

## High-Level Architecture

The workflow can be understood as five functional stages:

1. **Coordination:** The Manager organizes the research request.
2. **Information gathering:** The Researcher collects relevant evidence.
3. **Analysis:** The Analyst synthesizes the collected information.
4. **Critical review:** The Critic evaluates the analysis and identifies weaknesses.
5. **Publication:** The Obsidian Publisher prepares the final report for storage.

The Manager coordinates these stages. The exact execution order, handoff format, and conditions for repeating a stage are defined by the agent instructions and the orchestration implemented in the project.

## Information Flow

The expected information flow is:

- The initial research request provides the starting point.
- Research findings provide the evidence base for analysis.
- The analysis provides the main arguments and conclusions for review.
- The Critic's feedback identifies corrections or limitations to address.
- The reviewed report is passed to the publication stage.
- The final Markdown document is stored in Obsidian.

Information should retain its context as it moves between agents. In particular, source URLs, uncertainty, and limitations should not be lost during summarization.

## Reliability and Limitations

The workflow aims to improve research quality through specialization and review. However, several limitations remain inherent to research performed with language models and online sources:

- Online information may be incomplete, outdated, or incorrect.
- Sources may disagree or repeat the same underlying information.
- Agents may overlook relevant evidence or misinterpret a source.
- Critical review may fail to identify some errors.
- Publication to Obsidian does not independently validate the report.

The final report should therefore preserve source references and clearly communicate significant uncertainties.

## Implementation Notes

This document describes the intended architecture at a conceptual level. The following details should be documented once verified against the actual implementation:

- How Hermes CLI discovers and invokes each skill.
- How the Manager coordinates the agents.
- The format used to exchange intermediate results.
- Whether the Critic can trigger another research or analysis pass.
- How failures and incomplete research are handled.
- How the Obsidian destination and publication format are selected.

These details should reflect the actual `SKILL.md` instructions and implementation rather than assumptions about the runtime.


