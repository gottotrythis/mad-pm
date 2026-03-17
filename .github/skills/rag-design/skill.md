# RAG Design Skill

Use this skill when:
- the solution requires retrieval-augmented generation
- documents, knowledge bases, policies, or enterprise content must ground answers
- chunking, metadata, citation, or refresh strategy must be defined
- the team is debating between different retrieval or indexing approaches

---

## Skill objectives

- Design the retrieval layer cleanly before building
- Identify source inventory and data freshness needs
- Define chunking, metadata, indexing, and retrieval policies
- Define grounding and citation behavior
- Surface retrieval failure modes early

---

## Source inventory framework

For each source document/system, capture:

| Field | Description |
|---|---|
| Source name | Display name of the knowledge source |
| Source type | Document store, database, API, SharePoint, Confluence, etc. |
| Owner | Team or system that owns the content |
| Format | PDF, DOCX, HTML, structured JSON, etc. |
| Update cadence | Real-time, daily, weekly, static |
| Access control | Public, internal-only, role-restricted |
| Volume estimate | Number of documents / tokens at scale |

---

## Chunking strategy comparison

| Strategy | Best for | Watch out for |
|---|---|---|
| Fixed-size (token count) | Large homogeneous documents | Splits mid-sentence; loses context |
| Sentence boundary | Conversational or prose content | Short sentences → underloaded chunks |
| Paragraph / section | Structured documents with headers | Header-dense docs → large uneven chunks |
| Semantic (embedding similarity) | Heterogeneous content | Computationally expensive; needs overlap tuning |
| Hierarchical (parent/child) | Long docs needing both summary and detail | Requires two retrieval passes |

Recommended overlap: 10–20% of chunk size to preserve context across boundaries.

---

## Metadata strategy

Always index these fields for filtering and re-ranking:
- `source_id` — unique document identifier
- `source_name` — human-readable source label
- `last_updated` — for freshness filtering
- `section` / `chapter` — for structural context
- `access_level` — for permission-aware retrieval
- `document_type` — policy, FAQ, procedure, etc. (enables type-specific prompting)

---

## Retrieval strategy options

| Approach | Description | Trade-offs |
|---|---|---|
| Dense vector (ANN) | Embed query + docs; find nearest neighbors | Semantic but can miss exact keywords |
| Sparse (BM25/TF-IDF) | Keyword matching | Fast; misses paraphrase |
| Hybrid (dense + sparse) | Combine both with RRF or score fusion | Best recall; more complex pipeline |
| Re-ranking (cross-encoder) | Re-score top-K with full query-doc interaction | Slower; significantly improves precision |
| HyDE | Generate a hypothetical doc, then retrieve | Improves recall for vague queries; adds latency |

---

## Citation and grounding policy

- Define what a "source citation" looks like in the response (inline footnote, end of response, link)
- Define minimum evidence threshold: how many relevant chunks must be retrieved before the model responds?
- Define behavior when no relevant chunk is found: refuse, disclose, or fall back to general model knowledge (with disclosure)
- Never let the model respond as if grounded when retrieval returned 0 results

---

## Required output

1. Source inventory (table)
2. Freshness and ingestion requirements
3. Chunking strategy with rationale
4. Metadata strategy (fields and why)
5. Retrieval strategy (approach and why)
6. Citation / grounding policy
7. Failure modes (no-result, low-confidence, stale content, contradictory sources)
8. Monitoring implications

---

## Checklist

- [ ] All source systems listed with owners
- [ ] Ingestion/update cadence defined per source
- [ ] Chunking strategy chosen and rationale documented
- [ ] Chunk size and overlap values defined
- [ ] Metadata fields defined
- [ ] Retrieval approach chosen (dense / sparse / hybrid)
- [ ] Re-ranking decision made
- [ ] Citation policy defined
- [ ] No-result behavior defined
- [ ] Low-confidence behavior defined
- [ ] Stale content handling defined
- [ ] Access-controlled source handling defined
