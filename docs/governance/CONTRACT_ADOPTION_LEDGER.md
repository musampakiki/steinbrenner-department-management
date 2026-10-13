# ARBEIT-ARCH-10 — Contract adoption and owner decision ledger
Status: MODULE DOCS BOOTSTRAPPED / ISSUER API DRAFT / EXTERNAL APPROVALS OPEN
Source: platform ARCH-08 target blob c1304ba9562e0607ae5de5e63c09c460b888d1a0; ARCH-09 owner decision packet; no import of upstream source as competing normative API.
| Concern | Module-local target | Adoption status |
|---|---|---|
| Ownership/identity/structure | MODULE_BOUNDARY.md, TEMPLATE_CLONE_LIFECYCLE.md | DRAFT REVIEW |
| Template versions/clone safety | TEMPLATE_CLONE_LIFECYCLE.md | DRAFT REVIEW |
| Commands/events/idempotency | PUBLIC_PORTS.md | DRAFT REVIEW / NO SCHEMA |
| HR placements and discharge | HR_CONSUMER_MAPPING.md | CONSUMER DRAFT / HR APPROVAL OPEN |
| Full versioned JSON schemas/transport | none | NOT ISSUED |
| Kernel, App Installation, Workflows, Auth, Tenancy, KMS, Audit | CANONICAL_REFERENCES.md | CONTRACT PINS OPEN |
| Work Management/Organization Composition/Packages | MODULE_BOUNDARY.md | ISSUER APPROVAL OPEN |
| QA/metrics/runtime/prod | future artifacts | NOT ASSESSED / NOT AUTHORIZED |
Module documentation was independently authored, not a bytewise normative transplant. Require owner signoff of each contract, versioned immutable contract digest, compatibility and negative fixtures, exact external issuer pins and consumer approval; then update upstream locator with SHA, without erasing ARCH-08 history. No DOC/GOV/QA/MET/PRECODE promotion inferred.

## ARBEIT-ARCH-11 checkpoint
- Module contract versioning policy `docs/contracts/ISSUER_VERSIONING_POLICY.md`: CANDIDATE `0.1.0-draft` only; no accepted wire or source freeze.
- HR source evidence `docs/contracts/HR_ISSUER_PIN_AND_COMPATIBILITY_REVIEW.md`: exact candidate schema blob `57012796fa10490db2aaf3ec1e87fa6706f86935`, not an accepted issuer contract.
- Cross-owner approvals `docs/governance/CROSS_OWNER_APPROVAL_LEDGER.md`: external owner signatures/pins remain BLOCKED_EXTERNAL_OWNER. No execution evidence, QA/MET or PRECODE grant.
