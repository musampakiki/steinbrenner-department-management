# ARCH-20 — DM mapping of HR FC4 candidate
Date: 2026-10-14
Status: DOCUMENTARY DRAFT / NOT ACCEPTED
HR candidate: musampakiki/steinbrenner-team-agents, agent/team-agents-development, docs/contracts/schemas/hr-placement-receipt.0.1-fc4.candidate.schema.json, blob d1306a7e80492f11ac00ce25a9533142b24573b0.

| Observed fact | DM state | Allowed action |
|---|---|---|
| Verified PRE_INTAKE_REJECTION / REJECTED | REJECTED | preserve proof; no link |
| Verified INTAKE / PENDING | HR_PENDING | follow up with HR |
| Verified INTAKE / UNKNOWN | UNKNOWN_HOLD | issuer lookup; no replayed hiring |
| Verified PLACEMENT / COMMITTED | HR_PLACEMENT_RECORDED | check HR currentness and local position CAS before DM-only association |
| Network timeout, no HR receipt | DM_LOCAL_TRANSPORT_UNKNOWN | lookup by operation; do not invent HR UNKNOWN receipt |
| Foreign tenant or invalid authenticity | RECONCILIATION_HOLD | deny/redacted audit |
| HR committed but DM write failed | DM_LINK_PENDING | verify HR then retry local link, not HR hiring |
| Position capacity exhausted | CAPACITY_CONFLICT | hold and escalate |

Consumer-local timeout is never an issuer-authored HR receipt. A plain network error does not prove HR rejection. No fake intakeRef, receiptRef, agentRef or placementRef. Department structural cloning does not inherit staff, grants, credentials or tasks. HR owns employment records; DM owns positions and links. Both APIs remain candidate; Auth/Tenancy/KMS, Workflows, Domain PEP, HR signing/currentness and DM owner signoff OPEN. No tests/code/deployments or PRECODE authority.
