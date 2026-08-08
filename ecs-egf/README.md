# ECS Ecosystem Governance Framework (ECS-EGF)

> **Status:** `DRAFT 0.2` — draft for co-authoring by Founding Members.
> Ratified text is adopted at the Q4 2026 Incorporation General Assembly.

📄 **[Read the ECS Ecosystem Governance Framework](./ecs-ecosystem-governance-framework.md)**

Previous drafts are archived in versioned subdirectories
([`v0.1/`](./v0.1/ecs-ecosystem-governance-framework.md)); the document at
the root of this directory is always the current working draft.

The Council's own ecosystem-level framework. It is itself an EGF and MUST
respect the [Network GF](../network-gf/) — it is the reference implementation
of that document's requirements for EGFs, and the worked example of the
[Template EGF](../template-egf/). It covers the five fixed **Essential
Credential Schemas** and the rules under which the Council accredits Issuer
Grantors and Issuers for each schema.

## The five Essential Credential Schemas

| Schema | Identifies | Issuer onboarding mode | Definition |
| --- | --- | --- | --- |
| `Service` | Verifiable Services (including AI agents acting as services) | `ECOSYSTEM_ONBOARDING_PROCESS` | [service.json](https://verana-labs.github.io/verifiable-trust-spec/schemas/v4/service.json) |
| `Organization` | Legal entities controlling services | `GRANTOR_ONBOARDING_PROCESS` | [org.json](https://verana-labs.github.io/verifiable-trust-spec/schemas/v4/org.json) |
| `Persona` | Individuals controlling services | `GRANTOR_ONBOARDING_PROCESS` | [persona.json](https://verana-labs.github.io/verifiable-trust-spec/schemas/v4/persona.json) |
| `UserAgent` | End-user wallets and applications | `OPEN` (with normative vendor duties) | [ua.json](https://verana-labs.github.io/verifiable-trust-spec/schemas/v4/ua.json) |
| `Badge` | Humans (employees, members) operating on behalf of the organization or persona behind a service | `OPEN` (spec-mandated, with normative issuer duties) | [badge.json](https://verana-labs.github.io/verifiable-trust-spec/schemas/v4/badge.json) |

Each schema's full definition is normative in the Verifiable Trust
Specification v4. This framework covers the Council's **governance** of the
ECS ecosystem: schema configuration, per-schema credential frameworks,
accreditation, participant lifecycle, fees, trust assurance, sanctions, and
amendment.

**ECS Ecosystem Participants** — recruitment opens once this framework ships
(target Q4 2026), with initial participants permissioned in time for mainnet
(target Q1 2027). Express interest via the contact form at
[veranacouncil.org](https://veranacouncil.org).

## Version history

| Version | Date | Status | Summary |
| --- | --- | --- | --- |
| DRAFT 0.2 | 2026-08-08 | Draft | Aligned with Verifiable Trust spec v4: added the Badge ECS (fifth schema) with its §6.5 credential framework, spec-mandated `OPEN`/`PERMISSIONLESS` configuration, VTJSC fragment, schema digest, and biometric-data privacy rule; corrected the UserAgent schema digest. |
| DRAFT 0.1 | 2026-07-05 | Draft | First draft for co-authoring by Founding Members (archived under [`v0.1/`](./v0.1/ecs-ecosystem-governance-framework.md)). |

## License

[CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
