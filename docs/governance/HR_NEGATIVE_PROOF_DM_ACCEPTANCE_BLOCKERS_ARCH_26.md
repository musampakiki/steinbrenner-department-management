# ARCH-26 — DM Consumer Negative-Proof and HR Retention Acceptance Blocker Audit
Date: 2026-10-14
Status: DOCUMENTARY READINESS AUDIT / DM OWNER UNSIGNED / HR AUTHORITY UNACCEPTED
Read-only HR issuer sources: FC4 schema `d1306a7e80492f11ac00ce25a9533142b24573b0`; ARCH-22 HR ledger `2e23d518db663686830853e65d2eb4f8b12a2bce`; ARCH-23 HR retention `bf285c20bed4764adb5b375b4e09bae91ea171b5`; ARCH-25 HR decision packet `5fb04cb236432b5f79da8cdbe37f4a115990d075`.
DM prior consumer gate `docs/governance/HR_RETENTION_CONSUMER_DECISION_GATE_ARCH_25.md`, blob `f6ccdfe5c42bb0c8ec46b88f38c309f818e35c31`.

## Required consumer restrictions
- Any missing HR reply is **DM_LOCAL_TRANSPORT_UNKNOWN**, never HR-issued `INTAKE UNKNOWN` nor `REJECTED`.
- `KNOWN_PLACEMENT_COMMITTED` requires verified issuer proof, HR currentness/tenant scope and an independent DM seat CAS. An HR COMMITTED placement does not grant work execution or create a DM link.
- A valid signed historic receipt after transfer/revocation is not currentness.
- `NO_RECORD_CONFIRMED` may authorize any retry only when HR publishes and proves an accepted complete-negative guarantee, its coverage window and corresponding idempotency replay semantics. Today those are **NOT ACCEPTED**.
- `INDETERMINATE`, denied/hidden searches, expired retention, stale follower, recovery ambiguity and missing verifier remain HOLD. No inferred noncommit or blind second hire.
- If HR committed but DM position is full/deleted, preserve HR truth and record local conflict; no foreign career mutation or shared transaction.

## Consumer acceptance blocker routing
| Gate | Decision owner | Evidence needed | State |
|---|---|---|---|
| DM26-01 | HR | signed HR issuer API version/digest/SHA + receipt/operation lookup semantics | BLOCKED_EXTERNAL_OWNER |
| DM26-02 | HR | documented retention/tombstone/expiry + replay boundaries | BLOCKED_EXTERNAL_OWNER |
| DM26-03 | HR | proven issuer NO_RECORD completeness OR explicit prohibition | BLOCKED_EXTERNAL_OWNER |
| DM26-04 | Auth/Tenancy/KMS/Audit | accepted issuer authenticity, tenant privacy, trust+revocation | BLOCKED_EXTERNAL_OWNER |
| DM26-05 | DM | versioned consumer mapping, local CAS/seat rules, attributable owner signoff | UNSIGNED |
| DM26-06 | QA/MET/Workflows/effect owners | authorized negative tests, drain and UNKNOWN reconciliation | NOT_EXECUTED / BLOCKED |

## Verdict
Prior ARCH-21–25 designs consolidated without duplicating HR schema or selecting HR policy on DM's behalf. Bilateral wire compatibility cannot be declared. No shared Arbeit runtime/DB or direct HR private integration. PRECODE HOLD / R1 NO-GO / RELEASE HOLD.
