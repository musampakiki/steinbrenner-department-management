# Department Management public port candidate registry
Status: CANDIDATE / ISSUER REVIEW NOT SIGNED / NOT A WIRE API / NO IMPLEMENTATION.
Issuer candidate: this independent Department Management module. The product owner's assignment of repo does not automatically approve the endpoints, field spellings, transport or wire format.
| Candidate port group | Commands/queries | Key invariants |
|---|---|---|
| Template catalog | Create/Update draft, Publish, Deprecate, Retire, Get/List versions | published digest immutable, owner/tenant scope, compatibility pins and CAS |
| Department instance | Create from template, Get/List, Update structure, Archive/Restore | fresh ID/revisions, immutable provenance, stale revision rejected, archive needs discharge |
| Structural clone | CloneDepartmentStructure | current source snapshot+allowlist, fresh ID/positions, empty staffing and zero copied authority |
| Position | Get positions, Update approved seat structure | structural capacity only; no employment/privilege issuer |
| Staffing request | Request/Cancel/Get staffing, link verified HR placement, detach after discharge | HR owns employment; idempotency, 2-owner reconciliation, no fake IDs |
| Events | TemplatePublished, DepartmentStructureChanged, DepartmentArchived, StaffingRequestStateChanged | candidate events: trusted issuer, scoped tenant, eventId, owner revision, correlation and dedup |
No accepted REST/gRPC paths, JSON schema, DTO shape, enum, error wire codes or event transport yet. Potential fields `tenantId, actorRef, operationId, idempotencyKey, requestDigest, expectedRevision, ownerContractVersion, currentnessPin, issuerReceiptRef` are **candidate**, not production schema. Exactly-once delivery/distributed transactions are not claimed.
Errors: unauthorized, tenant mismatch, invalid state/version, CAS conflict, incompatible extension, idempotency conflict, external owner unavailable, pending reconciliation and UNKNOWN are proposed semantic categories. Never convert UNKNOWN to committed.
Public contract acceptance needs signed issuer revision and precise foreign-owner contract pins, negative/positive fixtures, security review and documented compatibility/rollback.
