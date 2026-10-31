---
id: ARBEIT-ARCH-28-BLOCKER-LEDGER
date: 2026-10-31
status: DOCUMENTARY_BLOCKER_AUDIT
source_protocol: docs/governance/protocols/2026-10-31_ARBEIT_ARCH_28_RETENTION_AND_CONTRACT_BLOCKERS.md
---
# ARBEIT-ARCH-28 — Retention and Issuer Contract Blocker Ledger

## Sources inspected
- `AGENTS.md`, blob `d8e47dc7bac8ab2414b6557f4fae618940dee481`.
- `SESSION_PROTOCOL_INDEX.md`, blob `8a18805bb86124b1bcf3e88362e08ea31158d176`.
- `docs/governance/CANONICAL_REFERENCES.md`, blob `57789d0d9f1be74953e2aacb04ffb863ead5fff4`.
- `docs/governance/ARBEIT_ADR_02_DM_CONSUMER_ADOPTION.md`, blob `1de578de59cba76d1123215644b00f0db3f3c532`.
- `docs/governance/protocols/2026-10-14_ARBEIT_ARCH_27_OWNER_CHOICE_READINESS.md`, blob `755004b616501b95ebeea82801b21793eaa92679`.

## Confirmed position
- ARBEIT is a logical classification only: no shared engine, database, build or synchronized release train.
- Department Management is a consumer of HR-issued placement/retention evidence; local mappings do not transfer issuer authority.
- ARBEIT-ADR-02 adoption records proposed 180-day operation evidence and 365-day minimized tombstone windows as proposals, not legal or issuer-approved policy.
- R1 `NO_RECORD_CONFIRMED` is disabled for automatic replay. R2 optional enablement requires HR issuer completeness proof and independent acceptance.
- DM must preserve local operation reference, digest, status and reconciliation hold; a vanished HR operation is not proof that it never committed. No automatic rehire after timeout or retention expiry.
- ARBEIT-ARCH-27 closed as a documentary packet while HR retention/no-record feasibility and HR/DM acceptance remain unsigned.

## Decision and evidence ledger
| ID | Required owner evidence/decision | Current status | Consequence |
|---|---|---|---|
| ARCH28-01 | HR issuer chooses and approves retention policy and its release-independent application | BLOCKED | Do not treat 180/365 days as accepted policy |
| ARCH28-02 | HR issuer proves completeness and trustworthy negative lookup semantics for the relevant retention window | BLOCKED | Keep R1 negative-proof automatic replay disabled |
| ARCH28-03 | Exact HR public contract path, version, blob SHA, error taxonomy and currentness semantics | BLOCKED | Consumer mapping is not an accepted wire contract |
| ARCH28-04 | Signed HR issuer acceptance and signed DM consumer acceptance | BLOCKED | No bilateral contract freeze |
| ARCH28-05 | Auth/KMS/Audit owner review for trust, retention, evidence minimization and auditability | OPEN | No cross-owner approval inferred |
| ARCH28-06 | QA negative cases and MET source/threshold/privacy approvals | OPEN | No executable QA/MET work authorized |
| ARCH28-07 | Explicit scoped PRECODE authorization after DOC/GOV/QA/MET | BLOCKED | No tests, implementation, schema generator, CI, migration or deployment |

## Safe next action
Request a written HR owner decision for ARCH28-01..03, with exact issuer-owned source and SHA. Then prepare bilateral acceptance for HR and DM to sign. Keep unknown outcomes in reconciliation hold; never infer non-commit from timeout, disappearance, retention expiry or a consumer-side query miss.

## Gate
**DOC REVIEW / PRECODE HOLD / R1 NO-GO / RELEASE HOLD.** This is a documentary audit only. No tests or implementation performed; no owner approval is created by this document.
