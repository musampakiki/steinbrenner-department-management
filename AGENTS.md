# Department Management — mandatory engineering rules
Repository: musampakiki/steinbrenner-department-management
Working branch: agent/department-management-development; never write main without separate explicit approval.
1. Before every substantial session read this file, SESSION_PROTOCOL_INDEX.md, latest relevant protocol, docs/governance/CANONICAL_REFERENCES.md and current owner contracts.
2. First GitHub file write of substantial session is dated OPEN protocol. Last file write is CLOSED protocol; update index before closure.
3. This repository issues **only** Department Management module-owned identities, schemas, published ports and internal rules after explicit owner acceptance. Platform cross-owner decisions remain in steinbrenner-paas; HR, Kernel, Workflows, security, employers issue their own truth. Proposed contracts remain CANDIDATE until signed.
4. Arbeit is only a logical group. Independently owned code, libraries, dependencies, storage, builds, versions, compatibility and replacement; no Arbeit engine/shared DB or private cross-module imports.
5. No new employee/clone identities or numbers, employment or qualification issuing, work plans/runs, scheduling, Kernel binding, auth/permissions, leases, tokens or other-domain business effects. Clone only approved structure with fresh IDs and zero staffing/privileges.
6. DOC → GOV → QA → MET → explicit PRECODE authorization → test-only RED → minimal source → observed GREEN. Current DOC REVIEW / PRECODE HOLD / R1 NO-GO. No executable changes, schema generator, tests, migration, CI or deployment authorized.
7. Confirm exact source SHA/contract issuer pins and classify CONFIRMED, REPORTED, INFERRED, UNKNOWN, BLOCKED. Do not record secrets, JWT, tokens, raw logs, private HR data or private screenshots in Git.
8. No change to Empty Host or steinbrenner-platform-control. No main commits. Upstream source ownership is not transferred by local consumer mappings.
