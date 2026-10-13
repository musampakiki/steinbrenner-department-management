# DM-CONSISTENCY-01 — Staffing request, HR receipt and department assignment consistency
Date: 2026-10-14
Status: CANDIDATE TARGET / NOT IMPLEMENTED / HR OWNER AGREEMENT OPEN

## Separate authoritative ledgers
- DM owns local staffingRequest lifecycle, position inventory/capacity and local DepartmentAssignmentLink aggregate/revision.
- HR owns authoritative agent identity, employee numbers, employment/placement lifecycle and current placement revision.
- Employer/Department Package owns professional qualification, authorization to perform job duties and employer clearance; Auth/RBAC/PEP own platform permissions.
- Work Management owns business tasks/shifts, while Workflows/domain effect issuer owns durable runs/drains/leases and effect receipts.
No distributed transaction or shared DB is assumed.

## Proposed local request and link lifecycle (names CANDIDATE)
`REQUEST_DRAFT → SUBMITTED → HR_PENDING → HR_PLACEMENT_RECORDED → DM_LINK_PENDING → LINKED`.
Alternates: `REJECTED, CONFLICT_HOLD, RECONCILIATION_REQUIRED, CANCEL_REQUESTED, CANCELLED_IF_UNCOMMITTED`.
Link lifecycle: `VERIFYING_HR → LINKED → TRANSFER_OR_DISCHARGE_PENDING → DETACHED`; dispute states `STALE_HR, CAPACITY_CONFLICT, UNKNOWN_HOLD`.
None of these DM labels changes HR placement truth. No generic "ACTIVE" equals authorization for tasks.

## Candidate consistency invariants
I-01: tenant and actor PEP scoped at every DM read/write/reconciliation; never trust unverified HR event or global employee number.
I-02: one position's occupied capacity cannot exceed its own policy; check `expectedPositionRevision`/CAS within DM ledger. If HR commits while seat now full: quarantine conflict, preserve HR receipt, initiate authorized reassignment or HR remediation; never discard acknowledged HR truth.
I-03: same scoped DM operationId and canonical payload must return same DM request/receipt; changed payload is conflict. HR issuer separately controls its idempotency and cannot be assumed to share DM dedup state.
I-04: only current issuer-authenticated HR placement receipt or owner-approved currentness evidence can create a DM link; `PENDING` or unknown HR outcome is not eligible. DM link stores scoped HR reference, issuer version and revision, never editable HR career event.
I-05: HR placement committed does not guarantee DM position link committed; link committed does not guarantee job-specific qualification or execution authorization.
I-06: event is a signal, not currentness source when out-of-order. Dedup eventId, retain per-aggregate last revision; gap or stale event leads verified HR snapshot lookup before changing state.
I-07: DM structural clone or new instance has **zero** staffing links/requests and no inherited HR receipt or privileges.
I-08: no local detach/removal when unresolved Work Management task/domain effect/clearance state requires drain. Preserve pending state and escalate; signed HR career close is separate.
I-09: store minimal HR data, tenant-filter every query, names only scoped derived views; never reveal cross-employer history or secrets.
I-10: never infer success from transport timeout. Query HR authoritative operation/placement receipt and reconcile with DM ledger before retry.

## Failure and reconciliation decision table
| Observed condition | Safe DM disposition | Forbidden inference |
|---|---|---|
| DM request persisted, HR not yet reached | PENDING; reconcile owner-approved intake by scoped operation ID | that an employee was hired |
| HR accepted intake but no placement | HR_PENDING; query issuer receipt | that agent identity or job clearance exists |
| HR placement COMMITTED, DM association write failed | DM_LINK_PENDING; durable pending reference; verify current HR receipt and retry DM-only CAS link | replay HR hiring without issuer proof |
| HR committed, target position now full/deleted | CAPACITY_CONFLICT; freeze link and request owner remediation/transfer | silently evict another placement or discard HR commitment |
| DM link exists, HR placement revoked/closed | STALE_HR/HOLD; stop any new work admission via employer PEP, coordinate drain, detach only with agreed evidence | continuing protected work on stale link |
| HR event arrives twice, late or missing sequence | dedup/gap HOLD; query issuer snapshot and compare revision | using event arrival order as truth |
| HR request timeout and result unknown | UNKNOWN_HOLD; get-by-operation; bounded query/retry only after proven absent under issuer policy | automatic second hire |
| Transfer partly committed | TRANSFER_OR_DISCHARGE_PENDING; reconcile both placement receipts and Work/domain drain | clone old passport, auto-close source or assume distributed atomic transfer |
| Termination requested with effect UNKNOWN | stop admission, maintain discharge pending, domain owner resolves and issuer-accepted close | erase position link and report fully terminated |
| DM crashes after durable link, before response | replay DM receipt from local ledger, compare HR currentness | second link or second placement |
| Foreign tenant receipt/candidate | reject and audit safe metadata | exposing lookup result or linking employee |

## Minimal recovery proof (future, not executed)
After recovery DM must show local operationId, request hash, tenant/actor authority evidence, position expected/current revision, HR contract version+receipt ID/revision/currentness check, local link revision and decision, unresolved Workflows/domain receipts, next reconciliation owner/action, timestamps and redaction/audit refs. Durable owner-local outbox/inbox is a design requirement, not a second Workflows engine. Polling/cadence/retry/dedup windows require HR and platform approvals. Bounded retry + backoff + incident escalation; no claim of exactly-once cross-owner side effects.

## Negative acceptance scenarios (documentary only)
Duplicate hire same key, conflicting payload, HR commit+DM outage, HR revocation+stale link, concurrent seat collision, replayed event, out-of-order transfer, tenant crossing, forged HR receipt, employee number name collision, unpublished template clone with staff, expired qualification, Workflows drain UNKNOWN, archive with live placement and request cancellation after HR commitment. Each needs owner-approved fixture and observed evidence after PRECODE; no tests executed.
