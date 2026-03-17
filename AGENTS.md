# Workspace Agent Instructions

All agents in this workspace follow the rules in:

- `.github/instructions/project.instructions.md` — shared baseline for all work

Domain-specific instruction overlays (load when domain is identified):
- `.github/instructions/sf.instructions.md` — Salesforce / healthcare loyalty work
- `.github/instructions/ai-ml.instructions.md` — AI / ML / GenAI product work

**Conflict resolution order:**
1. User request wins
2. Agent-specific instructions win next
3. Domain overlay instructions apply
4. Project baseline instructions apply as floor

---

## Agent Roster

| Agent | File | Purpose |
|---|---|---|
| `intake` | `.github/agents/intake.agent.md` | Convert raw requests into structured intake briefs |
| `planner` | `.github/agents/planner.agent.md` | Break approved intake into bounded work units |
| `architect` | `.github/agents/architect.agent.md` | Design solution shape, interfaces, and trade-offs |
| `reviewer` | `.github/agents/reviewer.agent.md` | Review plans, code, tests, and release artifacts |
| `release` | `.github/agents/release.agent.md` | Prepare deployment, rollout, smoke tests, and rollback |
| `ai-pm` | `.github/agents/ai-pm.agent.md` | Convert AI/ML opportunities into rigorous specs and KPIs |
| `eval` | `.github/agents/eval.agent.md` | Design evaluation plans, thresholds, and release gates for AI systems |
| `sf-regulatory` | `.github/agents/sf-regulatory.agent.md` | Healthcare / Salesforce regulatory, privacy, and audit review |

---

## Standard Handoff Sequences

### General work
```
intake → planner → architect → reviewer → release
```

### Salesforce / healthcare regulated work
```
intake → planner → architect → sf-regulatory → reviewer → release
```

### AI / ML / GenAI product work
```
intake → ai-pm → planner → architect → reviewer → eval → release
```

### Complex AI + Salesforce work
```
intake → ai-pm → planner → architect → sf-regulatory → reviewer → eval → release
```

---

## Domain Routing

### Route to Salesforce / Healthcare path when the request involves
- Salesforce clouds, objects, Flows, Apex, LWC, reports, dashboards
- Loyalty programs, rewards, redemptions, tiering, member journeys
- Healthcare, life sciences, patients, HCPs, caregivers, field reps
- Data privacy, consent, audit controls, deployment validation

**Domain overlay:** `.github/instructions/sf.instructions.md`

**Relevant skills:**
- `.github/skills/sf-loyalty-intake/skill.md`
- `.github/skills/sf-release-readiness/skill.md`
- `.github/skills/sf-integration-mapping/skill.md`

### Route to AI / ML / GenAI path when the request involves
- Copilots, assistants, RAG, LLMs, prompts, model workflows
- ML pipelines, training, inference, feature stores, embeddings
- Agentic orchestration, tool use, multi-agent systems
- AI product specs, evaluation, safety, observability

**Domain overlay:** `.github/instructions/ai-ml.instructions.md`

**Relevant skills:**
- `.github/skills/ai-spec-writing/skill.md`
- `.github/skills/rag-design/skill.md`
- `.github/skills/eval-design/skill.md`

---

## Skill Library

| Skill | File | When to use |
|---|---|---|
| sf-loyalty-intake | `.github/skills/sf-loyalty-intake/skill.md` | Structuring Salesforce loyalty intake briefs |
| sf-release-readiness | `.github/skills/sf-release-readiness/skill.md` | SF deployment checklists and release packs |
| sf-integration-mapping | `.github/skills/sf-integration-mapping/skill.md` | Documenting SF integration contracts and field maps |
| ai-spec-writing | `.github/skills/ai-spec-writing/skill.md` | Converting vague AI asks into rigorous product specs |
| rag-design | `.github/skills/rag-design/skill.md` | Designing retrieval-augmented generation systems |
| eval-design | `.github/skills/eval-design/skill.md` | Designing AI evaluation plans and release gates |

---

## Cross-cutting rules (all agents)

- Do not self-approve authored work.
- Do not make broad changes without a bounded plan.
- State assumptions explicitly — never invent requirements.
- Identify blast radius and what must not change before proposing changes.
- Include testing implications in every implementation recommendation.
- Include monitoring implications in every release recommendation.
- Always end output with a **Recommended next handoff** section.