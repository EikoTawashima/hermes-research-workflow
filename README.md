# Hermes Research Workflow

From web research to critical analysis and lasting knowledge — powered by natural-language agent skills.

**A skill-driven, multi-agent research workflow for Hermes CLI — from web research and critical analysis to a structured knowledge base in Obsidian.**

Hermes Research Workflow is a collection of specialized agent skills defined in natural language through `SKILL.md` files.

Optimized and tested for Hermes CLI, the workflow coordinates five specialized roles to transform a research question into a structured, critically reviewed report that can be added to an Obsidian vault.

Rather than relying on a collection of hard-coded Python agents, this project uses explicit natural-language skill definitions to describe agent responsibilities and guide the research process.

## Overview

Research involves more than collecting links or summarizing web pages. Useful research requires gathering relevant sources, synthesizing findings, challenging assumptions, and preserving the results in a knowledge base.

This project brings those stages together in a skill-driven workflow designed for Hermes CLI.

## Agent Architecture

The workflow is organized around five specialized agent roles.

| Agent | Responsibility |
|---|---|
| **Manager** | Coordinates the workflow, delegates tasks, and manages the overall research process |
| **Researcher** | Searches the web, gathers relevant information, and records source references |
| **Analyst** | Structures findings, compares information, and develops a coherent synthesis |
| **Critic** | Challenges conclusions, identifies contradictions, and highlights gaps or uncertainty |
| **Obsidian Publisher** | Formats the final report and integrates it into an Obsidian knowledge base |

Each agent's behavior is defined by its corresponding `SKILL.md` file.

## Research Workflow

The intended workflow follows these stages:

1. **Research request** — define the question, topic, and scope.
2. **Information retrieval** — collect relevant information from web sources.
3. **Analysis** — organize findings, compare claims, and identify key insights.
4. **Critical review** — examine assumptions, inconsistencies, evidence quality, and unresolved questions.
5. **Report generation** — consolidate the research and critical review into a structured document.
6. **Knowledge integration** — save the report to the configured Obsidian vault.

The Manager coordinates the workflow according to the instructions and execution behavior configured for Hermes CLI.

## Design Principles

### Skill-driven agent behavior

Agent responsibilities are expressed in natural language using `SKILL.md` files. This makes the workflow inspectable and allows individual skills to be reviewed, refined, and version-controlled.

### Specialized responsibilities

Research, analysis, critical review, and publication are separated into distinct roles to make the workflow easier to understand and maintain.

### Critical review as a dedicated stage

The workflow includes an explicit review stage rather than treating the first generated synthesis as the final answer.

### Local-first experimentation

The workflow is optimized and tested for Hermes CLI in the author's environment. Local model execution depends on the selected Hermes configuration and inference backend.

### Persistent knowledge

Research outputs can be preserved as Markdown reports in Obsidian, making them available for later retrieval, linking, and further investigation.

## Requirements

- Hermes CLI, configured according to its official documentation
- The model and inference configuration used by your Hermes environment
- The required agent skills and their dependencies
- Internet access and the web research capabilities required by the workflow
- An Obsidian vault with an accessible destination path

Additional requirements may apply depending on the tools and integrations used by the individual skills.

## Documentation

The project documentation covers the architecture, execution workflow, configuration, evaluation, and security considerations.

- [Architecture](docs/architecture.md) — Agent responsibilities, system design, and data flow.
- [Workflow](docs/workflow-diagram.png) — End-to-end research process.
- [Configuration](docs/configuration.md) — Hermes CLI setup, model configuration, and Obsidian integration.
- [Evaluation](docs/evaluation.md) — Test methodology, observed results, and known limitations.
- [Security](docs/security.md) — Untrusted web content, access permissions, and data protection.

## Repository Structure

```text
skills/
├── research-manager/SKILL.md
├── web-researcher/SKILL.md
├── research-analyst/SKILL.md
├── critical-reviewer/SKILL.md
└── obsidian-publisher/SKILL.md

docs/
examples/
```

Adapt this example to the actual directory structure of the repository.

## Installation and Configuration

This project is designed for Hermes CLI.

1. Clone the repository.
2. Review the individual `SKILL.md` files.
3. Install or link the skills using the discovery and installation mechanism supported by your Hermes CLI version.
4. Configure the required research tools and Obsidian destination.
5. Verify that Hermes can discover the skills and execute the workflow.

Follow the installation instructions in the documentation for the Hermes CLI version you use. The exact installation commands and skill paths depend on your environment.

## Usage

Start Hermes CLI using your normal workflow, then invoke the research manager.

Provide a research question and allow the configured agents to carry out the research, analysis, critical review, and report publication stages.

See the individual skill definitions and the documentation for the exact invocation syntax.

## Example Output

A generated research report may include:

- Research question and scope
- Key findings and supporting sources
- Analysis and synthesis
- Critical review and potential contradictions
- Uncertainties and limitations
- Conclusions and follow-up questions

See `examples/` for a sample report.

Only include example outputs that accurately represent reports generated by the workflow.

## Testing

The workflow has been tested and optimized for Hermes CLI using a locally-hosted LLM.

Testing and optimization are environment-dependent. Model choice, inference settings, available tools, and Hermes CLI versions may affect execution behavior and output quality.

Document the tested environment, model configuration, representative tasks, and known limitations to help others reproduce your results.

## Security and Limitations

Web content should be treated as untrusted input. Instructions found in retrieved pages must not automatically override the intended responsibilities or security constraints of the workflow.

Review the skills and their tool permissions before using them with sensitive data or granting access to a personal Obsidian vault.

Local model execution does not necessarily mean that the complete workflow is offline: Internet research requires network access, and configured external services may process data remotely.

Critical review can identify potential weaknesses, but it does not guarantee that every factual error or unsupported claim will be detected. Important findings should still be verified against their sources.

## Roadmap

- [ ] Document the tested Hermes CLI environment.
- [ ] Publish an architecture diagram and workflow description.
- [ ] Add a representative end-to-end research example.
- [ ] Document skill installation and configuration.
- [ ] Record known limitations and troubleshooting guidance.
- [ ] Add repeatable evaluation tasks for research quality and source traceability.

## Contributing

Issues, suggestions, and improvements to individual skills are welcome.

When proposing changes, explain the intended behavior, provide a representative task where possible, and describe how the change affects the overall workflow.

## License

See `LICENSE` for the terms governing use, modification, and redistribution.

---

**Hermes CLI · Natural-language skills · Multi-agent research · Critical review · Obsidian knowledge management**
