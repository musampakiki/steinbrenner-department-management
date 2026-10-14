# DM-GOV-APPROVAL-01 — cross-owner contract approval ledger
Date: 2026-10-14
Status: OWNER_APPROVALS_OPEN / NOT RELEASE AUTHORIZATION
This document tracks owner decisions, not accepted wire specifications.

| ID | Issuing authority | Contract decision / evidence required | Current evidence | State |
|---|---|---|---|---|
| CO-01 | DM issuer | approve module contract families, 0.1 candidate and owner contract digest | ISSUER_VERSIONING_POLICY.md draft | DRAFT / UNSIGNED |
| CO-02 | Team Agents HR | employer intake, agent identity, placement, transfers/discharge, privacy; sign issuer wire+DM mapping | HR candidate schema blob `57012796fa10490db2aaf3ec1e87fa6706f86935` | BLOCKED_EXTERNAL_OWNER |
| CO-03 | Kernel | module build/selection, provider binding, CAS/currentness port and issuer version | no accepted pin established | BLOCKED_EXTERNAL_OWNER |
| CO-04 | App Installation | install eligibility, permissions, package/version compatibility | no accepted pin established | BLOCKED_EXTERNAL_OWNER |
| CO-05 | Platform Workflows | draining, in-flight runs, timer/retry/lease/fencing scope | no accepted pin established | BLOCKED_EXTERNAL_OWNER |
| CO-06 | Auth/RBAC & Tenancy | actor/effective principal, tenant and authorization PEP, cross-tenant clone denial | no accepted pin established | BLOCKED_EXTERNAL_OWNER |
| CO-07 | KMS / Audit | secret noninheritance, cryptographic receipts, log/privacy retention | no accepted pin established | BLOCKED_EXTERNAL_OWNER |
| CO-08 | Work Management | business shifts, DAG tasks, active work/drain and effect reconciliation | no issuer contract pin established | BLOCKED_EXTERNAL_OWNER |
| CO-09 | Organization Composition | company graph and department links/tenant ownership | no issuer contract pin established | BLOCKED_EXTERNAL_OWNER |
| CO-10 | Department Packages / employer | role criteria, template extensions, clone allowlist, qualification/passport/clearance issuer | no issuer contract pin established | BLOCKED_EXTERNAL_OWNER |
| CO-11 | Domain effect ledger / PEP | protected effect truth, UNKNOWN settlement/replay and discharge | no accepted issuer pin established | BLOCKED_EXTERNAL_OWNER |
| CO-12 | DM GOV / QA / MET / release owners | compatibility fixtures, negative test evidence, signoffs and scoped PRECODE | documentary design only, tests not run | NOT_AUTHORIZED |

Approval evidence record required per entry: decisionId, responsible issuer, exact canonical repo/path, blob SHA, contract ID/version, schema digest, signature/reviewer, date, consumer pins, accepted guarantees, limitations, fixtures, decision and expiry/revocation. These are **governance record suggestions**, not a shared runtime API.
States: UNREVIEWED, DRAFT, BLOCKED_EXTERNAL_OWNER, REVIEW_REQUESTED, ISSUER_ACCEPTED, CONSUMER_COMPATIBLE, QA_VERIFIED, REJECTED, WITHDRAWN. Never mark ISSUER_ACCEPTED from a file's mere existence. Old version remains addressable; any external contract change triggers impact/CAS/revision/tenant/privacy review.

## Decision order and stops
DM first reviews its own draft. HR issuer signs an **actual** wire, then DM accepts a pinned consumer mapping; independently complete Kernel/Workflows/security/Work Management/Package owner reviews. QA/MET and release approval come last and require actual evidence. Current result: all external issuer rows blocked. This is documentation only, no executable PASS and no assumption of runtime availability.

## ARBEIT-ARCH-12 — CO-02 negotiation handoff
- DM issuer question packet: [HR_STAFFING_NEGOTIATION_PACKET](../contracts/HR_STAFFING_NEGOTIATION_PACKET.md); commit `3e7aa89ae8558ac51ac71732f2fdd2a5381a8ee0`.
- DM assignment consistency and partial-commit failure cases: [STAFFING_ASSIGNMENT_CONSISTENCY](../architecture/STAFFING_ASSIGNMENT_CONSISTENCY.md); commit `65e44c996c749a20107c4d94466c722fa0073296`.
- CO-02 state remains `BLOCKED_EXTERNAL_OWNER`. No HR issuer acceptance, issued wire, signed receipt model or consumer compatibility evidence. The packet was recorded in DM, not sent/approved in the HR repository.

## ARBEIT-ARCH-14 — CO-01/CO-02 bilateral decision hold
[Read-only HR/DM comparison](../contracts/HR_DM_BILATERAL_CONSUMER_SIGNOFF_GATE_ARCH_14.md), source candidate pins HR `c093cc449780ed935127dac4df0d144c7fe6be4a` and DM `e63ac587be1bf41d6c38a760677aa336669cdb9d`. Target alignment documented for receipt/currentness/idempotency; issuer signatures and accepted version/transport remain absent. **CO-01 UNSIGNED; CO-02 BLOCKED_EXTERNAL_OWNER; BILATERAL NOT_SIGNED.**

## ARCH-15 CO-02 checkpoint
HR receipt freeze candidate blob `bc942a0f5d1834a85df53d5f75fdef495810647b`, not accepted wire. [DM compatibility review](../contracts/HR_PLACEMENT_RECEIPT_CONSUMER_COMPATIBILITY_ARCH_15.md). CO-01 unsigned, CO-02 blocked, QA/MET not executed, PRECODE HOLD.

## ARCH-16 signoff readiness
HR issuer candidate blob `bc942a0f5d1834a85df53d5f75fdef495810647b`; DM signoff checklist [here](HR_PLACEMENT_CONSUMER_SIGNOFF_PREPARATION_ARCH_16.md). CO-01 UNSIGNED; CO-02 BLOCKED_EXTERNAL_OWNER; no HR contract approval or DM consumer acceptance. PRECODE HOLD.
