# Salesforce Release Readiness Skill

Use this skill when:
- a Salesforce change is approaching deployment
- sandbox/UAT/prod sequencing must be documented
- rollback and smoke tests are needed
- release evidence must be tightened for a controlled environment

---

## Skill objectives

- Produce a clean release readiness pack
- Make deployment sequencing and dependencies explicit
- Define validation checks and rollback conditions
- Reduce release ambiguity and operational risk

---

## Deployment tooling context

| Method | When to use |
|---|---|
| SFDX / CLI (`sf deploy`) | Recommended for tracked orgs with source control |
| Salesforce Packages (2GP) | For managed ISV or complex multi-component deploys |
| Changesets | Legacy orgs without source tracking; acceptable for small changes |
| Metadata API direct | Only for tooling / automation pipelines; not manual use |

---

## Environment sequencing

```
Developer Sandbox → Full/Partial Sandbox → UAT Sandbox → Production
```

- Developer sandbox: unit testing and integration smoke tests
- Full/Partial sandbox: regression testing and QA
- UAT sandbox: business validation; sign-off required before prod
- Production: gated; requires documented approval and rollback plan

---

## Required output

1. Release summary (what changed, why, who owns it)
2. Preconditions (approvals, environments, config, data setup)
3. Sandbox / UAT / prod deployment sequence with steps
4. Smoke test checklist (per environment)
5. Rollback plan (conditions, steps, validation)
6. Post-deployment monitoring / validation plan
7. Release recommendation (ship / hold / conditional)

---

## Smoke test patterns for Salesforce Loyalty work

- Create a test member and verify enrollment confirmation
- Trigger an accrual transaction and verify `TransactionJournal` and `LoyaltyLedger` update
- Redeem a reward and verify voucher issuance and balance deduction
- Trigger a tier evaluation and verify tier upgrade/downgrade record
- Verify Marketing Cloud send (if comms are part of the change)
- Verify connected app or integration call (if applicable)

---

## Rollback decision criteria

Rollback is required if any of the following occur:
- Critical automation errors on `LoyaltyProgramMember`, `TransactionJournal`, or `Voucher`
- Incorrect point balance updates for real members
- Communication sends to wrong or excluded member segments
- Integration failures with downstream systems that cannot self-recover
- Test coverage below threshold after deployment

---

## Checklist

- [ ] Metadata dependencies identified and sequenced
- [ ] Target environments identified
- [ ] Required approvals documented (business, compliance, IT)
- [ ] Test class coverage ≥ 75% confirmed (target ≥ 90%)
- [ ] Data setup steps documented
- [ ] Smoke tests listed per environment
- [ ] Rollback triggers and steps documented
- [ ] Post-deployment validation steps listed
- [ ] Monitoring owner identified
- [ ] Deployment window agreed (avoid peak program activity periods)
