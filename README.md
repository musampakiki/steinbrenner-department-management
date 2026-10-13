# Steinbrenner Department Management

Independent Department Management module within the **logical** Steinbrenner Arbeit classification. Not an Arbeit engine, shared executable, shared DB or synchronized release train.

**Documentary bootstrap:** ARBEIT-ARCH-10. **Status:** DOC REVIEW / PRECODE HOLD / R1 NO-GO. No accepted wire API or runtime implementation.

- [Module engineering rules](AGENTS.md)
- [Session protocol index](SESSION_PROTOCOL_INDEX.md)
- [Canonical source of truth](docs/governance/CANONICAL_REFERENCES.md)
- [Module boundary](docs/architecture/MODULE_BOUNDARY.md)
- [Template, clone and lifecycle](docs/architecture/TEMPLATE_CLONE_LIFECYCLE.md)
- [Candidate public ports](docs/contracts/PUBLIC_PORTS.md)
- [HR consumer mapping](docs/contracts/HR_CONSUMER_MAPPING.md)
- [Contract adoption ledger](docs/governance/CONTRACT_ADOPTION_LEDGER.md)

Branch: `agent/department-management-development`; `main` remains the untouched reference baseline. This module owns department structural records and requests; Team Agents HR owns employment truth; employer packages own qualifications; Work Management owns business tasks; platform Workflows owns durable orchestration; Kernel owns technical composition. Module API candidates cannot claim external owner signoff.
