# MAD Stack Workspace

This repository provides a structured multi-agent workspace for two primary domains:

- Salesforce loyalty management for healthcare and life sciences
- AI, ML, and GenAI product and delivery work

It is designed to improve delivery quality through clear intake, planning, architecture, review, evaluation, and release handoffs.

## Repository Layout

```text
.
├── AGENTS.md
├── README.md
├── .vscode/
│   └── mcp.json
└── .github/
    ├── agents/
    │   ├── intake.agent.md
    │   ├── planner.agent.md
    │   ├── architect.agent.md
    │   ├── reviewer.agent.md
    │   ├── release.agent.md
    │   ├── sf-regulatory.agent.md
    │   ├── ai-pm.agent.md
    │   └── eval.agent.md
    ├── skills/
    │   ├── sf-loyalty-intake/skill.md
    │   ├── sf-release-readiness/skill.md
    │   ├── sf-integration-mapping/skill.md
    │   ├── ai-spec-writing/skill.md
    │   ├── rag-design/skill.md
    │   └── eval-design/skill.md
    └── instructions/
        ├── project.instructions.md
        ├── sf.instructions.md
        └── ai-ml.instructions.md
```

## How This Workspace Works

The workspace follows a role-based agent model:

1. Intake clarifies and classifies the request.
2. Planning breaks work into bounded units.
3. Architecture defines solution shape and trade-offs.
4. Domain and risk review validates compliance and quality constraints.
5. Review checks correctness, safety, and readiness.
6. Release prepares deployment, rollback, and monitoring.

For AI-heavy initiatives, evaluation is required before release.

## Standard Handoff Paths

### General Path

`intake -> planner -> architect -> reviewer -> release`

### Salesforce or Healthcare Regulated Path

`intake -> planner -> architect -> sf-regulatory -> reviewer -> release`

### AI, ML, or GenAI Path

`intake -> ai-pm -> planner -> architect -> reviewer -> eval -> release`

## Domain Guidance Files

- Base project guidance: `.github/instructions/project.instructions.md`
- Salesforce and healthcare overlay: `.github/instructions/sf.instructions.md`
- AI, ML, and GenAI overlay: `.github/instructions/ai-ml.instructions.md`

## Skills Library

### Salesforce Skills

- `.github/skills/sf-loyalty-intake/skill.md`
- `.github/skills/sf-release-readiness/skill.md`
- `.github/skills/sf-integration-mapping/skill.md`

### AI and ML Skills

- `.github/skills/ai-spec-writing/skill.md`
- `.github/skills/rag-design/skill.md`
- `.github/skills/eval-design/skill.md`

## Editing and Quality Expectations

- Prefer small, reviewable changes over broad edits.
- State assumptions explicitly and avoid inventing requirements.
- Include testing implications with implementation guidance.
- Include monitoring and rollback implications with release guidance.
- Route sensitive Salesforce healthcare changes through regulatory review.
- Route AI release decisions through explicit evaluation gates.

## Workspace MCP Configuration

The workspace-level MCP configuration is located at:

- `.vscode/mcp.json`

Use it to define and standardize MCP server setup for this repository.

## Recommended Starting Point

If you are new to this workspace:

1. Read `AGENTS.md` for routing and handoff sequences.
2. Read `.github/instructions/project.instructions.md`.
3. Load the relevant domain overlay (`sf.instructions.md` or `ai-ml.instructions.md`).
4. Use the matching skill file before generating deliverables.