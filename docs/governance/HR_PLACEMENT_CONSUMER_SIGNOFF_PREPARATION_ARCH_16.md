# ARBEIT-ARCH-16 — DM consumer signoff preparation
Date: 2026-10-14
Status: PREPARED / SIGNOFF_NOT_GRANTED / HR_ISSUER_NOT_ACCEPTED
Owner: Department Management for position links and consumer mapping only.

## Exact HR documentary pin
HR `HR-PLACEMENT-RECEIPT-0.1-FC1` `musampakiki/steinbrenner-team-agents/docs/contracts/HR_PLACEMENT_RECEIPT_FREEZE_CANDIDATE_ARCH_15.md` blob `bc942a0f5d1834a85df53d5f75fdef495810647b`. Prior DM compatibility review blob `1245f24ffbb67a83372e5453c4f02ba83dfd6446`. Neither is an accepted wire version. HR ARCH-16 owner-decision-ready document must be reviewed in the HR repository; no HR issuance may be simulated by DM.

## Consumer signoff prerequisites
| Gate | Evidence | Status |
|---|---|---|
| D16-01 HR authority | actual HR issuer ACCEPT decision and immutable schema version/digest/SHA | BLOCKED_HR_OWNER |
| D16-02 DM scope | documented employer/department/position mapping approved by responsible issuer | OPEN |
| D16-03 receipts | issuer authentication, tenant, employee minimal disclosure, revocation/currentness | BLOCKED_AUTH_KMS_HR |
| D16-04 idempotency | scoped key, fingerprint collision, retry/outbox and get-by-operation reconciliation | CANDIDATE |
| D16-05 local state | DM position CAS, occupancy conflict HOLD, HR commit+DM failure repair without repeat hire | CANDIDATE |
| D16-06 discharge | Work Management drain, Workflows/domain effect receipts, employer clearance revocation | BLOCKED_EXTERNAL_OWNER |
| D16-07 proofs | issuer-approved positive and adversarial fixture plan and later observed test evidence | NOT_EXECUTED |
| D16-08 DM decision | named approver, accepted consumer contract version and source SHA, limitations, dated signature | UNSIGNED |
| D16-09 release | DOC/GOV/QA/MET, separate PRECODE authorization | NOT_AUTHORIZED |

No DM contract is `COMPATIBLE` merely because requirements match on paper. DM owner may prepare a reviewed consumer candidate now, but can accept only after the real HR accepted wire and external platform approvals. Acceptance must name exact pins rather than branch pointers or unversioned docs.

## Required future record
`dmDecisionId, dmAuthorizedApprover, decisionTimestamp, dmConsumerContractVersionAndSHA, acceptedHRContractVersionAndSHA, issuerReceiptVerificationPolicyPin, scope/tenant model, negativeTestEvidence, supportedErrorSemantics, migrationRollbackLimitations, decision, conditions`. These are governance document suggestions, not wire fields. Current values: no approver, no accepted HR wire, no DM signature.

## Safety
Separate HR employment and DM assignment ledgers; tenant authorization on each call; current receipt required before local link; stale/UNKNOWN is HOLD. Clone has zero inherited staff, credentials or grants. No private HR integration, shared Arbeit engine, runtime/tests/CI/deployment. PRECODE HOLD / R1 NO-GO.
