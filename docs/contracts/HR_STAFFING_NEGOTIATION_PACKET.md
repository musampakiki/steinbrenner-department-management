# DM-HR-NEG-01 — Bilateral HR staffing public-port negotiation packet
Date: 2026-10-14
Status: DM PROPOSAL / HR OWNER REVIEW REQUESTED IN DOCUMENT ONLY / NO ISSUER SIGNATURE
Contract candidate: DM employer-consumer profile `0.1-draft`; NOT an HR wire or production schema.

## Evidence and owner precedence
HR candidate JSON Schema `urn:steinbrenner:ta:hr-employer:candidate-0.1` in `musampakiki/steinbrenner-team-agents`, branch `agent/team-agents-development`, `docs/contracts/schemas/hr-employer-integration.candidate-0.1.schema.json`, Git blob `57012796fa10490db2aaf3ec1e87fa6706f86935`. Alignment TA-DOC-11 blob `bebecbbadbc6dd420005f9c076b0432b9cdf363e`. Source documents explicitly unaccepted. DM never becomes issuer of `placement`, employeeNumber, agent identity, transfer or HR employment history.

## Exact ownership and proposed operation semantics
| Stage | Candidate owner-issued port request | Proposed result; NEVER presume existing |
|---|---|---|
| DM staffing intake | HR issuer: accept/query requisition by trusted employerRef, tenant scope, DM operation/correlation and immutable requisition version | accepted/rejected/pending with durable intake reference; idempotent same request; mismatch conflict |
| Candidate selection | HR issuer: eligibility/candidate provision, possibly HR-authorized master/clone identity | HR agentRef only from authoritative issuer; never DM employee number allocation |
| Placement creation | HR issuer: record placement decision for accepted requisition and agent, with receipt query/replay | authoritative placementRef, agentRef, HR revision, committed/pending/rejected state and trusted issuer evidence |
| Placement currentness | HR issuer: get placement by immutable receipt/ref and optionally operationId | current placement status/revision, scope and effective state, signed/verified evidence, not stale event alone |
| Transfer | HR issuer: accepted move/split employer placement semantics with source/destination and causal proof | new destination truth/closed source truth only as HR decides; no guessed atomicity |
| Separation | HR issuer: begin/confirm separation and query receipt | accepted final/pending HR state, issuer current revision and discharge evidence; no forced close on UNKNOWN |
| Event consumption | HR issuer: revisioned placement events / notification semantics | eventId, aggregate sequence, publisher proof, replay window, dedup, gap recovery and snapshot lookup |

All names above are **negotiation labels**; not accepted endpoint names, DTO fields, event schema, signatures or transports. HR approves exact issuer contract, while DM separately accepts consumer mapping. Neither module may demand another module's private API.

## Required proposed receipt guarantees
For each placement operation, ask HR to normatively define: unique scope-bound operationId; authenticated issuer and effective tenant/employer; immutable placementRef; agentRef and HR employeeNumber when disclosure is permitted; requisitionRef/version; authoritative status with clear *committed vs pending* semantics; strictly scoped placement revision; commit time vs event delivery time; correlation and idempotency digest; accepted request identity; durable get-by-operation/get-by-placement recovery; evidence integrity and expiration/currentness rules; cancellation and revocation; error/UNKNOWN; cross-tenant disclosure controls. These are requested *semantics*, not an accepted field list.

A receipt is **not** an execution clearance, qualification proof, tenant authorization token, installation receipt or proof of DM position membership. A signed historic HR receipt proves history but does not automatically prove current placement; currentness lookup/revision policies must be agreed.

## Core negotiation decisions — all OPEN
- Define `employerRef` mapping to DM module vs specific employer/Department Package, `requisitionRef` mapping from DM staffingRequestId, `scopeRef` mapping to tenant/department; source candidate schema has no departmentId or positionId; never append invented fields to HR payload.
- Determine whether HR placement is unique per agent+employer+time, whether multiple concurrent placements are valid, and what employeeNumber may be disclosed to DM.
- Define HR-side idempotency retention, requestDigest mismatch, lookup under timeout, receipt authenticity, ordered/replayable events and snapshot/revision comparison.
- Agree rehires/transfers with active protected work, overlapping employer scope, discharge and terminal states; Work Management/employer/domain PEP issue drain/revocation/UNKNOWN evidence, not HR or DM.
- Define privacy, consent, audit/retention, soft visibility vs `NOT_FOUND`, cross-tenant and stale cached agent names.
- Define what HR verifies about DM request origin, actor/effective principal, installation eligibility and tenant PEP; external owners retain trust truth.
- DM owner signs its own versioned consumer profile only **after** HR issuer has accepted its contract and evidence; otherwise `BLOCKED_EXTERNAL_OWNER`.

## Negotiation outcome as of writing
NO HR approval received. Candidate read-only SHA pin is confirmed; no accepted HR public port, no runtime calls. This file is the formal proposed question packet for later HR owner review, not a claim a request was delivered or approved.
