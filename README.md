# MAD Stack Workspace

This repository now works as an AI PM starter workspace with two clearly separated layers:

- an operating-system layer for agents, rules, and reusable templates
- a project layer for active initiative work, research, and generated artifacts

It still supports both major domains already present in the repo:

- Salesforce loyalty management for healthcare and life sciences
- AI, ML, and GenAI product and delivery work

## Top-Level Structure

```text
.
├── AGENTS.md
├── ONBOARDING.md
├── MCP_SETUP.md
├── README.md
├── .github/
│   ├── agents/
│   ├── instructions/
│   └── skills/
├── .vscode/
│   └── mcp.json
├── knowledge/
│   ├── _templates/
│   └── examples/
├── memory/
│   ├── decisions/
│   ├── exec-updates/
│   ├── strategy-reviews/
│   └── weekly-plans/
├── templates/
├── projects/
│   └── incubation/
│       └── wtd-next-in-line/
├── output/
├── scripts/
└── datadump/
    └── README.md
```

## How To Think About The Repo

### 1. Operating system

These are the durable, reusable parts of the workspace:

- `AGENTS.md`: routing, handoffs, and agent roster
- `.github/instructions/`: baseline and domain overlays
- `.github/skills/`: specialized workflows
- `knowledge/`: repeatable PM context and reusable strategy scaffolds
- `templates/`: ready-to-fill delivery templates
- `memory/`: cross-project summaries and decision history

### 2. Project work

These are the initiative-specific parts:

- `projects/incubation/`: early discovery and framing
- `projects/active/`: execution-stage work
- `projects/archive/`: completed or paused work

Each project should get its own folder with subfolders such as:

- `documents/`
- `research/`
- `code/`
- `assets/` when needed

## Why This Is Better Than The Current Dump Model

- Reusable PM assets no longer get mixed with project-specific notes.
- New initiatives have a clear home from day one.
- Your current agent system stays intact instead of being duplicated.
- The structure matches how an AI PM actually works: strategy, discovery, decisions, evaluation, and delivery.

## Current Example Project

The existing `wtd next in line` material has been moved to:

- [`projects/incubation/wtd-next-in-line/`](/Users/vaibhavjha/Documents/mad-pm/projects/incubation/wtd-next-in-line)

This keeps the work intact while putting it in a scalable location.

## Recommended Flow For A New Project

1. Create `projects/incubation/<project-slug>/`.
2. Start with `templates/project-intake.md`.
3. Pull supporting context from `knowledge/_templates/`.
4. Route through the matching handoff path in `AGENTS.md`.
5. Save durable decisions or weekly summaries into `memory/` when they are useful beyond one project.

## Domain Guidance

- Base project guidance: `.github/instructions/project.instructions.md`
- Salesforce and healthcare overlay: `.github/instructions/sf.instructions.md`
- AI, ML, and GenAI overlay: `.github/instructions/ai-ml.instructions.md`

## Recommended Starting Point

1. Read `ONBOARDING.md`.
2. Read `AGENTS.md`.
3. Read `.github/instructions/project.instructions.md`.
4. Load the right domain overlay for the project.
5. Create or reuse a project folder under `projects/`.
