# ARCH-25 — DM consumer retention and negative-proof acceptance gate
Date: 2026-10-14
Status: DOCUMENTARY READY / CONSUMER UNSIGNED
HR source: FC4 candidate blob d1306a7e80492f11ac00ce25a9533142b24573b0; ARCH-24 HR review blob 2c7f5f913fc7af2e73aaf211ee268c26c643823c.
DM cannot select HR retention or invent issuer completeness. HR owner must publish accepted dedup, tombstone and lookup horizons, expiry and NO_RECORD_CONFIRMED evidence, exact contract version/schema SHA and security pins before DM consumer signoff.

## DM local decisions after lookup
KNOWN_PLACEMENT_COMMITTED: check authoritative HR currentness then DM position capacity/CAS; never repeat HR hire.
KNOWN_INTAKE_PENDING or KNOWN_INTAKE_UNKNOWN: hold; HR issuer recovery.
NO_RECORD_CONFIRMED: only accepted HR policy can authorize safe replay within verified horizon.
INDETERMINATE, retention expired, stale replica, missing verifier, timeout: DM_LOCAL_TRANSPORT_UNKNOWN / reconciliation HOLD, never infer noncommit.
ACCESS_DENIED: fail closed without tenant information leakage.
IDEMPOTENCY_CONFLICT: inspect canonical digest, no new placement.
HR commitment with full DM position: preserve HR fact and escalate local conflict; do not erase career history.

## DM acceptance gates
D25-01 Signed HR issuer contract, version, schema SHA and canonical request digest policy: BLOCKED.
D25-02 Accepted HR retention and dedup/lookup expiry semantics: BLOCKED.
D25-03 Negative-proof scope/freshness/writer fence or explicit no-negative guarantee: BLOCKED.
D25-04 Auth/Tenancy/KMS and privacy/audit approval: BLOCKED.
D25-05 DM-specific CAS, concurrency and owner signed compatibility: UNSIGNED.
D25-06 Observed QA/MET and separate scoped PRECODE: NOT AUTHORIZED.

No cross-module transaction, shared Arbeit ledger, private HR storage/API or executable test. DOC REVIEW / PRECODE HOLD / R1 NO-GO / RELEASE HOLD.
