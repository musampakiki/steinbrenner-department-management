# ARBEIT-ARCH-11 — Issuer Versioning, HR Contract Pinning and Cross-Owner Approvals
Date: 2026-10-14
Status: CLOSED — DOCUMENTARY PINNING ONLY / EXTERNAL OWNER APPROVALS OPEN / PRECODE HOLD / R1 NO-GO
Repository: musampakiki/steinbrenner-department-management
Branch: agent/department-management-development; main untouched.
ARCH-10 predecessor CLOSED protocol blob 2efc90cbac2afd25734f9f9ce6c9461a7bb769d1.
Current module baseline: AGENTS.md blob d8e47dc7bac8ab2414b6557f4fae618940dee481; PUBLIC_PORTS.md blob 23b327e2006fa5758cce57c73f9968a2b2b82d43; HR_CONSUMER_MAPPING.md blob 84f7fc5bed119b9221544328da30331d698dc76b.
HR exact candidate source: Team Agents docs/contracts/schemas/hr-employer-integration.candidate-0.1.schema.json blob 57012796fa10490db2aaf3ec1e87fa6706f86935; TA-DOC-11 blob bebecbbadbc6dd420005f9c076b0432b9cdf363e; TA-DOC-10 blob a4e0ba6e52b0c048ab562d30fb523e62ee1d1af0. These are *candidate* not accepted public HR wires.
Plan: versioning policy and issuance stages; HR exact read-only pin and semantic mapping with conflicts; cross-owner approval ledger; update references, adoption/index; close protocol last.
No code, tests, production schema freeze, CI, installation, migrations, deployments or other repo mutation authorized.

## Closure / exact write evidence
- OPEN first GitHub file write `cb96faada5df90ee8c8a11ae9ce281497a57317f`.
- Issuer version policy `docs/contracts/ISSUER_VERSIONING_POLICY.md` created `ff938aa7cbb94be3d75257438e310c3a4b096710`, DRAFT not accepted.
- HR issuer evidence mapping `docs/contracts/HR_ISSUER_PIN_AND_COMPATIBILITY_REVIEW.md` created `d1ce82e4a3c67ec029535f07913befc560d6162d`, candidate upstream HR schema blob `57012796fa10490db2aaf3ec1e87fa6706f86935`.
- Cross-owner approvals `docs/governance/CROSS_OWNER_APPROVAL_LEDGER.md` created `8503d45245acf159bc1abcf6ae80cc9c0c6eba4d` (12 entries, no asserted approval).
- CANONICAL_REFERENCES.md updated `c21276a08c4eaab2f87837cc39da13cd3a8a3374`; CONTRACT_ADOPTION_LEDGER.md updated `b65f008156500feeef76a076ffa5e285fe6061f2`; SESSION_PROTOCOL_INDEX.md updated `6148e9a3bb589c3c0289798d92497864e1a2b0c7`.
- README.md attempted update was blocked by tool; not claimed committed and not required for accurate index. This CLOSED protocol is the final write, its commit receipt returned by GitHub.
- No Team Agents, Kernel, Workflows, main, Empty Host, platform-control or executable changes. No tests, CI, release, deployment or accepted API/version. Owner approvals still OPEN; QA/MET NOT ASSESSED; PRECODE HOLD / R1 NO-GO / RELEASE HOLD.
- Next gate: request Team Agents HR issuer-approved port version and receipt/signature model; separately obtain Kernel/Workflows/App Installation/Trust pins before DM issuer API freeze or consumer integration claims.
