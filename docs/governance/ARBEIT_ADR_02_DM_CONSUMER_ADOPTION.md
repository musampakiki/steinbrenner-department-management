# ARBEIT-ADR-02 — DM consumer adoption
Date: 2026-10-14
Status: ARCHITECTURAL DIRECTION ADOPTED / HR API AND DM SIGNOFF OPEN

Reference HR ADR-02 owner document in steinbrenner-team-agents, branch agent/team-agents-development. R1 internal testing, R2 commercial with unknown gap. HR retention is release-independent. Proposed engineering windows: 180 days operation evidence and 365 days minimized tombstone (not legal/issuer-approved). DM never assumes a vanished HR operation is uncommitted. R1 NO_RECORD_CONFIRMED disabled for automatic replay; R2 optional after HR issuer completeness proof and independent acceptance.

DM preserves local operationRef, digest, status and reconciliation hold; trusted historical HR COMMITTED requires fresh HR placement/currentness followed by DM-only position CAS. No automatic HR rehire after timeout or retention expiry. Arbeit has no shared DB or runtime. DM contract signer, HR retention signoff, Auth/KMS/Audit review and QA/MET remain OPEN. PRECODE HOLD / R1 NO-GO.
