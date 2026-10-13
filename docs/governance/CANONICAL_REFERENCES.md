# Canonical references and ownership pins — DM-REF-01
Module: Department Management. Date 2026-10-14. Exact issuer versions require future refresh at acceptance.
| Owner | Canonical owner-controlled source | Known pin and status |
|---|---|---|
| Platform architecture | steinbrenner-paas/ARCH/ARBEIT_ADR_01_LOGICAL_BLOCK_INDEPENDENT_MODULES_2026-10-14.md | blob `1d407c991d44f1013baa3255f6c6aafe9f0c4785` ACCEPTED architecture |
| Platform architecture | steinbrenner-paas/ARCH/ARBEIT_ARCH_06_INDEPENDENT_MODULE_CONFORMANCE_MATRIX.md | blob `eb0dbf3159923502a765e2c44f3a3134684ce6c4` design gates |
| Platform integration | steinbrenner-paas/ARCH/ARBEIT_ARCH_08_DEPARTMENT_MANAGEMENT_PUBLIC_CONTRACTS_TARGET.md | blob `c1304ba9562e0607ae5de5e63c09c460b888d1a0` candidate cross-owner target |
| Platform governance | steinbrenner-paas/ARCH/ARBEIT_ARCH_09_DEPARTMENT_OWNER_AND_CONTRACT_ADOPTION_DECISION_PACKET.md | decision packet, not issued DM schema |
| Platform docs ownership | steinbrenner-paas/ARCH/PLATFORM_ADR_MODULE_OWNED_BLOCK_DOCS_VERSIONED_MATERIALIZATION_2026-10-13.md | blob `98049e1d4ce35b4d3b55ba17eddb9d1d9abaf1ce` ACCEPTED |
| Team Agents HR | steinbrenner-team-agents/docs/architecture/HR_AGENCY_BUSINESS_EMPLOYER_BOUNDARY.md | blob `820d25c37a6af16f0f3d43686a98d4e8a630da67` UNACCEPTED integration ports |
| Team Agents HR | steinbrenner-team-agents/docs/contracts/HR_EMPLOYER_SCHEMA_OWNER_ALIGNMENT_TA_DOC_11.md | blob `bebecbbadbc6dd420005f9c076b0432b9cdf363e` CANDIDATE |
Kernel, Workflows, App Installation, Auth/RBAC, Tenancy, KMS, Audit, Work Management, Organization Composition and Department Packages: exact owner-issued public contract version/SHA **NOT PINNED**, cross-owner approval OPEN. Do not fabricate acceptance.
Precedence: issuing owner's public versioned schema controls its domain. Local consumer mappings are not competing truth. Documentation-only platform targets do not change owner API.

## ARBEIT-ARCH-11 evidence pin update (2026-10-14)
- Team Agents HR candidate schema: `docs/contracts/schemas/hr-employer-integration.candidate-0.1.schema.json`, branch `agent/team-agents-development`, blob `57012796fa10490db2aaf3ec1e87fa6706f86935`, schema ID `urn:steinbrenner:ta:hr-employer:candidate-0.1`. This is **UNACCEPTED**, not a supported API contract version.
- HR external employer standard blob `a4e0ba6e52b0c048ab562d30fb523e62ee1d1af0`; no acceptance of wire.
- Current module draft issuer policy: [ISSUER_VERSIONING_POLICY](../contracts/ISSUER_VERSIONING_POLICY.md); HR read-only review [HR_ISSUER_PIN_AND_COMPATIBILITY_REVIEW](../contracts/HR_ISSUER_PIN_AND_COMPATIBILITY_REVIEW.md); [cross-owner approval ledger](CROSS_OWNER_APPROVAL_LEDGER.md).
