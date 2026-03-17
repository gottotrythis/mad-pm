---
applyTo: "**"
---

# Salesforce / Healthcare Domain Instructions

Apply this overlay when a task is classified as Salesforce loyalty management,
healthcare life sciences, or any work involving regulated member, patient, or HCP data.

Load this file alongside `project.instructions.md` for all Salesforce work.

---

## Object model rules

- Name every Salesforce object and field that could be affected — standard and custom.
- Distinguish between standard objects (`Contact`, `Account`) and custom (`LoyaltyMember__c`, `TransactionJournal__c`).
- Flag any changes to OWD (org-wide defaults), sharing rules, profiles, or permission sets.
- Identify record types, page layouts, validation rules, and duplicate rules that intersect with the change.
- For Loyalty Management work, treat these as high-risk objects:
  - `LoyaltyProgram`, `LoyaltyProgramMember`, `TransactionJournal`, `MemberBenefit`, `Voucher`

---

## Automation rules

- Clearly identify the automation mechanism: Flow (record-triggered, scheduled, screen, autolaunched), Apex trigger, Process Builder (legacy), or Workflow Rule.
- Never recommend changes to active Flows or Apex without specifying:
  - Which sandbox validates first
  - Required test coverage (target ≥ 90%)
  - Deployment sequencing
- Flag order-of-execution implications: validation rules → before triggers → after triggers → Flows.
- Do not mix automation types for the same object/trigger event unless explicitly justified.

---

## Integration rules

- Identify all inbound and outbound integration points for any change.
- Document: source, target, transport (REST/SOAP/Platform Events/CDC/Outbound Message), field mappings, and transformation logic.
- Identify retry behavior, idempotency requirements, and reconciliation strategy.
- Use the `sf-integration-mapping` skill for any non-trivial integration change.
- Flag changes to connected apps, named credentials, or external services.

---

## Loyalty program rules

- Identify impact on: program rules, tier logic, reward/redemption eligibility, accrual behavior, expiration logic, and member communications.
- Treat any change to member balance, transaction history, or accrual logic as **high-risk** — require explicit UAT sign-off.
- Flag whether the change affects: qualifying vs non-qualifying spend rules, tier point vs currency point distinctions.
- For HCP-facing programs: identify sales rep, medical science liaison, and compliance officer impact.

---

## Data sensitivity rules

- Assume all HCP, patient, member, and personal data is **sensitive by default**.
- Identify fields that constitute PHI, PII, or regulated data under HIPAA / state privacy laws.
- Document consent and communication preference implications for any Marketing Cloud or messaging integration.
- Never recommend moving, copying, or transforming sensitive data without explicit justification and a documented data flow.
- Flag if the change could expose sensitive records to roles/profiles that should not see them.

---

## Deployment rules

- Always sequence deployments: **Full Sandbox → Partial Sandbox (UAT) → Production**.
- Require documented rollback steps before any production deployment proceeds.
- Require test class coverage ≥ 75% (Salesforce minimum) — target ≥ 90% for triggered objects.
- Use changesets or SFDX packages — no manual metadata deployment in production.
- Document metadata dependency order (e.g., custom objects before flows, permission sets before profiles).
- Identify any required post-deployment data steps (e.g., data migration, field backfill, cache refresh).

---

## Audit and compliance rules

- Flag changes to audit fields, history tracking settings, and event log subscriptions.
- Require Field History Tracking be enabled for any regulated or eligibility-impacting field.
- Identify reporting and dashboard impacts for any compliance output (member eligibility, activity logs, audit trails).
- For life sciences: identify any 21 CFR Part 11 or SOX implications on data integrity and change evidence.
- Do not remove or modify audit log retention settings without explicit authorization.

---

## Handoff triggers (when to escalate)

Invoke `sf-regulatory` agent when:
- Change touches PHI, PII, consent, or communication preferences
- Change affects reward/redemption eligibility decisions
- Change requires deployment in a regulated environment
- Evidence of testing and approval is needed for audit trail
