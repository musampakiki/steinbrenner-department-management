# ARCH-27 — DM consumer acceptance readiness
Date: 2026-10-14
Status: DOCUMENTARY / UNSIGNED
HR FC4 schema blob d1306a7e80492f11ac00ce25a9533142b24573b0; HR ARCH-26 audit blob c17deafa173712832ef1630fde1122ae8668c252.

HR must sign retention/dedup/replay period, and explicit enable/disable decision on NO_RECORD_CONFIRMED. If disabled or not provable, DM holds unknown outcomes; NOT_FOUND never permits blind HR hiring replay. HR committed placement requires verified currentness and DM-only seat CAS. Auth/KMS/Tenancy, HR issuer contract version/SHA, Workflows/drain, DM owner signoff and QA/MET all remain OPEN. No cross-module shared state, no runtime code/tests/PRECODE. DOC REVIEW / R1 NO-GO.
