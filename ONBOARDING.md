# Onboarding

This repository is designed as an AI Product Manager starter workspace.

## What lives here

- `.github/agents/`: role definitions for structured handoffs
- `.github/instructions/`: baseline and domain-specific operating rules
- `knowledge/`: reusable product context and reference assets
- `projects/`: active and archived project work
- `memory/`: lightweight running context across weeks and decisions
- `templates/`: ready-to-use delivery templates
- `output/`: generated artifacts that should not become source-of-truth

## Suggested first-run flow

1. Read `README.md` for the repo map.
2. Read `AGENTS.md` for routing and handoff patterns.
3. Read `.github/instructions/project.instructions.md`.
4. If the work is AI, also read `.github/instructions/ai-ml.instructions.md`.
5. Start a new initiative under `projects/incubation/<project-slug>/`.
6. Copy the relevant starter files from `knowledge/_templates/` and `templates/`.

## Working model

- Keep reusable thinking in `knowledge/`.
- Keep project-specific artifacts in `projects/`.
- Keep durable summaries in `memory/`.
- Keep generated one-off outputs in `output/`.

## Naming guidance

- Prefer kebab-case for folders and files.
- Use one folder per initiative under `projects/`.
- Keep raw research, strategy docs, and deliverables separated inside each project.
