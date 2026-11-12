<!--
Sync Impact Report
- Version change: 1.0.0 -> 1.1.0
- Modified principles:
	- IV. Observability and Traceability by Default -> IV. Observability and Operational Transparency
	- V. Security and Data Minimization -> V. Security Baseline and Data Protection
- Added sections:
	- Tech Standards
	- Security Requirements
	- Performance and Scalability
	- Coding Standards
	- Compliance and Governance
- Removed sections:
	- Technical Standards
	- Delivery Workflow
	- Governance
- Follow-up TODOs:
	- None
-->

# RAG System Constitution

## Core Principles

### I. Retrieval Accuracy First
All user-facing responses MUST be grounded in retrieved sources from the approved knowledge base.
The system MUST distinguish grounded facts from model reasoning and MUST reject or flag outputs
when supporting retrieval evidence is missing. Rationale: retrieval-grounded behavior is the core
quality and trust mechanism of a RAG system.

### II. Deterministic Interfaces and Contracts
Every pipeline stage (ingestion, indexing, retrieval, generation, and evaluation) MUST expose
explicit input/output contracts and stable schemas. Contract changes MUST be versioned and
documented before release. Rationale: deterministic boundaries reduce regressions and make the
system testable as independent components.

### III. Test-First for Critical Paths (NON-NEGOTIABLE)
Changes to chunking, embedding, retrieval ranking, prompt orchestration, or response post-processing
MUST include tests before implementation is considered complete. At minimum, each change MUST have
unit coverage and one behavior-level assertion that protects against hallucination regressions.
Rationale: RAG quality failures are often silent without targeted tests.

### IV. Observability and Operational Transparency
The system MUST emit structured logs and trace IDs across retrieval and generation steps so any
answer can be traced to query, retrieved passages, model configuration, and output metadata.
The system MUST log query activity and response-time metrics for each request, while ensuring
restricted data is never logged. Rationale: traceability is required for debugging, quality
improvement, and operational governance.

### V. Security Baseline and Data Protection
Only approved data sources may be indexed, and sensitive data MUST be excluded, masked, or
permission-scoped before ingestion. Secrets MUST never be hardcoded and MUST be loaded from secured
configuration channels. Rationale: RAG systems amplify data exposure risk if ingestion controls are
not strict.

## Tech Standards

- Runtime MUST use Node.js version 22.0.0 or lower.
- Backend services MUST be implemented with Express.js.
- Secrets MUST NOT be stored in source code and MUST be kept in a local `.env` file for this
  proof of concept.
- Secrets MUST be scanned before every commit to Git.

## Security Requirements

- Secrets MUST NOT appear in source code or committed configuration files.
- Personally identifiable information (PII) MUST NOT be logged.

## Performance and Scalability

- Any request expected to exceed 5 seconds MUST be executed asynchronously.
- Any request that exceeds 5 seconds MUST surface a progress bar to the user.

## Coding Standards

- Project test coverage MUST be at least 80%.
- Every function and every API endpoint MUST include comments documenting purpose and behavior.
- Logging MUST be implemented for executed queries and response time per request.

## Compliance and Governance

This constitution supersedes conflicting local practices for this repository. Amendments require a
documented proposal, explicit approval by project maintainers, and an impact summary describing
required migrations or workflow updates.

The project MUST comply with all applicable local and international standards that protect user data.
Accessibility requirements MUST meet WCAG 2.1 Level AA.
When accessibility features are implemented, details MUST be appended to `accessibility-report.txt`.
Every implementation stage MUST generate a high-level executive summary in no more than four
sentences.

Versioning policy for this constitution follows semantic versioning:
- MAJOR: incompatible governance changes or principle removal/redefinition.
- MINOR: new principle/section or materially expanded guidance.
- PATCH: clarifications, wording improvements, or non-semantic refinements.

Compliance review is mandatory during specification and pull request review. Reviewers MUST verify
that proposed work satisfies all core principles and explicitly identify any exceptions with rationale.

**Version**: 1.1.0 | **Ratified**: 2026-11-11 | **Last Amended**: 2026-11-11
