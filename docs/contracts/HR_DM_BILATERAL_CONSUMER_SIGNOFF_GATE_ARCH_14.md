# ARBEIT-ARCH-14 — Bilateral HR ↔ Department Management reconciliation
Date: 2026-10-14
Status: DOCUMENTARY RECONCILIATION COMPLETE / ISSUER ACCEPTANCE OPEN / BILATERAL SIGNOFF NOT GRANTED

## Immutable source evidence, NOT approved contract versions
- HR issuer-owned proposed contract: `musampakiki/steinbrenner-team-agents` `agent/team-agents-development/docs/contracts/HR_STAFFING_PLACEMENT_RECEIPTS_TA_ARCH_13.md`, Git blob `c093cc449780ed935127dac4df0d144c7fe6be4a`.
- HR candidate JSON Schema: `docs/contracts/schemas/hr-employer-integration.candidate-0.1.schema.json`, Git blob `57012796fa10490db2aaf3ec1e87fa6706f86935`, `urn:steinbrenner:ta:hr-employer:candidate-0.1`; not an accepted transport.
- DM proposal: `musampakiki/steinbrenner-department-management` `agent/department-management-development/docs/contracts/HR_STAFFING_NEGOTIATION_PACKET.md`, Git blob `e63ac587be1bf41d6c38a760677aa336669cdb9d`.
- DM consistency: `docs/architecture/STAFFING_ASSIGNMENT_CONSISTENCY.md`, Git blob `8fe0f5e316c56d0294b7beeae62770e3051e9821`.
SHA pins identify document **content**, not immutable released API versions, signed decisions, runtime schema, or branch HEAD.

## Reconciliation matrix
| ID | HR issuer proposal | DM consumer requirement | Outcome / owner action |
|---|---|---|---|
| BIL-01 Employer identity | HR validates authorized employerRef and tenant/actor | DM staffingRequestId/departmentId/positionId, employer Package identity | GAP: agree legal employer vs DM structural issuer; HR owns intake field mapping |
| BIL-02 Requisition identity | HR candidate employerRef, requisitionRef, requestedCount, scopeRef | DM revisioned vacancy/position capacity | GAP: mapping/version/cardinality must be signed; cannot invent HR departmentId |
| BIL-03 Placement receipt | HR proposes issuer-authenticated placementRef, agentRef, HR revision and status | DM verifies receipt before local CAS link | ALIGNED TARGET; exact signed envelope/issuer contract OPEN |
| BIL-04 Idempotency | HR proposes scoped operation + canonical request hash | DM separate idempotency and reconciliation ledger | ALIGNED TARGET; key scopes, retention and conflict response OPEN |
| BIL-05 Currentness | HR proposes get-by-ref/operation and current revision | DM must reject stale/closed HR state | ALIGNED TARGET; authoritative lookup semantics/TTL OPEN |
| BIL-06 Partial commit | HR placement may commit before DM link | DM pending repair with no duplicate hire | ALIGNED TARGET; recovery lookup, capacity conflict and compensation OPEN |
| BIL-07 Transfer/exit | HR owns career transfer/closure | DM coordinates Work Management drain and employer PEP revocation | GAP: separate owner receipts and terminal ordering must be agreed |
| BIL-08 Events | HR candidate revisioned events and snapshot | DM dedup, gap hold, snapshot verify | ALIGNED TARGET; delivery, ordering, replay window OPEN |
| BIL-09 Confidentiality | HR minimum-scoped identity/placement disclosures | DM minimal ref storage, tenant filter | ALIGNED TARGET; Auth/Tenancy privacy signoff OPEN |
| BIL-10 Clone permissions | HR identity cloning distinct from DM structural cloning | new department/positions, empty staff, no inherited privileges | ALIGNED architectural target; negative evidence NOT TESTED |
| BIL-11 Execution clearance | HR placement never grants workplace qualification or work permission | employer Package/PEP separate proof | ALIGNED ownership; external package/PEP signoff OPEN |
| BIL-12 Versions/error semantics | HR candidate 0.1 and proposed ports not accepted | DM `0.1-draft` consumer proposal not accepted | NO COMPATIBLE WIRE PIN; no schema freeze, no PRECODE |

## Invariant: two different commitments
HR `placement COMMITTED` (only as eventual accepted issuer state) is HR ledger truth. DM `DepartmentAssignmentLink LINKED` is DM's own position relationship. Neither implies the other, nor job qualification or authorization to execute. DM may not issue HR employee numbers, transfer/rewrite HR career or treat a signed historical receipt as current. HR may not write DM position state. There is no distributed atomic transaction, shared DB, Arbeit engine, shadow Workflows or global retry runner. UNKNOWN remains UNKNOWN. For HR committed + DM crashed: read verified HR current state, then reconcile DM-only CAS link; never repeat hiring blindly. For occupied seat: preserve HR commitment as conflicting, hold and escalate, not evict/rewrite.

## Version pinning and signoff gate
A valid future signoff packet must contain: exact HR issuer contract ID/version/schema digest/source SHA; HR authorized approver and timestamp; DM consumer contract ID/version/digest/SHA and authorized approver; exact agreed scope/tenant and security issuer ports; idempotency, lookup/currentness and receipt authenticity policy; revocation/transfer/discharge; compatibility test plan and future observed evidence; limitations, change/deprecation and rollback path. **No signatures or approved versions are present here.**

Approval transitions: `DOCUMENTS_PINNED → ISSUER_DECISION_PENDING → HR_ISSUER_APPROVED → DM_CONSUMER_APPROVED → EXTERNAL_TRUST_APPROVED → QA_EVIDENCE_PASS → PRECODE_AUTHORIZED`. Current actual status: `DOCUMENTS_PINNED / ISSUER_DECISION_PENDING / BILATERAL NOT_SIGNED / PRECODE HOLD`. Do not skip gates or treat cross-written documentation as consent.

## Required explicit decisions
HR owner: employerRef semantics, placement cardinality, canonical receipt/envelope/authenticity, currentness query, scope/privacy, transfer/discharge and version/error codes. DM owner: legal-employer mapping, seat capacity/CAS, pending repair state and privacy. Security/KMS/Workflows/Work Management/employer Package owners: authorization, secret/signature, in-flight effects, drain, clearance. Each must record a separate issuer decision; no automatic proxy approval.

## No execution
No code, executable tests, migrations, CI, deployments, contract acceptance or real placement operations. Documentary comparison is not observed conformance. DOC REVIEW / PRECODE HOLD / R1 NO-GO / RELEASE HOLD.
