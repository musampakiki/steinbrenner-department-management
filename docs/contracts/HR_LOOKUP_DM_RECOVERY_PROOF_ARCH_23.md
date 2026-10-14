# ARCH-23 — Department Management HR lookup recovery proof obligations
Date: 2026-10-14
Status: DM DOCUMENTARY CONSUMER CANDIDATE / UNSIGNED
HR FC4 source blob `d1306a7e80492f11ac00ce25a9533142b24573b0`. HR issuer owns operation lookup semantics and retention: DM cannot set HR negative-proof guarantees.

## Consumer decision matrix
| Issuer evidence | DM disposition |
|---|---|
| Verified KNOWN_REJECTED_PRE_INTAKE | reject locally, preserve receipt evidence; no link |
| Verified KNOWN_INTAKE_PENDING | HR_PENDING; no link |
| Verified KNOWN_INTAKE_UNKNOWN | UNKNOWN_HOLD; lookup until reconciled |
| Verified KNOWN_PLACEMENT_COMMITTED | verify current HR revision and DM position CAS; only DM-local repair |
| Verified IDEMPOTENCY_CONFLICT | CONFLICT_HOLD; compare local canonical digest, no fresh HR hire |
| HR-authoritative NO_RECORD_CONFIRMED | reissue only if contract specifically permits safe retry under same scope/key/horizon |
| INDETERMINATE / expired horizon / stale HR reader | DM_LOCAL_TRANSPORT_UNKNOWN or RECONCILIATION_HOLD; no inferred noncommit |
| Unauthorized/foreign tenant | DENY with redacted audit; no disclosure |
| Absent response/timeout | DM_LOCAL_TRANSPORT_UNKNOWN; durable local operation ID, request hash and safe issuer lookup |
| HR COMMITTED, DM capacity already occupied | CAPACITY_CONFLICT; preserve HR fact and escalate, do not silently evict |

## Required cross-module recovery evidence
DM keeps tenant-scoped operationRef, actor/authority ref, canonical request digest, requisitionRef, department/position expected revision, HR source contract/version+receiptRef+placementRevision, last authoritative freshness result, DM link CAS revision, attempt/correlation ID and redacted audit marker. HR retains identity/career/outcome truth, not DM capacity. Independent stores and replaceability. No repeated hiring from ambiguity. DM cannot assert exactly-once cross-owner execution, and local LINKED never provides employer job permission.

## Retention dependency
Until HR accepts a dedup/lookup horizon, DM must HOLD uncertain operations; never default to 24h, 7d or arbitrary expiry. Recovery after HR retention expiry needs an owner-approved fallback (e.g. wider authoritative placement history) before any replay; `NOT_FOUND` under privacy-denied scope remains ambiguous.

## Future documentary negative-proof fixtures
DM23-01 lost HR response after placement; DM23-02 HR retention expired; DM23-03 same key different digest; DM23-04 stale HR replica; DM23-05 forged receipt; DM23-06 cross-tenant lookup; DM23-07 HR committed but local CAS full; DM23-08 cancellation race; DM23-09 placement revoked; DM23-10 DM crash after link before response. No tests executed.

Gate: HR issuer accepted query+retention contract SHA/version, Auth/KMS/Tenancy signatures, DM owner approved consumer version, QA/MET observed results and separate PRECODE. ALL OPEN. DOC REVIEW / PRECODE HOLD / R1 NO-GO.
