# Evaluation Design Skill

Use this skill when:
- an AI feature needs measurable release criteria
- a prompt/RAG/agent system needs regression testing
- stakeholders are claiming quality without evidence
- pilot vs production gating must be decided
- a model, prompt, or retrieval change is being evaluated for regression

---

## Skill objectives

- Define the evaluation strategy end-to-end
- Identify failure modes and adversarial cases
- Define numeric thresholds and release gates
- Create a regression-oriented test plan
- Produce a ship / hold / pilot recommendation

---

## Evaluation framework

### 1. Offline evals (pre-deployment)
- Evaluate on a static golden dataset before deploying
- Required metrics depend on system type (see below)
- Run automatically in CI/CD on any model/prompt/retrieval change

### 2. Online evals (post-deployment)
- Shadow traffic comparison, A/B tests, or gradual rollout
- Instrument real usage for quality signals
- Set anomaly detection thresholds

### 3. Adversarial evals
- Jailbreak / injection attempts
- Out-of-scope queries
- Misleading or contradictory inputs
- Edge cases near decision boundaries

### 4. Regression suite
- A curated set of high-value test cases that must not degrade
- Run on every code, prompt, model, or retrieval config change
- Never shrink the regression suite without documented approval

---

## Metric reference by system type

### LLM generation
| Metric | Description | Threshold type |
|---|---|---|
| Task completion rate | % of tasks where output meets spec | Pass/fail |
| Hallucination rate | % of outputs containing unsupported claims | Numeric upper bound |
| Format compliance | % of outputs matching required structure | Numeric lower bound |
| Safety trigger rate | % of outputs flagged by safety classifier | Numeric upper bound |

### RAG systems
| Metric | Description | Threshold type |
|---|---|---|
| Answer faithfulness | Output grounded in retrieved context (RAGAS) | Numeric lower bound |
| Context recall | Relevant chunks retrieved / total relevant chunks | Numeric lower bound |
| Context precision | Relevant chunks in top-K / K | Numeric lower bound |
| No-answer rate | % of queries returning "I don't know" | Range (not too high / not too low) |

### Agentic systems
| Metric | Description | Threshold type |
|---|---|---|
| Task success rate | End-to-end task completed correctly | Numeric lower bound |
| Tool call accuracy | Correct tool selected and called | Numeric lower bound |
| Loop / recursion rate | % of runs hitting max iteration limit | Numeric upper bound |
| Human escalation rate | % of tasks requiring human override | Range |

---

## Scoring approaches

| Method | When to use |
|---|---|
| Human eval (gold standard) | High-stakes quality decisions; calibrates automated evals |
| LLM-as-judge | Scale offline evals; use a separate strong model to score |
| Rule-based assertions | Format compliance, structured output validation |
| RAGAS framework | RAG-specific metrics (faithfulness, context recall/precision) |
| Reference-based (BLEU/ROUGE) | Only for constrained generation; not for open-ended output |

---

## Required output

1. Evaluation objective (what is being evaluated and why it matters)
2. Failure model (likely and worst-case failure modes)
3. Test categories (offline, online, adversarial, regression)
4. Dataset and rubric requirements (golden set, human labels, scoring method)
5. Acceptance thresholds (minimum release, warning thresholds, kill-switch criteria)
6. Regression plan (what runs on every change, ownership)
7. Post-launch monitoring plan (metrics, alerts, review cadence)
8. Ship / Hold / Pilot recommendation with rationale

---

## Checklist

- [ ] Evaluation objective is explicit
- [ ] Failure modes listed (at least top 3)
- [ ] Offline eval dataset defined (size, source, labeling method)
- [ ] Online monitoring metrics defined
- [ ] Adversarial cases included
- [ ] Golden regression suite defined
- [ ] All thresholds are numeric or clearly bounded (no "should be good")
- [ ] Scoring method chosen and documented
- [ ] Human eval vs automated eval decision made
- [ ] Monitoring ownership assigned
- [ ] Release recommendation tied to evidence, not intuition
