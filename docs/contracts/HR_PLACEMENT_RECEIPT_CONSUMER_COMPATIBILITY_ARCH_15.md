# DM-HR-COMPAT-15 — Consumer compatibility assessment of HR freeze candidate
Date: 2026-10-14
Status: DOCUMENTARY PIN VERIFIED / CONSUMER NOT APPROVED / EXTERNAL ISSUER PENDING
HR issuer-owned frozen review candidate: `musampakiki/steinbrenner-team-agents`, branch `agent/team-agents-development`, `docs/contracts/HR_PLACEMENT_RECEIPT_FREEZE_CANDIDATE_ARCH_15.md`, Git blob `bc942a0f5d1834a85df53d5f75fdef495810647b`, documentary ID `HR-PLACEMENT-RECEIPT-0.1-FC1`. Issuer candidate creation commit `84c775e79763728d6d6c1935dfc6ff5da3fd52fd`. Evidence pin is **not** an accepted API contract.

## Consumer-specific coverage
| Gate | DM expectation | Finding |
|---|---|---|
| C15-01 owner | HR issues employment/placement, DM issues position links | documentary alignment, not API signoff |
| C15-02 immutable identity | verified HR placementRef+agentRef+revision; no employee number minting | target aligned, accepted schema missing |
| C15-03 provenance | authenticated HR issuer, tenant/employer/actor and signed receipt | BLOCKED: KMS/Auth trust and wire format |
| C15-04 currentness | get-by-operation and current HR revision, reject historical/stale | candidate described, guarantees unsigned |
| C15-05 idempotency | separate HR/DM dedup, conflict for mismatched payload | target aligned, retention and digest not specified |
| C15-06 partial commit | HR COMMITTED/DM failed → DM-only CAS repair | candidate aligned, fixtures not run |
| C15-07 seat capacity | concurrent/stale/deleted seat → HOLD not silent HR compensation | DM-local candidate, no executable proof |
| C15-08 transfer/exit | verified HR state and external drain/PEP revocation | BLOCKED external Workflows/Work/PEP |
| C15-09 privacy | minimum scoped read, tenant denial, no cross-employer data | BLOCKED Auth/Tenancy approval |
| C15-10 compatibility | accepted HR version/digest, accepted DM consumer version, tests/signatures | BLOCKED both owners and QA |

## Signoff condition
DM owner must explicitly review exact accepted HR issuer schema and port with SHA, semantic version and authorized signoff, then publish its own versioned consumer contract/revision and compatibility decision. Current `0.1-fc1` is documentary, so consumer can mark **PINNED_FOR_REVIEW only**, not `COMPATIBLE`. Neither HR placement nor DM association grants business qualification/clearance or platform permissions. No shared Arbeit runtime, no private HR SDK/DB dependency, no distributed transaction.

## Counterexamples requiring eventual negative fixtures
Replay same placement operation after HR commits but DM times out; request key with changed digest; valid historical receipt with revoked placement; foreign tenant; forged issuer/signature; out-of-order events; occupied position; pending separation with protected effect UNKNOWN; clone with inherited position membership; employee name collision. No fixtures executed.

## Decision
`HR DOCUMENT_PIN_CONFIRMED / HR ISSUER_APPROVAL OPEN / DM CONSUMER_APPROVAL OPEN / BILATERAL_COMPATIBILITY_BLOCKED / PRECODE HOLD / R1 NO-GO`. This is a non-normative consumer mapping; HR retains sole authority over issuer contract.
