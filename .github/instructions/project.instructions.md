# Project Instructions for MAD Stack

This workspace uses a multi-agent development model.

These instructions apply to all custom agents, reusable skills, and planning/review workflows in this repository.

## Core operating principles

1. Prefer structured execution over improvisation.
2. Never jump from a vague request directly into large-scale implementation.
3. Separate intake, planning, architecture, implementation, review, evaluation, and release concerns.
4. Keep work bounded. Favor small, reviewable units over broad edits.
5. State assumptions explicitly. Do not invent missing requirements.
6. Identify what must not change before proposing changes.
7. Prefer traceability, maintainability, and low blast radius over cleverness.
8. For regulated, privacy-sensitive, or enterprise-impacting work, require stronger review and release discipline.

## Domain modes

This workspace supports two primary domains:

### A. Salesforce loyalty management for life sciences / healthcare
Optimize for:
- traceability
- controlled changes
- privacy and audit awareness
- explicit release readiness
- conservative risk handling

### B. AI / ML / GenAI product and solution development
Optimize for:
- problem clarity
- measurable product outcomes
- evaluation rigor
- safety and observability
- cost/latency awareness
- disciplined multi-agent orchestration

## Execution rules

- Do not make broad code changes without a bounded plan.
- Do not self-approve authored work.
- Do not present hand-wavy recommendations as release-ready.
- Do not treat "AI" as a sufficient justification for a feature.
- Do not assume data is non-sensitive.
- Always identify dependencies, risks, and rollback implications.
- Always include testing implications in implementation guidance.
- Always include monitoring implications in release guidance.

## Planning rules

A good plan must include:
- the objective
- in-scope boundaries
- out-of-scope boundaries
- assumptions
- dependencies
- risks
- acceptance criteria
- recommended handoff

If these are missing, the plan is incomplete.

## Review rules

A good review must:
- identify blockers separately from non-blockers
- cite the reason the issue matters
- identify testing gaps
- identify operational gaps
- reject unsafe ambiguity

## AI system rules

For AI/ML/GenAI work:
- define why AI is needed
- define non-AI alternatives where relevant
- define evaluation criteria before release
- define failure behavior
- define monitoring and fallback behavior
- define user-visible limitations where necessary

## Salesforce rules

For Salesforce healthcare/loyalty work:
- call out object/field/flow/Apex/LWC/integration impact explicitly
- flag data sensitivity and access concerns
- identify validation and deployment implications
- favor traceability and release discipline

## Handoff guidance

Use this rough handoff sequence unless the task clearly needs a different order:

- intake -> planner -> architect -> domain/risk review -> builder -> reviewer -> release

For AI-heavy work, insert evaluation before release.

## Output expectations

Prefer structured markdown with clear sections.

When producing plans, specs, reviews, evals, or release packs, always include:
- summary
- risks
- assumptions
- next handoff recommendation

## Memory usage

When stable patterns or recurring lessons emerge, summarize them in a reusable form suitable for:
- memory
- skills
- templates
- future planning guidance