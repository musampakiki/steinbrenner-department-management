# ARCH-19 — Department Management FC3 consumer mapping and local recovery
Date: 2026-10-14
Status: DOCUMENTARY CONSUMER MAPPING / HR FC3 UNACCEPTED / DM UNSIGNED
Read-only HR issuer schema: `musampakiki/steinbrenner-team-agents`, branch `agent/team-agents-development`, `docs/contracts/schemas/hr-placement-receipt.0.1-fc3.candidate.schema.json`, blob `a12ca2ca4a176fac28715dc9772783e22365c46d`.
Source DM local design: `docs/architecture/STAFFING_ASSIGNMENT_CONSISTENCY.md`, blob `8fe0f5e316c56d0294b7beeae62770e3051e9821`.
## Mapping and safety
| HR candidate discriminator | DM local request disposition | DM position link eligibility |
|---|---|---|
| INTAKE / PENDING | HR_PENDING after trusted issuer proof | NO |
| INTAKE / REJECTED | REJECTED only if verified issuer decision + matching request | NO |
| INTAKE / UNKNOWN | UNKNOWN_HOLD, authoritative lookup by operation before retry | NO |
| PLACEMENT / COMMITTED | HR_PLACEMENT_RECORDED, then verify **current** HR state | MAY attempt local DM seat CAS after currentness; no work authorization |
| No HR receipt because timeout/network failure | DM-local UNKNOWN_HOLD (not forged INTAKE/UNKNOWN) | NO |
| Invalid/untrusted/foreign tenant receipt | DENY or RECONCILIATION_HOLD, redacted audit | NO |
## Invariants and open issues
1. HR owns placement, agent identity, employment career; DM owns StaffingRequest/position/DepartmentAssignmentLink only. No direct foreign database or shared Arbeit engine.
2. A signed historical `PLACEMENT COMMITTED` receipt is insufficient for currentness. Verify accepted HR get-current snapshot and matching tenant/employer/requisition before DM position CAS.
3. HR committed + DM write failed: durable DM_LINK_PENDING; recover HR proof/current revision then repeat **DM-only** link, never repeat HR hire blindly.
4. Stale/deleted/full position: CAPACITY_CONFLICT HOLD and issuer-governed remediation; never overwrite existing assignment or erase HR career.
5. FC3 intakeRef mandatory for REJECTED/UNKNOWN is unresolved for rejection before HR intake persisted; cannot manufacture `intakeRef`.
6. Transport timeout cannot create issuer evidence or fictional signed UNKNOWN; maintain consumer-local unresolved operation and query HR with accepted idempotent operation.
7. Employee number is HR-owned, optional/minimum disclosure; no inherited staff or permissions on structural clones.
8. Transfer/discharge depends on Work Management drain, Workflows/domain reconciliation and employer clearance revocation, separate from HR receipt.
9. External Auth/Tenancy/KMS and HR exact public contract pins, error taxonomy, retention and QA proof are OPEN.
## Future consumer signoff gate
HR signed contract ID/version+schema SHA; HR issuer semantics for recorded vs unrecorded intake and event/currentness; trusted Auth/KMS issuer verifier; DM approved mapping/revisions; QA positive/negative evidence and explicit PRECODE. None granted. **Status: DOCUMENTARY REVIEW COMPLETE / DM CONSUMER NOT COMPATIBLE-APPROVED / PRECODE HOLD / R1 NO-GO.**
