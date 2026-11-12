
# Testing out Spec Kit Development

 this project is to test out using the spec kit workflow for development. 



Notes: 

When I generated a readme for the first time then some of the context of my conversation with Github Copilot was included - notably the question of versioning being automatically done for each speckit artifact or if it was based on my git commits. 

- initial constitution: generated while project was blank / just initiated. Did a great job actually at an initial pass using just the template and just the directory name. Updated after - only took about 20 credits.

---------- keeping below as generated for historical context

# RAG System with Spec Kit

A Retrieval-Augmented Generation (RAG) project scaffold managed with Spec Kit.
This repository uses a project constitution to define technical, security, quality,
and governance requirements before implementation.

## Current Status

- Spec Kit initialized
- Project constitution defined in `.specify/memory/constitution.md`
- Feature specification/planning/implementation artifacts are generated via Spec Kit commands

## Prerequisites

- Node.js `<= 22.0.0`
- Git
- Spec Kit CLI available in your environment

## Project Governance

The source of truth for project rules is:

- `.specify/memory/constitution.md`

Key enforced expectations include:

- Express.js backend standard
- No secrets in source code; local `.env` usage for this PoC
- Secret scanning before commits
- No PII logging
- Minimum 80% test coverage
- WCAG 2.1 AA accessibility target

## Getting Started

1. Clone the repository.
2. Ensure Node version is `<= 22.0.0`.
3. Create a local `.env` file for secrets (do not commit it).
4. Start feature workflow with Spec Kit.

## Spec Kit Workflow

Typical flow:

1. `/speckit-specify` – create/update feature spec
2. `/speckit-clarify` – resolve ambiguities
3. `/speckit-plan` – produce implementation plan and design artifacts
4. `/speckit-tasks` – generate executable task list
5. `/speckit-implement` – execute tasks
6. `/speckit-converge` – reconcile implementation vs spec/plan/tasks

## Versioning & History

- Constitution semantic version is tracked inside `.specify/memory/constitution.md`.
- File history is tracked through Git commits.

## Notes

- This repository currently contains planning/governance scaffolding and is ready for feature specification and implementation.
