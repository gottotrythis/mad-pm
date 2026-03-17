# Salesforce Integration Mapping Skill

Use this skill when:
- Salesforce changes interact with external systems
- field mappings, API contracts, or reconciliation behavior must be documented
- batch/event failure handling needs to be defined
- a new integration touchpoint is being introduced or modified

---

## Skill objectives

- Define source-to-target field mappings
- Identify contract assumptions and missing fields
- Document error handling, retries, and reconciliation logic
- Make integration risk visible before build or release

---

## Common Salesforce integration patterns

| Pattern | Transport | Use case |
|---|---|---|
| REST callout (outbound) | HTTP/REST | Salesforce → external system |
| REST inbound | Connected app + REST API | External → Salesforce |
| Platform Events | Salesforce Event Bus | Async, decoupled event publishing |
| Change Data Capture (CDC) | Salesforce CDC | Streaming object change events to external consumers |
| Outbound Messages (legacy) | SOAP | Workflow-triggered SOAP notify |
| Batch API | Bulk API 2.0 | Large-volume data sync |
| MuleSoft / middleware | Any | Orchestrated multi-system integration |

---

## Field mapping table format

| Source field | Source system | Target field | Target system | Transformation | Nullable | Notes |
|---|---|---|---|---|---|---|
| `Member_ID__c` | Salesforce | `memberId` | ERP API | None | No | Dedup key |
| `Points_Balance__c` | Salesforce | `pointBalance` | Portal | Cast to int | No | Live balance |
| `Tier__c` | Salesforce | `tierCode` | Marketing Cloud | Picklist → code map | Yes | See tier mapping table |

---

## Error handling patterns to document

- **Retry policy:** max retries, backoff interval, final failure action
- **Idempotency:** is the target system idempotent? What is the dedup key?
- **Partial failure:** if a batch partially fails, what is the recovery path?
- **Dead letter queue:** where do failed events or records go?
- **Alerting:** who is notified on integration failure?

---

## Required output

1. Source system (name, type, owner)
2. Target system (name, type, owner)
3. Field mapping table
4. Transformation rules
5. Validation rules (mandatory fields, format constraints)
6. Error handling and retry behavior
7. Reconciliation approach (how to detect and resolve drift)
8. Risks and open questions

---

## Checklist

- [ ] Source system named and owner identified
- [ ] Target system named and owner identified
- [ ] All mapped fields listed with transformation rules
- [ ] Mandatory vs optional fields distinguished
- [ ] Primary/dedup key(s) identified
- [ ] Failure paths documented
- [ ] Retry and idempotency rules documented
- [ ] Reconciliation cadence and method defined
- [ ] Monitoring and alerting owner named
- [ ] PHI / PII fields flagged for data handling review
