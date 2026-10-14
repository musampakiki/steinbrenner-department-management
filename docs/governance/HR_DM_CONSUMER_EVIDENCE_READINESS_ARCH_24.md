# ARCH-24 — DM consumer evidence consolidation and signoff readiness
Date: 2026-10-14
Status: DOCUMENTARY AUDIT COMPLETE / DM SIGNOFF BLOCKED
Source ownership: HR issues operation outcomes and receipts; DM owns staffing requests, positions, links and local retry state. No shared Arbeit service or database.

## Pinned read-only evidence
HR FC4 issuer candidate blob d1306a7e80492f11ac00ce25a9533142b24573b0.
HR ARCH-21 persistence/lookup blob eb217a3f9945a5d8ff98a065cd290f1eff57bad5.
HR ARCH-22 ledger blob 2e23d518db663686830853e65d2eb4f8b12a2bce.
HR ARCH-23 failure/retention blob bf285c20bed4764adb5b375b4e09bae91ea171b5.
DM ARCH-21 consumer blob 29fb9f959e375dbe4b334b4729bd8f7e1a3fd906.
DM ARCH-22 mapping blob 513a053d1cfd0f289d38b1c6a7950e77c2b1e6a4.
DM ARCH-23 proof requirements blob 0e70e0a66b973d25a2a4f0298f0e365413294587.
All are Git document pins, **not accepted HR API version pins or signatures**.

## Already covered, no repetition
Verified HR PRE_INTAKE_REJECTION, recorded INTAKE/PENDING or UNKNOWN, historical PLACEMENT/COMMITTED, DM_LOCAL_TRANSPORT_UNKNOWN, recovery after HR COMMITTED with DM failure, independently checked HR currentness and DM seat CAS are documented in ARCH-21–23. No new DM DTO or issuer semantics authorized.

## DM owner signoff blockers
D24-01 HR owner accepted wire/schema identity/version and exact SHA with signed decision: BLOCKED_EXTERNAL_OWNER.
D24-02 HR issuer guaranteed dedup/lookup horizon and safe replay after expiry: OPEN.
D24-03 HR issuer authoritative NO_RECORD_CONFIRMED conditions, writer fence and stale replica treatment: OPEN.
D24-04 trusted tenant/employer scope and signature verifier (Auth/KMS/Tenancy): BLOCKED_EXTERNAL_OWNER.
D24-05 DM local position capacity/CAS, recovery on conflict, clone zero-staff invariant and privacy limits: CANDIDATE / NO QA.
D24-06 separate Workflows/Work Management/domain effect reconciliation and clearance: BLOCKED_EXTERNAL_OWNER.
D24-07 observed fault-injection QA/MET, signed DM compatibility decision and explicit PRECODE: NOT_EXECUTED / UNSIGNED.

## Decision
DM cannot use a missing/expired/denied HR lookup to assume noncommit. HR-issued COMMITTED is historical employment fact, not automatically current HR state nor DM LINKED nor employer clearance. A consumer-only timeout remains DM-local UNKNOWN_HOLD. For recovery after HR COMMITTED and DM failure, retry DM-only CAS after verified HR currentness, never blind second HR placement.
Current verdict: CONSUMER DOCUMENTATION CONSOLIDATED; BILATERAL COMPATIBILITY NOT ESTABLISHED; NO ACCEPTED API OR PRECODE. HOLD / R1 NO-GO / RELEASE HOLD.
