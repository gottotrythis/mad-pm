# AI Spec Writing Skill

Use this skill when:
- the request is about AI, ML, GenAI, assistants, copilots, RAG, or agentic systems
- the ask is solution-first and not yet a real product spec
- KPIs, non-goals, and acceptance criteria are missing
- someone says "use AI" without defining the problem being solved

---

## Skill objectives

- Convert a vague AI ask into a rigorous product specification
- Clarify the real user problem and current workflow
- Determine whether AI is justified vs deterministic alternatives
- Define measurable outcomes, non-goals, and failure behavior
- Prepare a handoff to architecture or evaluation

---

## AI justification framework

Ask these questions before approving AI as the solution:

| Question | If NO → consider |
|---|---|
| Is there genuine ambiguity or judgment the AI handles better than rules? | Deterministic logic / rules engine |
| Would a search or filter solve the problem sufficiently? | Semantic search without LLM generation |
| Does the output need to be grounded in specific documents or data? | RAG (not bare LLM) |
| Is human error rate the bottleneck this is solving? | Process improvement first |
| Can the failure cost be tolerated if the model is wrong 5–20% of the time? | Human-in-the-loop or rules fallback needed |

---

## Spec variants to distinguish

### LLM-only spec
- Focus: prompt design, input/output schema, model selection, latency/cost
- Key risk: hallucination, prompt injection, cost overrun

### RAG spec
- Add: source inventory, ingestion/refresh cadence, chunking, metadata, retrieval strategy, citation policy
- Use the `rag-design` skill in parallel
- Key risk: retrieval failure, stale content, no-result behavior

### Agentic spec
- Add: agent graph, tools available, handoff conditions, human approval gates, max token budget, loop detection
- Key risk: runaway agent, unauthorized actions, unpredictable multi-step behavior

### Fine-tuning / ML pipeline spec
- Add: training data provenance, labeling methodology, evaluation dataset, model versioning, serving infrastructure
- Key risk: data leakage, distribution shift, silent model degradation

---

## Required output

1. Problem statement (user problem, current workflow, business objective)
2. Users and use cases
3. Why AI / why not AI (explicit justification)
4. Scope and non-goals
5. Expected system behavior (happy path + failure paths)
6. Success metrics (product KPIs, model KPIs, operational KPIs)
7. Risks (safety, cost, latency, compliance, UX)
8. Evaluation needs
9. Recommended next handoff

---

## Checklist

- [ ] User problem is explicit and user-validated
- [ ] Business objective is measurable
- [ ] AI justification is stated (not assumed)
- [ ] Non-AI alternative is considered
- [ ] Non-goals are listed
- [ ] Failure behavior is described for top 3 failure modes
- [ ] Acceptable failure rate / error tolerance is defined
- [ ] Evaluation implications are included
- [ ] PHI/PII handling is addressed (if relevant)
- [ ] Model/provider assumptions are named
