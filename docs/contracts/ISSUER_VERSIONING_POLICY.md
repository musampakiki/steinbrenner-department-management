# DM-CONTRACT-VERSION-01 — Issuer contract versioning and acceptance
Date: 2026-10-14
Status: CANDIDATE / NOT APPROVED / NOT EXECUTABLE
Issuer candidate: Department Management (this repo). This is a module-owned draft policy, not accepted transport/API.

## Distinct version dimensions
- Module release/build identity, immutable artifact digest and state migration version.
- Public contract family ID and semantic version, independently evolved from module release.
- Template content version/digest, instance revision and clone-allowlist revision.
- HR and other consumed interface version + immutable upstream contract blob SHA, acceptance state and trust context.
- Department Package extension contract/version, and per-tenant policy revision.
Never infer compatibility from matching numbers across dimensions, an Arbeit taxonomy tag or file placement.

## Candidate families
DM.TemplateCatalog, DM.DepartmentInstances, DM.StructuralClone, DM.DepartmentPositions, DM.StaffingRequests, DM.PlacementLinks, DM.DepartmentEvents. These are descriptive identifiers, NOT endpoint names, accepted DTOs or wire versions.
A first issuer candidate may be labeled `0.1.0-draft` solely for review. It must **never** be represented as an accepted `v1` or a deployed service.

## Publication transitions and objective proofs
`DRAFT → OWNER_REVIEWED → OWNER_ACCEPTED → CROSS_OWNER_COMPATIBLE → QA_VERIFIED → RELEASE_AUTHORIZED`; rejection/withdrawal is independently recorded. Owner acceptance does not automatically prove consumer agreement, installed eligibility, staging tests or release. Drafts can change with tracked revisions; accepted/public contract versions and schemas are immutable and addressable with digest and commit SHA. Compatible extensions require accepted issuer and consumer evidence; breaking changes require a new major contract version, explicit migration, compatibility/deprecation window and consumer opt-in. Security-tightening changes require issuer policy review even when fields appear backward compatible.

Proposed `ContractReleaseReceipt` (governance concept, NOT runtime schema): issuer, repo, branch/tag, contract family, semver, source commit SHA, content blob SHA, schema digest, owner approval reference, supported consumers, supported versions, incompatibilities, deprecatedAt, rollback constraints, evidence links. No such accepted receipt exists yet.

## Compatibility classification
- Patch: semantics and required fields unchanged; bug clarification only subject to compatibility proof.
- Minor: genuinely additive optional capabilities, older consumers remain valid and safe.
- Major: changed identifiers, required fields, enum semantics, authorization, idempotency, revisions, clone permissions, privacy, failure semantics or destructive lifecycle changes.
A behavior that introduces new privileges or changes tenant visibility cannot be silently categorized as minor.
Consumer has to pin the exact *accepted* issuer version; draft upstream SHA is an evidence pin only, not a usable runtime dependency.

## Change and rollback gate
Every candidate diff must produce: change rationale, before/after exact digest, source owner signatures, negative abuse cases (clone secrets, employee ID spoofing, cross tenant, stale CAS, replay), HR and other consumer impact, per-version compatibility matrix, migration/drain/rollback plan for in-flight staffing and Workflows, unresolved UNKNOWN reconciliation, audit obligations and withdrawal/deprecation routing. No automatic zero-downtime hot swap. No implementation until DOC/GOV/QA/MET and explicit PRECODE.
