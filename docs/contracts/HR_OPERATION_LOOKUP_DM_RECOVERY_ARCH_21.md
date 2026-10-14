# ARCH-21 — Department Management consumer lookup and timeout recovery
Date: 2026-10-14
Status: DM DOCUMENTARY MAPPING / HR ISSUER CONTRACT NOT ACCEPTED
Read-only HR FC4 source `musampakiki/steinbrenner-team-agents/docs/contracts/schemas/hr-placement-receipt.0.1-fc4.candidate.schema.json` blob `d1306a7e80492f11ac00ce25a9533142b24573b0`. The HR issuer-owned ARCH-21 persistence and lookup document supplies further candidate semantics; exact SHA must be pinned after creation.

## Local operation behavior
- Before outbound HR request, DM durably records its own scoped operationRef, tenant/employer authorization context references, canonical payload digest, requisition/position expected revision and correlation. DM persistence is never HR receipt issuance.
- If the HR reply is absent/timeout: `DM_LOCAL_TRANSPORT_UNKNOWN`, not `INTAKE UNKNOWN` and not `REJECTED`. Query accepted HR issuer get-by-operation under same scoped key; no blind hiring retry.
- Verified HR pre-intake business rejection → local REJECTED only after trustworthy issuer proof. Auth 401/403, privacy-filtered missing record or transport timeout does not prove HR business refusal.
- Verified HR registered INTAKE PENDING/UNKNOWN → local HR_PENDING / UNKNOWN_HOLD; never DM link. Verified HR PLACEMENT COMMITTED → separately verify current HR placement, then DM position capacity/CAS; position conflict → preserve HR truth and quarantine. DM link does not grant work permission.
- HR NO_RECORD_CONFIRMED is usable only if HR owner explicitly guarantees completeness within idempotency retention, authorization scope and concurrency boundary. Unavailable, privacy-denied, expired lookup or issuer indeterminate → HOLD.
- HR COMMITTED + DM crash: replay DM-local link using checked HR receipt/currentness, never replay HR placement creation by assumption. DM maintains own recovery/audit, not a shared Arbeit scheduler, shared DB or foreign private ledger.

## DM decision gaps
DM21-01 canonical request digest consistency across owners; DM21-02 issuer accepted lookup response semantic taxonomy; DM21-03 privacy-safe denial; DM21-04 HR idempotency expiry and replay policy; DM21-05 currentness revision and revocation; DM21-06 DM position CAS and capacity reconciliation; DM21-07 Auth/KMS signature verifier; DM21-08 Workflows/Work Management pending discharge; DM21-09 QA/MET and bilateral signature. All OPEN.
No executable tests, API approval, code, migration, CI or PRECODE. PRECODE HOLD / R1 NO-GO / RELEASE HOLD.
