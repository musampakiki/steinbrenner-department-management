# ARCH-22 — DM consumer recovery after HR outcome lookup
Status: DOCUMENTARY CANDIDATE / NOT SIGNED
HR FC4 evidence blob d1306a7e80492f11ac00ce25a9533142b24573b0.

| HR lookup evidence | DM local handling |
|---|---|
| KNOWN_REJECTED_PRE_INTAKE | Close request only with trusted matching HR rejection; no link |
| KNOWN_INTAKE_PENDING | HR_PENDING; no position link |
| KNOWN_INTAKE_UNKNOWN | UNKNOWN_HOLD; no blind retry |
| KNOWN_PLACEMENT_COMMITTED | Verify HR currentness then local DM position CAS; do not rehire |
| NO_RECORD_CONFIRMED | Retry only under separately accepted HR idempotency and freshness guarantee |
| INDETERMINATE or timeout | DM_LOCAL_TRANSPORT_UNKNOWN; hold and reconcile |
| AUTHORIZATION_DENIED | Deny; do not expose foreign tenant records |
| IDEMPOTENCY_CONFLICT | Hold and investigate canonical digest mismatch |

DM owns its local operation, staffing request, capacity and assignment links; HR owns agent identity, placement and career. No shared Arbeit ledger, no inferred job clearance. No accepted HR wire/DM signature, tests, code or PRECODE authorization.
