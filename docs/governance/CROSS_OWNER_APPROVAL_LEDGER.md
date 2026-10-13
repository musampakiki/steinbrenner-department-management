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
