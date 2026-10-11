# Configuration

## Overview

Hermes Research Workflow is designed to run with Hermes CLI and uses natural-language agent instructions defined in `SKILL.md` files.

Configuration covers the runtime environment, access to research sources, agent instructions, and the destination used to publish reports in Obsidian.

This document provides a starting point for setting up the project. Exact commands and configuration options should be added after verifying them against the Hermes CLI version and the project's actual implementation.

## Prerequisites

Before using the workflow, make sure the following components are available:

- **Hermes CLI:** An installed and working environment compatible with the project's skills.
- **Agent skills:** The `SKILL.md` files defining the Manager, Researcher, Analyst, Critic, and Obsidian Publisher.
- **Research access:** The web or other information-retrieval capabilities required by the Researcher.
- **Obsidian:** An existing vault or a destination directory for generated Markdown reports.
- **Model access:** Any model or provider configuration required by the Hermes CLI environment.

The exact requirements depend on the tools and integrations used by the current version of the project.

## Project Structure

A possible repository layout is:

```text
hermes-research-workflow/
├── README.md
├── LICENSE
├── docs/
│   ├── architecture.md
│   ├── workflow.md
│   └── configuration.md
└── skills/
    ├── manager/
    │   └── SKILL.md
    ├── researcher/
    │   └── SKILL.md
    ├── analyst/
    │   └── SKILL.md
    ├── critic/
    │   └── SKILL.md
    └── obsidian-publisher/
        └── SKILL.md
```

This tree is illustrative. Adapt it to match the actual repository structure and the skill discovery conventions supported by Hermes CLI.

## Hermes CLI Setup

Install and configure Hermes CLI according to its official documentation.

Then make the project's skill instructions available through the discovery or loading mechanism supported by your installed version.

Before running the complete workflow, verify that:

- Each skill is accessible to the runtime.
- Each skill has a clear and distinct responsibility.
- The instructions describe the expected inputs and outputs.
- Required tools and permissions are available.
- The agents can follow the intended workflow without relying on undocumented assumptions.

**Version tested:** `[Add the Hermes CLI version used for testing]`

**Setup reference:** `[Add the relevant official Hermes CLI documentation link]`

Record the version and setup method that you have actually tested. Avoid assuming that skill installation or discovery works identically across versions.

## Agent Orchestration

The Manager is responsible for explicitly invoking the specialized agents. The workflow is therefore coordinated through the Manager rather than relying on the agents to independently initiate the next stage.

The intended execution sequence is:

1. The Manager invokes the Researcher.
2. The Manager invokes the Analyst using the research output.
3. The Manager invokes the Critic to review and amend the analysis.
4. The Manager passes the resulting output to the Obsidian Publisher.

Each agent's `SKILL.md` defines its responsibilities and instructions. The Manager's skill defines how the agents are coordinated.

The Critic amends the analysis but does not independently restart the research process.

When modifying the skills, keep the Manager's orchestration instructions consistent with the responsibilities and expected outputs of the other agents.

## Model and Runtime Configuration

The behavior of the workflow depends partly on the model and runtime configuration used by Hermes CLI.

Document the following settings where relevant:

| Setting | Value to document |
|---|---|
| Hermes CLI version | Tested version |
| Model/provider | Model and provider used during testing |
| Tool access | Research and other enabled tools |
| Runtime settings | Relevant execution or permission settings |
| Environment variables | Names of required variables, without secret values |

The workflow should not depend on undocumented settings where they can reasonably be made explicit.

Never commit API keys, access tokens, or other credentials to the repository. Use the appropriate local configuration or secret-management mechanism for your environment.

## Research Tool Access

The Researcher requires access to suitable information sources.

Document which research tools are expected to be available and how they are configured in your environment.

For each tool, specify:

- Its purpose in the research process.
- Whether authentication is required.
- Any relevant access limitations.
- Whether it is required or optional.

The availability of a tool should not be assumed merely because it is mentioned in a `SKILL.md` file. Confirm that the runtime can actually invoke it.

## Obsidian Integration

The Obsidian Publisher integrates research reports into an existing Obsidian vault.

The agent takes the vault's information architecture into account when determining where to add a report. The destination depends on the nature of the research topic and the folder structure available in the vault.

For example, research about an organization is added to the `Organization` folder.

### Obsidian Vault Structure

The Obsidian Publisher is designed to integrate research reports into the existing vault rather than saving every report to a single fixed output directory.

The vault uses the following folder structure:

```text
Obsidian Vault/
├── Organizations/
├── Persons/
├── Places/
├── Technologies/
└── Hardware/
```

### Destination Selection

The Publisher selects the destination folder according to the primary subject of the research.

| Category | Folder |
|---|---|
| Organizations | `Organizations/` |
| Persons | `Persons/` |
| Places | `Places/` |
| Technologies | `Technologies/` |
| Hardware | `Hardware/` |

For example, research about a company should be integrated into `Organizations/`, while research about a hardware component should be integrated into `Hardware/`.

When a topic could reasonably fit into more than one category, the Publisher follows the classification instructions defined in its `SKILL.md`.

### Access and File Handling

The Publisher must be able to access the target vault and add the report to the selected folder.

The following implementation details should be documented once verified:

- How the vault location is provided to the agent.
- How the Publisher inspects the existing folder structure.
- How report filenames are determined.
- How existing notes and filename conflicts are handled.
- What happens when the appropriate folder is missing.
- How ambiguous or cross-category topics are classified.

The folder names above describe the current vault structure. They should not be interpreted as configuration variables or automatic runtime behavior unless the implementation explicitly supports them.

### Destination Selection

The destination is determined contextually:

1. The Publisher receives the analysis report.
2. It considers the subject of the research.
3. It takes the existing vault structure into account.
4. It selects the appropriate destination.
5. It adds the report to that location.

The `Organization` folder is one example. Other destinations depend on the categories and structure of the user's vault.

### Configuration Details

Document the following details for your own setup:

- **Vault location:** The path or access mechanism used by the Publisher.
- **Folder conventions:** The existing folders and how they correspond to research topics.
- **File naming:** The convention used when adding a report.
- **Existing notes:** How the Publisher handles an existing note at the intended destination.

The destination-selection rules should reflect the actual vault structure and the instructions defined in the Publisher's `SKILL.md`.

The agent should not assume that a folder exists without checking the available structure through its configured tools. Any behavior for missing folders, ambiguous categories, or filename conflicts should be documented according to the implementation.

### Permissions and Data Integrity

The Publisher needs sufficient access to add reports to the vault. Where practical, its write access should be limited to the intended vault.

Credentials and private configuration details should not be committed to the repository. Existing notes should be handled carefully to avoid unintended overwrites or changes.

## Running a Research Session

The exact command for starting a research session depends on how the skills are exposed and invoked by Hermes CLI.

Add the verified command used by your project here:

```bash
[Replace with the actual command used to start a research session]
```

Document any required arguments, such as the research topic, output preferences, or other options supported by your implementation.

A typical session should make the following information clear:

1. The topic or question being investigated.
2. The expected output format.
3. The tools available to the agents.
4. The destination for the final report.
5. Any constraints that apply to the research.

Do not use the example above as a literal shell command; replace it with a command that has been tested in your environment.

## Troubleshooting

### A skill is not available

- Confirm that the `SKILL.md` file exists in the expected location.
- Check that its directory and metadata follow the conventions required by Hermes CLI.
- Verify that the runtime can discover or load the skill.

### Research results are incomplete

- Confirm that the required research tools are available.
- Check whether the topic and research objectives are sufficiently specific.
- Review the source coverage and limitations recorded by the Researcher.

### The final report is missing

- Check the Publisher's configured destination.
- Confirm that the runtime has write permissions.
- Review any available execution output or error messages.
- Verify that the publication step was reached.

### The report is difficult to verify

- Ensure that important findings retain their source links.
- Check that conclusions are distinguished from sourced facts.
- Confirm that the Critic's feedback and unresolved limitations are reflected where appropriate.

## Configuration Checklist

Before considering the environment ready, verify the following:

- [ ] Hermes CLI is installed and its version is recorded.
- [ ] All five agent skills are available to the runtime.
- [ ] Required research tools are configured and accessible.
- [ ] Model and provider settings have been verified.
- [ ] The Obsidian destination is configured.
- [ ] Write permissions are limited to the intended destination where practical.
- [ ] The workflow has been tested with a sample research topic.
- [ ] The final Markdown report has been checked in Obsidian.
- [ ] No credentials or sensitive local configuration files are included in the repository.

## Maintenance

Keep this document synchronized with the implementation.

Whenever the project changes, review the documented Hermes CLI version, skill locations, tool requirements, execution instructions, and Obsidian output settings.

Configuration details should describe the tested behavior of the project rather than an assumed or intended setup.


