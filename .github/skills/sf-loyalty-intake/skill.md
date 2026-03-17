# Salesforce Loyalty Intake Skill

Use this skill when:
- the request involves Salesforce loyalty management
- the request touches healthcare or life sciences contexts
- the stakeholder ask is business-heavy and under-structured
- a discovery/intake brief must be created before planning

---

## Skill objectives

- Turn a raw ask into a structured loyalty-management intake brief
- Identify impacted personas, workflows, objects, automations, and integrations
- Identify privacy, auditability, and release implications early
- Prepare a clean handoff to the planner or Salesforce regulatory agent

---

## Discovery questions to ask

**Business context**
- What loyalty program is this for? (name, type, target population)
- What business outcome does this change drive?
- Is this triggered by a compliance requirement, product roadmap, or operational issue?
- What is the deadline or regulatory timeline, if any?

**Personas affected**
- Who are the members? (patients, HCPs, caregivers, field reps, consumers)
- Which internal teams own or operate this change? (loyalty ops, IT, compliance, marketing)
- Who approves this change? (program owner, legal, compliance, IT review board)

**Loyalty program mechanics**
- Which program tiers or segments are affected?
- Does this affect points accrual, point expiration, redemption, or voucher issuance?
- Does this change eligibility criteria, qualifying activities, or reward catalog?
- Are there any spend thresholds, activity caps, or promotional rules involved?

**Salesforce surfaces**
- Which Salesforce org(s) are involved?
- Are any connected apps, portals, or Experience Cloud sites affected?
- Is Marketing Cloud (email, SMS, push) involved in member communications?
- Are there third-party systems (partner portals, ERP, pharmacy platform) that must be updated?

**Data and compliance**
- Does the change touch PHI, PII, or regulated member data?
- Are consent records or communication preferences involved?
- Is there an audit trail requirement for this change?
- Are there retention or deletion requirements?

---

## Salesforce Loyalty Management object map

| Object | Risk level | Description |
|---|---|---|
| `LoyaltyProgram` | High | Defines the program structure |
| `LoyaltyProgramMember` | High | Individual member enrollment and status |
| `TransactionJournal` | High | Accrual and redemption transaction log |
| `MemberBenefit` | Medium | Benefits and entitlements assigned to members |
| `Voucher` / `VoucherDefinition` | High | Issued rewards and redemption instructions |
| `LoyaltyLedger` | High | Point balance ledger per member |
| `LoyaltyPartner` | Medium | External partner relationships |
| `PromotionMarketSegment` | Medium | Promotional targeting rules |

---

## Required output

1. Request summary
2. Business objective
3. Personas affected
4. Loyalty process affected (accrual / redemption / tiering / comms / eligibility)
5. Salesforce surfaces likely impacted (objects, flows, Apex, LWC, integrations, Marketing Cloud)
6. Data sensitivity implications
7. Known dependencies
8. Key risks and unknowns
9. Recommended next handoff

---

## Checklist

- [ ] Program name and type identified
- [ ] Impacted loyalty objects named
- [ ] Member data sensitivity assessed
- [ ] Automation type(s) identified (Flow / Apex / Process Builder)
- [ ] Integration touchpoints identified
- [ ] Consent/communication preference impact assessed
- [ ] Deployment environment(s) identified
- [ ] Approvals and review path identified
- [ ] Regulatory review flag raised if PHI/PII or eligibility decisions are involved
