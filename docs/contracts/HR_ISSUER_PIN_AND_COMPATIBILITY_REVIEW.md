# DM-HR-PIN-01 — Team Agents HR issuer evidence pins and consumer mapping
Date: 2026-10-14
Status: READ_ONLY_SOURCE_PIN_CONFIRMED / HR_WIRE_UNACCEPTED / INTEGRATION_BLOCKED
Repository: musampakiki/steinbrenner-team-agents
Source branch: agent/team-agents-development

## Exact pinned upstream candidate artifacts
| Upstream path | Git blob SHA | Semantic status |
|---|---|---|
| docs/contracts/schemas/hr-employer-integration.candidate-0.1.schema.json | `57012796fa10490db2aaf3ec1e87fa6706f86935` | JSON Schema 2020-12; `$id=urn:steinbrenner:ta:hr-employer:candidate-0.1`; documentary only, oneOf union is NOT a transport |
| docs/contracts/HR_EMPLOYER_SCHEMA_OWNER_ALIGNMENT_TA_DOC_11.md | `bebecbbadbc6dd420005f9c076b0432b9cdf363e` | documentary candidate NOT ACCEPTED |
| docs/development/EXTERNAL_EMPLOYER_INTEGRATION_STANDARD.md | `a4e0ba6e52b0c048ab562d30fb523e62ee1d1af0` | design standard CANDIDATE |
| docs/architecture/HR_AGENCY_BUSINESS_EMPLOYER_BOUNDARY.md | `820d25c37a6af16f0f3d43686a98d4e8a630da67` | HR / employer partition, proposed ports |

These pins provide reproducible *read-only evidence*, NOT approved HR public-port versions. No HR write or contract adoption was performed in this session.

## Candidate mapping — strict authority split
| HR candidate schema definition / fields | DM consumer requirement | Integration gap |
|---|---|---|
| `staffingRequest`: employerRef, requisitionRef, requestedCount, scopeRef, optional idempotencyRef | DM owns local requestId/departmentId/positionId and requisition version; maps authorized external employerRef and scope | accepted employer identity, canonical request fingerprint, idempotency and tenant/currentness missing |
| `agent`: agentInstanceRef, employeeNumber, givenName, familyName, optional parentAgentRef/nameVersion | HR identity only; DM stores limited opaque agentRef and HR receipt reference | HR-signed issuer identity, privacy and rename cache invalidation contract pending |
| `placement`: placementRef, employerRef, requisitionRef, agent, revision, status | HR authoritative placement; DM links only after verified current receipt and local CAS | status PENDING/PLACED/SEPARATION_PENDING/CLOSED are candidate; event issuer, ordering, signed receipt, replay rules not accepted |
| `discharge`: placementRef, issuerRef, reconciliationState, dischargeEvidenceRef, optional successorAgentRef | independently verify work drain/domain receipts and accepted HR discharge before detach/archive | UNKNOWN effects, HR acceptance and revocation ordering unresolved |
| `careerEvent`: agentInstanceRef, employeeNumber, eventRef, issuerRef, eventType, occurredAt | no editable HR history in DM; may retain scoped immutable reference only | tenant visibility, historical correction/retention and signature missing |
| `qualification`/`clearance` entries in HR dossier | NO HR qualification ownership. Employer/Department Package issues business passport/clearance with independent PEP | these defs do not make Team Agents issuer of employer competence; prohibit inherited credentials |
| `workday`/`plan`/`task`/`shift`/`taskOutcome` | NOT owned by DM; Work Management/employer and external Workflows/domain effect issuers | never use HR candidate union as permission to implement work scheduler |

## Conflict and safety review
1. HR candidate `staffingRequest` does not define departmentId or positionId; DM may not silently extend HR wire. Need issuer-approved extension/mapping and compatibility.
2. `placement.status=PLACED` does not imply DM association, workplace qualification, clearance, active task eligibility or any platform authorization.
3. The HR schema does not prove signed authenticity, actor scope, tenant isolation, CAS races, idempotent cross-owner effects or durable event delivery. These require accepted issuer envelopes and QA evidence, not JSON Schema alone.
4. Clone: DM structural clone starts with no HR placement or employee number; HR agent clone itself is separate and never inherits employer passport.
5. Transfer/termination may leave HR and DM in distinct pending states; signed receipts/reconciliation before detachment. Timeout means UNKNOWN, not absence of HR commitment.
6. Privacy: display names and employeeNumber are HR-sourced identifying data; DM should retain only minimal refs and not expose global HR directories.
7. No shared transaction, DB, private SDK, shared Arbeit engine or imported HR schema as DM-owned normative file.

## Required HR issuer approval
Provide exact accepted HR endpoint/event contract version, immutable public source/schema SHA, actor/tenant authorization requirements, identity and placement receipt semantics, vacancy mapping, revision/CAS/idempotency, privacy and retention, discharge ordering, error/UNKNOWN policy, signed review and supporting fixture references. DM issuer must separately sign consumer mapping and compatibility. Until both: `BLOCKED_EXTERNAL_OWNER`.
