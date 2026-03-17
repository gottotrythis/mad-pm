---
applyTo: "**"
---

# AI / ML / GenAI Domain Instructions

Apply this overlay when a task is classified as AI, ML, or GenAI product work.

Load this file alongside `project.instructions.md` for all AI/ML work.

---

## Problem framing rules

- Always start with the **user problem** — not the solution technology.
- Require a clear statement of why AI (vs deterministic logic or simpler automation) is appropriate.
- Do not accept "use AI" or "use an LLM" as sufficient product justification.
- Define what "wrong" looks like and what the consequences of model error are before design begins.
- Use the `ai-spec-writing` skill to structure any vague AI ask into a product spec.

---

## Model and inference rules

- Identify: model family, provider (OpenAI, Anthropic, Azure OpenAI, self-hosted), API vs SDK mode, and version pinning strategy.
- Flag cost-per-call, token budget, and total monthly cost implications upfront.
- Require explicit model versioning — no implicit dependency on "latest" or un-pinned endpoints.
- Define fallback / degraded-mode behavior for:
  - Model unavailability (provider outage)
  - Rate limit exceeded
  - Latency SLA breach
  - Budget threshold hit

---

## Prompt engineering rules

- Keep all prompts version-controlled alongside application code — not hardcoded in notebooks or ad-hoc strings.
- Treat prompt changes as code changes: they require review and re-evaluation before deployment.
- Clearly separate: system prompt, user turn, assistant turn, and few-shot examples.
- Flag prompt injection risk for any workflow that incorporates external or user-controlled content into a prompt.
- Never include secrets, PII, or credentials in prompt templates.

---

## RAG rules

- Use the `rag-design` skill for any retrieval-augmented generation work.
- Define before building:
  - Source inventory (which documents, databases, or APIs)
  - Ingestion and refresh cadence
  - Chunking and metadata strategy
  - Ranking and retrieval approach
  - Citation and grounding policy
- Define no-result and low-confidence behavior explicitly — do not assume the model will handle it gracefully.
- Treat retrieval failures as first-class failure modes: test for empty results, stale results, and contradictory sources.

---

## Evaluation rules

- Use the `eval-design` skill for all AI systems approaching release.
- No release recommendation without defined numeric or bounded acceptance thresholds.
- Require **offline evals** before any online deployment.
- Require adversarial / edge case coverage in the eval suite.
- Define a regression suite before first production release — every subsequent change must not degrade it.
- Separate product success metrics from model accuracy metrics from operational metrics.

---

## Safety and observability rules

- Identify all user-visible failure modes and how they are surfaced (error message, fallback, escalation).
- Define monitoring requirements before release:
  - Token usage and cost per task
  - Latency P50/P90/P99
  - Error rate and timeout rate
  - Safety trigger rate (if using guardrails)
  - Retrieval quality signals (if using RAG)
- Set explicit kill-switch or circuit breaker criteria — what metric value triggers a rollback.
- Flag any workflow where personally identifiable information is ingested by a model: document data handling, retention, and deletion behavior.

---

## Agentic / multi-agent rules

- Document the agent graph explicitly: roles, tools available to each agent, handoff conditions, and termination conditions.
- Identify human-in-the-loop checkpoints: where does a human need to approve or redirect?
- Test for agent loop and infinite recursion conditions before release.
- Define max token budget and execution time limit per agent run.
- Never allow agents to make irreversible external actions (send emails, modify production data, push code) without an explicit human approval gate unless explicitly authorized in the spec.
- Log all agent decisions, tool calls, and intermediate reasoning for debugging and audit.

---

## Data and privacy rules

- Identify all training, fine-tuning, and inference data sources.
- Do not use production user data for model training without explicit consent and legal review.
- Identify whether the system stores any model inputs or outputs — if yes, with what retention policy.
- Flag re-identification risks when combining model outputs with other data sources.

---

## Handoff triggers (when to escalate)

Invoke `eval` agent when:
- An AI feature is approaching release and thresholds are not yet defined
- Regression behavior is unknown after a prompt or model change

Invoke `ai-pm` agent when:
- The ask is solution-first and the user problem is unclear
- KPIs, non-goals, and failure behavior are not yet articulated
