# ECS Ecosystem Governance Framework (ECS-EGF)

| Field | Value |
| --- | --- |
| Document Name | ECS Ecosystem Governance Framework (ECS-EGF) |
| Version | DRAFT 0.1 |
| Status | Draft for co-authoring by Founding Members |
| Governs | The ECS ecosystem: the four Essential Credential Schemas (Service, Organization, Persona, UserAgent) and every Participant in their permission trees |
| Governed By | The Verana Council Association (in formation), acting as the ecosystem governance authority (EGA) of the ECS ecosystem |
| Approved By | Pending — Incorporation General Assembly, target Q4 2026 |
| Approval Date | Pending |
| License | [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Anchoring | Git history and tagged releases in `verana-labs/verana-council-gov` plus a public URL now; on-chain `GovernanceFrameworkDocument` (url + digest_sri) on the ECS Ecosystem entry once the network is live |

> **Status: DRAFT 0.1.** This is a first draft published for co-authoring by the
> Founding Members of the Verana Council Association (in formation). It is
> scheduled for ratification at the Q4 2026 Incorporation General Assembly.
> Where this document states protocol facts, the
> [Verifiable Trust specification](https://verana-labs.github.io/verifiable-trust-spec/)
> and the
> [Verifiable Public Registry (VPR) specification](https://verana-labs.github.io/verifiable-trust-vpr-spec/)
> prevail. Where it states entity facts, the Council's public record and its
> published entity definitions prevail. During the pre-incorporation period,
> 2060 OÜ acts as transitional steward; every steward power carries an
> event-triggered sunset (see Chapter 14).

## 1. Introduction

*This chapter is non-normative.*

### 1.1 Why Essential Credential Schemas exist

Verifiable Trust inverts the internet's default: verify first, then connect.
Before any connection is accepted, a relying party must be able to answer, by
independent cryptographic verification, four questions about a counterpart:

1. **What service is this?** — answered by a Service credential.
2. **Who is accountable for it?** — answered by an Organization credential
   (a legal entity) or a Persona credential (an identified individual
   controller).
3. **What software is the user running?** — answered by a UserAgent
   credential.
4. **Under which governance framework is all of the above accredited?** —
   answered by trust resolution terminating at an Ecosystem DID and its
   published, digest-anchored governance framework.

The four **Essential Credential Schemas (ECS)** — Service, Organization,
Persona, UserAgent — are the minimum schema set that makes those four
questions resolvable for *any* Verifiable Service (VS) or Verifiable User
Agent (VUA), regardless of sector. The Verifiable Trust specification defines
their content ([ECS-SERVICE], [ECS-ORG], [ECS-PERSONA], [ECS-UA]) and
requires that an ECS Ecosystem provide all four as CredentialSchema entries
in a Verifiable Public Registry (VPR).

### 1.2 The ECS ecosystem and its trust-root status

This document is the ecosystem governance framework (EGF) of the **ECS
ecosystem** operated by the Verana Council Association: the ecosystem that
publishes the four ECS on the Verana network and accredits the Participants
who issue and verify credentials under them.

The ECS ecosystem holds no protocol privilege. Per the Verifiable Trust
specification's whitelist mechanism ([WL]), each VS and VUA operator
maintains its own list of trusted ECS Ecosystem DIDs. The Council's ECS
ecosystem becomes a trust root **only** because operators choose to
recognize it — a client-side, revocable act of recognition, not a protocol
grant. This document is written so that such recognition remains rational:
public rules, non-discretionary accreditation, symmetric records, and
enforcement bound to on-chain state.

### 1.3 Position in the document architecture

The Verana Council governs three framework documents:

- the **Network Governance Framework (Network GF)** — the constitutional
  layer that every EGF anchored on the Verana network must respect;
- this **ECS-EGF** — the Council's own ecosystem, and deliberately the
  *reference implementation* of the Network GF's requirements for EGFs
  (chapter [NGF-EGF]); and
- the **Template EGF** — a voluntary scaffold for third parties authoring
  sector EGFs, for which this document serves as the worked example.

This EGF governs **only** the ECS ecosystem. It creates no obligation for
any other ecosystem, and the Council is expressly not a sector-EGF
authority. The Council acts here in the role the VPR specification calls an
ecosystem's **governance authority**: responsible for enforcing the rules of
this framework and, when necessary, applying the financial sanctions the
protocol provides.

The objective of this framework, in one sentence: **the trustworthiness of
the four ECS credential chains** — that a credential which verifies against
the ECS ecosystem's trust root was issued by an accredited party, about a
verified subject, under published rules, and that its revocation state is
reliable.

### 1.4 How to read this document

Chapters 2–3 define conformance language and local terminology. Chapters
4–5 establish the ecosystem's on-chain footprint and the normative
configuration of the four schemas. Chapter 6 contains one credential
framework per schema, on a fixed skeleton. Chapters 7–8 define the
accreditation machine and the Participant lifecycle. Chapters 9–14 cover
economics, trust assurance, sanctions and disputes, privacy, amendment, and
transition. Annex A collects every quantified threshold as an Initial
Parameter; Annex B schedules this framework's Controlled Documents.

Design decisions not settled by the specifications or the Council's public
record are marked with **[DECISION]** blockquotes for the Founding Members
to confirm or amend.

## 2. Conformance

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
"OPTIONAL" in this document are to be interpreted as described in
[RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) and
[RFC 8174](https://www.rfc-editor.org/rfc/rfc8174) when, and only when, they
appear in all capitals, as shown here.

Every normative statement in this document carries a stable bracketed
requirement identifier (for example `[ECS-ACC-4]`). Identifiers are
permanent: once assigned they are never renumbered or reused, and
cross-references cite identifiers, never section numbers. Statements not
marked normative, and all text under a heading annotated "*This section is
non-normative.*", are informative.

Cross-references to the Network Governance Framework cite its chapter
identifier prefixes (for example "chapter [NGF-EGF]"), because the sibling
documents are versioned independently.

Bracketed anchors of the Verifiable Trust and VPR specifications (for
example [ECS-SERVICE], [ECS-ORG], [ECS-PERSONA], [ECS-UA], or
[MOD-PP-MSG-3]) are external citations into those specifications. They are
distinct from this document's own requirement identifiers, whose families
always carry a numeric suffix (for example [ECS-ORG-14] is a requirement of
this document; [ECS-ORG] is the VT specification's Organization schema
definition).

## 3. Terminology

Terms of art defined in the
[Verifiable Trust specification](https://verana-labs.github.io/verifiable-trust-spec/)
and the
[VPR specification](https://verana-labs.github.io/verifiable-trust-vpr-spec/)
are used with their spec meanings and are not redefined here — in
particular: *Corporation*, *Ecosystem*, *Participant*, *onboarding process*,
*CredentialSchema*, *SchemaAuthorizationPolicy*, *trust deposit*, *trust
unit (TU)*, the participant roles (`ECOSYSTEM`, `ISSUER_GRANTOR`,
`VERIFIER_GRANTOR`, `ISSUER`, `VERIFIER`, `HOLDER`), and the onboarding
modes (`OPEN`, `GRANTOR_ONBOARDING_PROCESS`, `ECOSYSTEM_ONBOARDING_PROCESS`,
`ISSUER_ONBOARDING_PROCESS`, `PERMISSIONLESS`). Definitions below contain no
normative keywords.

- **Accreditation** — the formal recognition, by the ecosystem governance
  authority or an Issuer/Verifier Grantor, of a party's competence to act in
  a permissioned role (issuer, verifier, grantor) for a given schema.
  Distinct from *certification*, which attests conformity of a product,
  process, or service (the UserAgent framework is a certification at
  software-product-line level).
- **Cause** — any of the enumerated grounds for sanction listed in
  [ECS-SANC-2].
- **Controlled Document** — a document subordinate to this framework,
  independently versioned, listed in Annex B with its owner and normative
  location, and binding by incorporation.
- **Council** — the Verana Council Association (in formation), a Swiss
  Verein (Art. 60 ZGB); in this document, always acting in its capacity as
  the ecosystem governance authority (EGA) of the ECS ecosystem.
- **ECS whitelist** — the list of trusted ECS Ecosystem DIDs that each VS
  and VUA operator maintains per the Verifiable Trust specification ([WL]).
- **Ecosystem governance authority (EGA)** — the party responsible for
  developing, publishing, maintaining, and enforcing an ecosystem's
  governance framework. Never abbreviated "GA" in this document.
- **Evidence Checklist** — the uniform, per-role, per-schema list of
  evidence items an applicant must satisfy; a Controlled Document whose
  completed instance is digest-anchored on-chain (see [ECS-ACC-8]).
- **General Assembly** — the supreme organ of the Verana Council Association
  under its statutes. Always spelled out; never "GA".
- **Grace Period** — the defined transition window after an involuntary
  termination of an issuer during which credentials it issued continue to
  verify while holders migrate (see [ECS-LIFE-16]).
- **Member** — an organization holding a seat in the Verana Council
  Association (a Verein member); per the Network GF ([NGF-TRAN-7]), the
  "Founding" designation is historical only and confers no right or power.
  Never used for a VPR role; on-chain roles are always called
  *Participants*.
- **Network validator** — an operator of a consensus node of the Verana
  network (a Council member duty). Distinct from an *onboarding validator*.
- **Onboarding validator** — the Participant that validates an applicant in
  a VPR onboarding process (the `validator` of the VPR specification's
  Participant module). The bare word "validator" is never used alone in this
  document.
- **Participant Candidate Agreement** — the uniform agreement executed by
  every applicant for a permissioned role in the ECS ecosystem; a Controlled
  Document derived from this framework (Annex B).

## 4. The ECS Ecosystem on the VPR

### 4.1 Governance authority and relationship to the Network GF

[ECS-GEN-1] This framework supplements, and does not supersede, the Network
Governance Framework; in the event of conflict between this framework and
the Network Governance Framework, the Network Governance Framework SHALL
control.

[ECS-GEN-2] This framework MUST satisfy every requirement that Network GF
chapter [NGF-EGF] imposes on ecosystem governance frameworks anchored on the
Verana network.

*Non-normative note:* the ECS-EGF is deliberately the **reference
implementation** of chapter [NGF-EGF]: the Council holds its own ecosystem
to the same rules it asks every other ecosystem to meet, and to nothing
less. Table 1 maps each [NGF-EGF] requirement class to the section of this
document that satisfies it.

Table 1 below is a non-normative index; the cited sections are the
normative text.

**Table 1 — Conformance mapping to Network GF chapter [NGF-EGF]:**

| [NGF-EGF] requirement class | Satisfied by |
| --- | --- |
| Published on-chain as `GovernanceFrameworkVersion` + `GovernanceFrameworkDocument` (url + digest_sri, language) | §4.2, [ECS-GEN-6] |
| Document-control metadata block | Front-matter table of this document |
| Identified EGA with contact point | §4.1, [ECS-GEN-3]; contact per [ECS-GEN-4] |
| Legal jurisdiction stated | [ECS-GEN-5] |
| No contradiction of the Network GF | [ECS-GEN-1] |
| Layering clause | [ECS-GEN-1] |
| Scope defined | §1.3, §5 |
| Roles per schema defined | Chapter 6 (per-schema frameworks) |
| Onboarding requirements per role | Chapters 6–7 |
| Sanctions and appeal | Chapter 11 |
| Issuer termination duties | [ECS-LIFE-18] |
| Verified revocation requests | [ECS-SANC-9] |
| Revocation-availability asymmetry | [ECS-LIFE-11], [ECS-GEN-7] |
| Fee schedule (or absence) | Chapter 9, Annex A |
| Privacy / data-handling commitments | Chapter 12 |
| Amendment process with notice | Chapter 13 |
| Personal-data prohibition on-chain | [ECS-PRIV-1] |
| Lawful-purpose clause | [ECS-GEN-9] |
| No misrepresentation of Council endorsement | [ECS-GEN-10]; §4.4 (whitelist honesty) |

[ECS-GEN-3] The ecosystem governance authority of the ECS ecosystem is the
Verana Council Association; the Council MUST exercise every EGA power under
this framework through its own decision rules (the voting rule of Network GF
[NGF-GOV-6] to [NGF-GOV-8]), and no Board organ of the association SHALL
hold any authority under this framework.

[ECS-GEN-4] The Council MUST publish and maintain a public contact point
for ECS ecosystem matters (currently the contact form at
[veranacouncil.org](https://veranacouncil.org)).

[ECS-GEN-5] The legal jurisdiction of this framework is Switzerland, the
seat of the Verana Council Association; disputes escalate as provided in
Chapter 11.

[ECS-GEN-6] The Council MUST anchor every ratified version of this
framework on-chain as a `GovernanceFrameworkDocument` (url + digest_sri) of
the ECS Ecosystem entry: version 1 is supplied to, and activated by, Create
Ecosystem ([MOD-ES-MSG-1]) at Ecosystem creation; every subsequent version
is added via Add Governance Framework Document ([MOD-GF-MSG-1]) and
activated via Increase Active Governance Framework Version
([MOD-GF-MSG-2]); before the network is live, the canonical anchoring is
the tagged release history of `verana-labs/verana-council-gov`.

[ECS-GEN-7] Every version of this framework and of its Controlled Documents
MUST remain publicly resolvable without authentication for as long as any
permission or credential issued under it can be valid; the chain-anchored
digest version is canonical over any web copy.

[ECS-GEN-8] Participation in the ECS ecosystem — submitting or accepting
any onboarding process, holding any Participant entry, or issuing or
verifying any credential under an ECS — constitutes acceptance of the
version of this framework active at the time of the act.

[ECS-GEN-9] A Participant of the ECS ecosystem MUST NOT use its
permissions, or credentials issued under this framework, for an unlawful
purpose.

[ECS-GEN-10] No party, including the Council, SHALL represent the creation
or registration of an ecosystem, or accreditation under this framework, as
an endorsement by the Council of any product, service, or organization.

[ECS-GEN-11] Nothing in this framework requires any Participant to breach
law applicable to it; a Participant relying on this clause MUST notify the
Council in writing, identifying the conflicting legal obligation.

### 4.2 On-chain footprint

[ECS-ROOT-1] The Council MUST establish and maintain the following on-chain
entries on the Verana network, in this order: a Corporation entry for the
Verana Council Association ([MOD-CO-MSG-1]); the ECS Ecosystem entry
([MOD-ES-MSG-1]) with its `did` (the **ECS Ecosystem DID**), carrying
version 1 of this framework as its governance framework document
(url + digest_sri, activated at creation; subsequent versions via
[MOD-GF-MSG-1] / [MOD-GF-MSG-2]); the four ECS CredentialSchema entries
([MOD-CS-MSG-1]) configured per Chapter 5; the root `ECOSYSTEM` Participant
entries ([MOD-PP-MSG-7]); and, for every (schema, role) pair with role
`ISSUER` or `VERIFIER` that is subject to accreditation criteria, the
corresponding SchemaAuthorizationPolicy documents ([MOD-CS-MSG-5] /
[MOD-CS-MSG-6]); criteria for other gated roles are published per
[ECS-ACC-1].

[ECS-ROOT-2] The Council MUST publish, in the ECS Ecosystem DID Document,
one `LinkedVerifiablePresentation` service entry per ECS pointing to the
self-issued Verifiable Trust Json Schema Credential (VTJSC) of that schema,
with the exact fragment names required by [VT-ECS-ECOSYSTEM-DIDDOC]
(`#vpr-schemas-service-vtjsc-vp`, `#vpr-schemas-org-vtjsc-vp`,
`#vpr-schemas-persona-vtjsc-vp`, `#vpr-schemas-ua-vtjsc-vp`).

[ECS-ROOT-3] The VTJSCs for the Organization and Persona schemas MUST carry
`validFrom` and `validUntil` properties, as required by
[VT-ECS-JSON-SCHEMA-CRED-W3C]; the Council MUST re-issue each such VTJSC
before its `validUntil`, without interruption of resolvability.

### 4.3 ECS Ecosystem DID lifecycle

*Non-normative note:* per [WL], VS and VUA operators whitelist the ECS
Ecosystem DID as a trust root. The integrity of that single DID therefore
carries the entire ECS trust graph. The following commitments are
self-binding pledges by the Council, in the pattern established by root
identifier governance frameworks elsewhere.

[ECS-ROOT-4] The Council MUST create the ECS Ecosystem DID and its
controlling keys in a recorded ceremony involving no fewer than two
authorized representatives of distinct Council member organizations, with
each cryptographic action verified by a person other than the one who
performed it, and MUST publish a signed ceremony report.

[ECS-ROOT-5] The Council MUST publish the ECS Ecosystem DID, and every
change to it, at no fewer than three independent locations: the on-chain
Ecosystem entry, veranacouncil.org, and the `verana-labs/verana-council-gov`
repository; Council members SHOULD additionally publish it on their own
websites.

[ECS-ROOT-6] The Council MUST document, as part of the ECS Onboarding and
Identity Verification Operational Annex (Annex B), its key-custody,
key-rotation, and key-recovery procedures for the ECS Ecosystem DID,
including the multi-person control rule of [ECS-ROOT-4] applied to every
rotation.

[ECS-ROOT-7] The Council MUST announce every key rotation of the ECS
Ecosystem DID publicly within 7 days of execution, with the rotation's
effective time and the verification path for the new key material.

[ECS-ROOT-8] If the Council ceases to operate the ECS ecosystem — by
General Assembly decision, dissolution, or otherwise — it MUST, before
abandoning the ECS Ecosystem DID, publish migration procedures sufficient
for VS and VUA operators to re-anchor trust resolution, and MUST publicly
declare the abandonment; the Council MUST NOT let the DID lapse silently.

### 4.4 Whitelist honesty

[ECS-ROOT-9] The Council MUST NOT represent the ECS ecosystem's trust-root
status as a protocol privilege; in all public communication it MUST
describe that status as recognition freely granted, and freely revocable,
by individual VS and VUA operators through their ECS whitelists per the
Verifiable Trust specification ([WL]).

[ECS-ROOT-10] The Council MUST NOT condition any accreditation, permission,
fee, or service under this framework on a party's whitelisting of the ECS
Ecosystem DID, and MUST NOT penalize any party for recognizing additional
or alternative ECS ecosystems.

### 4.5 Trust Registry Query Protocol (TRQP) compliance

*Non-normative note:* the Verifiable Trust specification requires that the
VPR's query API support the ToIP Trust Registry Query Protocol (TRQP). Ambiguity
about what "authorized" means is the worst interoperability failure
available to a trust registry, so this framework fixes the mapping for the
ECS ecosystem.

[ECS-GEN-12] For TRQP queries concerning the ECS ecosystem, the PARC
mapping is fixed as follows: `authority_id` = the ECS Ecosystem DID (or the
Ecosystem entry `id`); `entity_id` = the `did` of the Participant entry —
the DID of the Verifiable Service that appears as credential issuer or
verifier (the owning Corporation is resolvable from the entry); `action` =
`issue` or `verify`; `resource` = the CredentialSchema `id` of the ECS
concerned; a conforming responder MUST apply this mapping.

[ECS-GEN-13] A TRQP responder answering for the ECS ecosystem MUST return
`authorized: true` if and only if all of the following hold at the
evaluated time: the relevant Participant entry is in `VALIDATED` state; the
evaluated time falls within the entry's effective validity
(`effective_from` < t < `effective_until`); the entry has not been revoked
([MOD-PP-MSG-9]); the Participant entry has not been ecosystem-slashed
([MOD-PP-MSG-12] — repayment per [MOD-PP-MSG-13] restores the
corporation's ability to obtain a new permission, never the slashed
entry); and the Participant's Corporation is not non-trustable due to an
unrepaid network-level slash ([MOD-TD-MSG-5]).

[ECS-GEN-14] The Council MUST ensure that this framework is discoverable
from the ECS Ecosystem DID, satisfying TRQP's requirement that the
ecosystem governance framework be discoverable via the `authority_id`.

[ECS-GEN-15] Permission state for the four ECS MUST be reconstructible
as-of any past time from public chain data, so that TRQP time-scoped
queries and issuance-time authorization checks yield deterministic answers.

## 5. The Four Essential Credential Schemas

### 5.1 Normative configuration

[ECS-GEN-16] The Council MUST create and maintain the four ECS
CredentialSchema entries with exactly the configuration of Table 2; any
deviation is an amendment to this framework (Chapter 13).

**Table 2 — ECS CredentialSchema configuration (normative):**

| Field | Service | Organization | Persona | UserAgent |
| --- | --- | --- | --- | --- |
| `json_schema` | [ECS-SERVICE] | [ECS-ORG] | [ECS-PERSONA] | [ECS-UA] |
| `issuer_onboarding_mode` | `ECOSYSTEM_ONBOARDING_PROCESS` | `GRANTOR_ONBOARDING_PROCESS` | `GRANTOR_ONBOARDING_PROCESS` | `OPEN` |
| `verifier_onboarding_mode` | `OPEN` | `OPEN` | `OPEN` | `OPEN` |
| `holder_onboarding_mode` | `ISSUER_ONBOARDING_PROCESS` | `ISSUER_ONBOARDING_PROCESS` | `ISSUER_ONBOARDING_PROCESS` | `PERMISSIONLESS` |
| `issuer_grantor_validation_validity_period` | 0 | Annex A | Annex A | 0 |
| `verifier_grantor_validation_validity_period` | 0 | 0 | 0 | 0 |
| `issuer_validation_validity_period` | Annex A | Annex A | Annex A | Annex A |
| `verifier_validation_validity_period` | Annex A | Annex A | Annex A | Annex A |
| `holder_validation_validity_period` | Annex A | Annex A | Annex A | 0 |
| `pricing_asset_type` | `TU` | `TU` | `TU` | `TU` |
| `pricing_asset` | `tu` | `tu` | `tu` | `tu` |
| `digest_algorithm` | `SHA384` | `SHA384` | `SHA384` | `SHA384` |

*Non-normative notes on Table 2:*

- Every `*_validation_validity_period` is a mandatory parameter of
  [MOD-CS-MSG-1]; `0` is the chain value written for roles a schema does
  not use (the protocol reads 0 as "never expire", which is inert for a
  role no onboarding path reaches).
- The `holder_onboarding_mode` values for Service, Organization, and Persona
  are mandated by the Verifiable Trust specification
  ([VT-ECS-JSON-SCHEMA-VPR-CONFIG]).
- Issuer modes: Service issuers are onboarded directly by the Council
  (`ECOSYSTEM_ONBOARDING_PROCESS`); Organization and Persona issuers are
  onboarded by accredited Issuer Grantors
  (`GRANTOR_ONBOARDING_PROCESS`); UserAgent issuers are software vendors who
  self-register (`OPEN`), subject to the normative vendor duties of §6.5.

> **[DECISION]** *Verifier onboarding mode `OPEN` for all four schemas at
> launch.* Rationale: verifying an ECS credential is the low-risk side of
> the exchange — a verifier learns only what a holder chooses to present,
> and gating verification would tax adoption of exactly the parties
> (wallets, services) the ecosystem needs. Verification fees are 0 at
> launch (Chapter 9), so open verifier mode creates no fee-capture risk.
> The alternative is `ECOSYSTEM_ONBOARDING_PROCESS` for verifiers of the
> Persona schema, on the argument that personal-data-bearing credentials
> deserve accountable verifiers; Founding Members should confirm or tighten.
> Tightening later is a schema-configuration amendment under Chapter 13.

A second configuration choice concerns the UserAgent holder side.

> **[DECISION]** *UserAgent `holder_onboarding_mode` = `PERMISSIONLESS`.*
> The UserAgent credential is an AnonCreds credential ([VT-ECS-UA-CRED-ANON])
> held by end-user agent instances; unlinkability is its design goal, and
> the credential is checked at reception time by the holder wallet. Creating
> on-chain `HOLDER` Participant entries per agent instance would build a
> correlatable registry of user agents — contrary to the schema's privacy
> purpose. The alternative (`ISSUER_ONBOARDING_PROCESS`) is rejected for
> that reason, but Founding Members should confirm.

### 5.2 Schema identity: permanent links and digests

[ECS-GEN-17] The `json_schema` of each ECS CredentialSchema entry MUST
verify against the corresponding SHA-384 digest of Table 3, computed per
the Verifiable Trust specification (JCS canonicalization of the schema
minus `$id`).

**Table 3 — ECS schema permanent links and digests (from the VT spec):**

| Schema | Permanent link | JCS/SHA-384 digest |
| --- | --- | --- |
| ServiceCredential | <https://verana-labs.github.io/verifiable-trust-spec/schemas/v4/service.json> | `sha384-0v+BAFGpnBX/RVqH9dUlMglxMrD4AKy4qUtb1lMN4iW9I2gO7XjcUfmGOf0oInP3` |
| OrganizationCredential | <https://verana-labs.github.io/verifiable-trust-spec/schemas/v4/org.json> | `sha384-UPn4TDqS1nMBAN3FyMzTAZOWp99zBjBD69OjpbhwOKZj7iOrS5qPwJ2SArRz0yzu` |
| PersonaCredential | <https://verana-labs.github.io/verifiable-trust-spec/schemas/v4/persona.json> | `sha384-VfXTfuks02OkoR5USaTfEdc4NU25m4+vNrLATnjC0r0Pn1S3tFTdOvGCfSYdjE2I` |
| UserAgentCredential | <https://verana-labs.github.io/verifiable-trust-spec/schemas/v4/ua.json> | `sha384-yLRK2mCokVjRlGX0nVzdEYQ1o6YWpQqgdg6+HlSxCePP+D7wvs0+70TJACLZfbF/` |

### 5.3 Schema-change policy

[ECS-GEN-18] Any change to an ECS `json_schema`, onboarding mode, digest
algorithm, or pricing asset is a governance act of the Council: it MUST be
approved by the Council's ⅔ supermajority, MUST be announced at least 30
days before taking effect, and MUST be reflected in an amendment of this
framework whose change-log row names the on-chain acts that execute it.

[ECS-GEN-19] Adoption of a new major version of the Verifiable Trust
specification's ECS definitions (with new schema digests) MUST preserve
verification of credentials issued under the prior version for the
remainder of their validity, unless the prior version is revoked for a
documented security cause.

## 6. Per-Schema Credential Frameworks

*Non-normative note:* each of the four frameworks below follows one fixed
skeleton — Purpose · Scope · Principles · Issuer policies (eligibility,
identity verification, issuance, revocation, level of assurance,
monitoring) · Holder policies · Verifier policies · Credential definition —
so that the assurance differences between schemas are legible as deltas.
Where a section states "no additional restrictions", the silence is
deliberate: the general rules of this framework and the Network GF apply,
and nothing more. Detailed verification ceremonies (session scripts,
challenge formats, accepted registry and eID lists) live in the **ECS
Onboarding and Identity Verification Operational Annex**, a versioned
Controlled Document (Annex B) — not in this constitutional text.

[ECS-GEN-20] The policies of each per-schema framework in this chapter
apply *in addition to* the general requirements of this framework and of
the Network Governance Framework; a Participant subject to them MAY be
bound by stricter obligations under a Controlled Document, and no
Controlled Document SHALL loosen them.

[ECS-GEN-21] Identity verification under this chapter comprises two
distinct steps that MUST both be performed: **identity assurance**
(establishing that the claimed real-world subject exists and is accurately
described by the evidence) and **identity authentication** (establishing
that the party in the onboarding session is that subject or its authorized
representative, including proof of control of the relevant DID).

### 6.1 Service Credential Framework

#### 6.1.1 Purpose and scope

*This section is non-normative.* The Service credential identifies a
Verifiable Service: its DID, name, type, description, logo,
minimum-age requirement, and its terms-of-service and privacy-policy
documents (each pinned by URI + SRI digest). Every VS must present a
Service credential as a linked verifiable presentation, bound to an
accountable entity via exactly one Organization or Persona credential
(VT spec [VS-REQ]); Service-credential issuers must themselves be
Verifiable Services, making the trust chain recursive.

#### 6.1.2 Principles

*This section is non-normative.* The Service credential is
context-independent (one credential describes one service, wherever
presented) and binds the service, not its operator — operator
accountability travels through the Organization or Persona credential.

#### 6.1.3 Issuer policies

[ECS-SVC-1] `ISSUER` Participant entries for the Service schema are
created exclusively by the Council through the ecosystem onboarding
process (`ECOSYSTEM_ONBOARDING_PROCESS`); the Council MUST act as the
onboarding validator for every Service-issuer application.

[ECS-SVC-2] An applicant for Service issuer accreditation MUST satisfy the
published accreditation criteria of the active SchemaAuthorizationPolicy
for (Service, ISSUER), which MUST include at least: a registered
Corporation entry with demonstrated control of its DID; operation of a
conformant Verifiable Service; organizational identity verified to the
same standard as an Organization credential subject (§6.2.4); and
sustainable financing per [ECS-FEE-6].

[ECS-SVC-3] Before issuing a Service credential, the issuer MUST validate
that the applicant owns and controls the service described: proof of
control of the service DID by challenge-response over the DIDComm
onboarding session; resolvability and SRI-digest integrity of the declared
terms-of-service, privacy-policy, and logo resources; and consistency of
the declared service type and `minimumAgeRequired` with the service as
operated.

[ECS-SVC-4] A Service-credential issuer MUST NOT rely, for ownership or
control validation, solely on assertions or documents supplied by the
applicant that are not corroborated by DID-control proof or by reliable
third-party sources.

[ECS-SVC-5] A Service-credential issuer MUST revoke a Service credential
within 5 days of establishing any of: loss or transfer of the subject's
DID control; material misdescription of the service; a verified revocation
request per [ECS-SANC-9]; or revocation of the Organization or Persona
credential that binds the service to its accountable entity.

[ECS-SVC-6] Service credentials are issued at a single level of assurance,
anchored to organizational identity verification per §6.2.4; future
versions of this framework MAY define multiple levels.

[ECS-SVC-7] A Service-credential issuer MUST monitor, at least monthly,
the continued resolvability and digest integrity of the SRI-pinned
resources of credentials it has issued, and MUST open a revocation review
on persistent failure.

#### 6.1.4 Holder policies

[ECS-SVC-8] `HOLDER` entries are created by issuers through the issuer
onboarding process; a holder MUST notify its issuer within 30 days of any
change to the credential subject data, and immediately upon loss of DID
control.

#### 6.1.5 Verifier policies

There are no additional verifier restrictions for the Service schema
(verifier mode `OPEN`; see the [DECISION] under Table 2).

#### 6.1.6 Credential definition

[ECS-SVC-9] Service credentials MUST be W3C Verifiable Trust Credentials
linked to the Service VTJSC, with subject fields exactly per the VT
specification's [ECS-SERVICE] and digests computed with SHA-384.

### 6.2 Organization Credential Framework

#### 6.2.1 Purpose and scope

*This section is non-normative.* The Organization credential binds a DID to
a verified legal entity: registered name, mandatory registry identifier
(`registryId`), registry URI, address, ISO 3166-1 country code, legal
jurisdiction, organization kind, and an optional LEI. The subject DID is
the sole authoritative identifier; everything else is descriptive evidence.
This is the ecosystem's highest-assurance workhorse: it is what makes a
service *accountable*.

#### 6.2.2 Principles

*This section is non-normative.* Verification is registry-anchored: the
authoritative source for a legal entity's existence is the public register
that constitutes it, never the entity's own publications. Assurance is
anchored to existing standards (eIDAS "substantial", NIST 800-63 IAL2
analogues for organizations) rather than bespoke criteria.

#### 6.2.3 Issuer structure

[ECS-ORG-1] `ISSUER` entries for the Organization schema are created by
accredited **Issuer Grantors** (`GRANTOR_ONBOARDING_PROCESS`); the Council
MUST accredit Issuer Grantors per jurisdiction or region against the
published Issuer Grantor criteria Controlled Document for the Organization
schema ([ECS-ACC-1], Annex B), and each Issuer Grantor acts as the
onboarding validator for issuer applicants within its published scope,
evaluating them against the active SchemaAuthorizationPolicy for
(Organization, ISSUER).

> **[DECISION]** *Issuer Grantor scopes are non-exclusive.* More than one
> Issuer Grantor may be accredited for the same jurisdiction or region;
> exclusivity would recreate the monopoly gatekeeper this architecture
> exists to avoid, and the neutrality duty ([ECS-ACC-13]) plus
> non-discretionary admission make competition safe. The alternative
> (one grantor per jurisdiction) simplifies oversight; Founding Members
> should confirm.

#### 6.2.4 Identity verification

[ECS-ORG-2] Before issuing an Organization credential, the issuer MUST
verify the subject's legal existence and the accuracy of every subject
attribute against at least one of the following, matching the declared
`registryId` and `registryUri`: (a) an extract or attestation obtained
directly from the constitutive public registry of the declared
jurisdiction; (b) a qualified third-party database that is periodically
updated from such registries; or (c) direct official communication with
the organization through contact data obtained from an independent source.

[ECS-ORG-3] Evidence found on websites, in documents, or through links
provided solely by the applicant MUST NOT be accepted as verification
evidence under [ECS-ORG-2].

[ECS-ORG-4] The issuer MUST verify the applicant's control of the subject
DID by challenge-response within the DIDComm onboarding session, and MUST
verify that the natural person conducting the session is an authorized
representative of the legal entity.

[ECS-ORG-5] The issuer MUST verify consistency between `countryCode`,
`legalJurisdiction`, and the registry evidence, and MUST treat a declared
`lei` as informational unless it is corroborated by vLEI-grade evidence.

[ECS-ORG-6] The issuer MUST screen the subject organization against
applicable sanctions lists at issuance and at each renewal, at the level
of assurance stated in the Operational Annex.

[ECS-ORG-7] Identity verification for Organization credentials MUST meet a
level of assurance at least equivalent to eIDAS "substantial" (or NIST
SP 800-63 IAL2 as applied to organizational representatives), as detailed
in the Operational Annex; bespoke criteria MUST NOT replace these anchors.

#### 6.2.5 Issuance and revocation

[ECS-ORG-8] Each Organization credential issuance decision MUST involve at
least two authorized persons of the issuer, separating evidence
verification from issuance approval.

[ECS-ORG-9] Organization credentials MUST carry `validFrom` and
`validUntil`, with a lifetime not exceeding the Initial Parameter of
Annex A; renewal requires re-verification per [ECS-ORG-2]–[ECS-ORG-7].

[ECS-ORG-10] The issuer MUST revoke an Organization credential within
5 days of establishing any of: dissolution or deregistration of the legal
entity; loss or transfer of subject-DID control; material inaccuracy of a
subject attribute; or a verified revocation request per [ECS-SANC-9].

[ECS-ORG-11] An applicant that fails Organization verification MAY be
directed to apply for a Persona credential instead (§6.3); the issuer MUST
NOT issue an Organization credential at a relaxed standard as a substitute.

#### 6.2.6 Monitoring

[ECS-ORG-12] An Organization-credential issuer MUST retain the evidence
supporting each issuance for the retention period of Annex A and MUST make
it available to the Council on reasoned request in a sanctions or audit
proceeding.

#### 6.2.7 Holder policies

[ECS-ORG-13] A holder of an Organization credential MUST notify its issuer
within 30 days of any change affecting a subject attribute, and
immediately upon loss of DID control or commencement of dissolution or
insolvency proceedings.

#### 6.2.8 Verifier policies

There are no additional verifier restrictions for the Organization schema.

#### 6.2.9 Credential definition

[ECS-ORG-14] Organization credentials MUST be W3C Verifiable Trust
Credentials linked to the Organization VTJSC, with subject fields exactly
per the VT specification's [ECS-ORG] and digests computed with SHA-384.

### 6.3 Persona Credential Framework

#### 6.3.1 Purpose and scope

*This section is non-normative.* The Persona credential binds a DID to an
identified natural-person controller (name, description, optional avatar,
mandatory controller country code and jurisdiction). It is the
accountability path for services operated by individuals — the
lower-ceremony sibling of the Organization credential, with personal-data
duties attached.

#### 6.3.2 Principles

*This section is non-normative.* Proofing follows established
person-identity standards (NIST SP 800-63A, eIDAS); recency matters more
than ceremony; and the holder's privacy is protected by data minimization
and the consent rules of Chapter 12.

#### 6.3.3 Issuer structure

[ECS-PER-1] `ISSUER` entries for the Persona schema are created by
accredited Issuer Grantors (`GRANTOR_ONBOARDING_PROCESS`) under the same
structure, criteria publication, and neutrality duties as §6.2.3 applied
to the Persona schema's criteria instruments per [ECS-ACC-1] (the
(Persona, ISSUER) SchemaAuthorizationPolicy and the Persona Issuer Grantor
criteria Controlled Document).

#### 6.3.4 Identity verification

[ECS-PER-2] Before issuing a Persona credential, the issuer MUST perform
identity proofing of the natural-person controller at a level of assurance
at least equivalent to NIST SP 800-63A IAL2 or eIDAS "substantial",
using government-issued identity evidence or a recognized national eID
scheme as listed in the Operational Annex.

[ECS-PER-3] The identity proofing relied upon MUST have been performed no
more than the Annex A proofing-recency period before issuance.

[ECS-PER-4] The issuer MUST verify the subject's control of the DID by
challenge-response within the DIDComm onboarding session, binding the
proofed person to the DID.

[ECS-PER-5] Where the credential subject is controlled through a guardian
or legal proxy, the issuer MUST verify the guardianship or proxy authority
itself, record it in the issuance evidence, and re-verify it at renewal.

#### 6.3.5 Issuance and revocation

[ECS-PER-6] Persona credentials MUST carry `validFrom` and `validUntil`,
with a lifetime not exceeding the Initial Parameter of Annex A.

[ECS-PER-7] The issuer MUST record the subject's consent to issuance and
to any publication of subject data; withdrawal of that consent is a
mandatory revocation trigger, and any published derivative of the subject
data MUST be deleted, not merely flagged, upon revocation.

[ECS-PER-8] The issuer MUST revoke a Persona credential within 5 days of
establishing any of: death or verified incapacity of the controller
without a verified successor arrangement; loss or transfer of subject-DID
control; material inaccuracy of a subject attribute; consent withdrawal;
or a verified revocation request per [ECS-SANC-9].

#### 6.3.6 Monitoring

[ECS-PER-9] A Persona-credential issuer MUST retain issuance evidence per
the Annex A retention period, applying the data-minimization and
protection duties of Chapter 12 to all personal data in that evidence.

#### 6.3.7 Holder policies

[ECS-PER-10] A holder of a Persona credential MUST notify its issuer
within 30 days of any change affecting a subject attribute, and
immediately upon loss of DID control.

#### 6.3.8 Verifier policies

[ECS-PER-11] A verifier of Persona credentials MUST NOT retain presented
personal data beyond the purpose and duration for which it was presented,
per [ECS-PRIV-5].

#### 6.3.9 Credential definition

[ECS-PER-12] Persona credentials MUST be W3C Verifiable Trust Credentials
linked to the Persona VTJSC, with subject fields exactly per the VT
specification's [ECS-PERSONA] and digests computed with SHA-384.

### 6.4 UserAgent Credential Framework

#### 6.4.1 Purpose and scope

*This section is non-normative.* The UserAgent credential lets a running
user-agent instance prove which software product and version it is,
without identifying its user. The issuer DID identifies the software
product line; the credential is issued per instance; and the format is
AnonCreds precisely so that presentations are unlinkable. This framework
is a *certification of software at product-line (type) level*, not an
accreditation of the instance or its user.

#### 6.4.2 Principles

*This section is non-normative.* Open issuer registration keeps the wallet
and agent market permissionless; accountability attaches to the vendor
through its trust deposit and the vendor duties below, not through a
gatekeeper.

#### 6.4.3 Issuer policies (vendor duties)

[ECS-UA-1] `ISSUER` entries for the UserAgent schema are self-created by
software vendors under `OPEN` mode ([MOD-PP-MSG-14]), subject to the
vendor duties of this section, which are conditions of keeping the
permission.

[ECS-UA-2] A software vendor MUST hold exactly one UserAgent issuer
authorization per software product line, and the issuer DID of every
UserAgent credential MUST uniquely identify that product line, per the
Verifiable Trust specification ([ECS-UA]).

[ECS-UA-3] A vendor MUST NOT issue UserAgent credentials for software it
does not produce and control, and MUST NOT issue under one product line's
issuer DID for instances of a different product line.

[ECS-UA-4] UserAgent credentials MUST be issued as AnonCreds Verifiable
Trust Credentials ([VT-ECS-UA-CRED-ANON]) with revocation support, and
MUST NOT be published in any DID Document.

[ECS-UA-5] The `version` (and, where used, `build`) attributes MUST
accurately identify the software running in the instance at issuance; a
vendor MUST NOT attest versions it has not released.

[ECS-UA-6] A vendor MUST revoke the UserAgent credentials of instances of
a release within 5 days of establishing that the release is compromised or
materially misrepresents its identity, and MUST maintain the availability
of its revocation registry per [ECS-LIFE-11].

#### 6.4.4 Holder policies

There are no holder onboarding requirements for the UserAgent schema
(`holder_onboarding_mode` = `PERMISSIONLESS`; see the [DECISION] under
Table 2): the holder wallet enforces issuer authorization at credential
reception time, per the Verifiable Trust specification.

#### 6.4.5 Verifier policies

There are no additional verifier restrictions for the UserAgent schema.

[ECS-UA-7] A verifier of UserAgent credentials MUST NOT attempt to
correlate UserAgent presentations across sessions or services.

#### 6.4.6 Credential definition

[ECS-UA-8] UserAgent credentials MUST conform to the VT specification's
[ECS-UA] with the
AnonCreds credential definition referencing the UserAgent VTJSC via
`relatedJsonSchemaCredentialId`, and digests where applicable computed
with SHA-384.

## 7. Accreditation

*Non-normative note:* this chapter is the machine that turns published
criteria into on-chain permissions. Its design premises: criteria are
published before anyone applies; evaluation is separated from decision;
admission is non-discretionary when criteria are met; every clock is
day-counted and runs against the Council as much as against the applicant.

### 7.1 Published criteria

[ECS-ACC-1] For every (schema, role) pair gated by an onboarding process
under Table 2, the Council MUST publish objective accreditation criteria
before accepting any application for that pair: (a) for pairs with role
`ISSUER` or `VERIFIER`, as SchemaAuthorizationPolicy documents on-chain
(url + digest_sri, created via [MOD-CS-MSG-5] and activated via
[MOD-CS-MSG-6] — the only roles the protocol accepts for such policies);
(b) for pairs with role `ISSUER_GRANTOR` or `HOLDER`, as digest-anchored
criteria Controlled Documents (Annex B) resolvable per [ECS-GEN-7].
References elsewhere in this framework to the published criteria of the
active SchemaAuthorizationPolicy for a (schema, role) are read, for pairs
under (b), as references to the corresponding criteria Controlled
Document.

[ECS-ACC-2] Each SchemaAuthorizationPolicy document MUST be structured as
mandate → addressed role → control practice → required evidence →
verification method (on-chain state, cryptographic proof, DIDComm evidence
exchange, or human review), so that an onboarding validator can evaluate
applications consistently.

[ECS-ACC-15] Where the published criteria for a (schema, role) define
eligibility categories (for example legal form, sector, or jurisdiction),
they MUST include a catch-all category admitting applicants outside the
named categories on escalated evidence, so that no legitimate applicant is
structurally excluded.

[ECS-ACC-3] Where an active SchemaAuthorizationPolicy exists for a
(schema, role), the granting corporation MUST issue the corresponding
Issuer Authorization Credential (IAC) or Verifier Authorization Credential
(VAC) to the candidate upon successful completion of the onboarding
process, as the VPR specification requires.

### 7.2 Evaluation and decision

[ECS-ACC-4] Applications for Council-validated roles (Service issuers;
Organization and Persona Issuer Grantors) MUST be evaluated by the
committee the Council charters for ECS accreditation, which delivers
written recommendations only; the accreditation decision itself MUST be
taken by the Council.

[ECS-ACC-5] If the chartered committee is vacant or inquorate, its duties
under this chapter revert to the General Assembly of the Council until the
vacancy is cured.

[ECS-ACC-6] Admission is non-discretionary: the Council (or, for issuer
applications, the competent Issuer Grantor) MUST accredit an applicant
that meets all published criteria of the active SchemaAuthorizationPolicy,
and MUST NOT apply criteria that were not published at the time the
application was filed.

[ECS-ACC-7] A refusal MUST state written reasons identifying each
unsatisfied published criterion, and MUST inform the applicant of the
appeal path of Chapter 11; a refused applicant MAY re-apply at any time
without a cooldown period.

### 7.3 Evidence and process discipline

[ECS-ACC-8] Each application MUST be evaluated against the uniform
Evidence Checklist for its (schema, role); on validation, the onboarding
validator MUST anchor the SRI digest of the completed checklist in the
`op_summary_digest` field of the applicant's Participant entry when
executing Set Participant OP to Validated ([MOD-PP-MSG-3]), making the
evidentiary basis of every accreditation verifiable.

[ECS-ACC-9] Every applicant for the same (schema, role) MUST execute the
same Participant Candidate Agreement (Annex B), identical in substance for
all applicants of that role; side agreements altering accreditation
conditions are void as against this framework.

[ECS-ACC-10] Applications MUST be processed in the order received (FIFO)
within each (schema, role) queue; the Council MAY cap concurrent
substantive reviews at the Annex A workload limit, and MUST publish the
current queue state.

[ECS-ACC-11] The following clocks apply symmetrically and are Initial
Parameters (Annex A): the applicant completes its Evidence Checklist
within the evidence window; the reviewing body completes its completeness
check within the completeness-check period and its substantive review
within the substantive-review period; an application with no decision at
the decision deadline escalates automatically to the Council plenary, and
if still undecided 30 days later, to the General Assembly.

[ECS-ACC-12] An accreditation applicant that is a Council member, or a
related party of one, MUST be evaluated and decided by a panel of
disinterested members per [ECS-SANC-6] applied by analogy.

### 7.4 Continuing duties and neutrality

[ECS-ACC-13] A fee-earning grantor or onboarding validator (an Issuer
Grantor, or the Council when collecting validation fees) MUST evaluate
every applicant only against the published criteria of the active
SchemaAuthorizationPolicy, MUST NOT refuse or delay a qualifying
applicant on any other ground, and MUST retain its conformance evidence
for each validation for the full validity period of that validation.

[ECS-ACC-14] An accredited Participant has a continuing duty to keep its
application facts accurate: it MUST notify its onboarding validator of any
material change within 30 days, and of any change of control within the
Annex A change-of-control disclosure period.

## 8. Participant Lifecycle

*Non-normative note:* every Participant in the ECS trees moves through the
same state machine, and every transition is executed by a named VPR
message — the paper rule and the chain act never diverge. Stages:
**Qualification → Application → Activation → Operation → Notification →
Suspension → Termination → Transition** (the eight stage names shared
across all Verana governance documents). The Participant Candidate
Agreement executes within the Application stage (§8.2).

### 8.1 Qualification and application

[ECS-LIFE-1] Before applying, a candidate SHOULD self-assess against the
published SchemaAuthorizationPolicy criteria and the Evidence Checklist
for the targeted (schema, role); the Council MUST keep both publicly
resolvable per [ECS-GEN-7].

[ECS-LIFE-2] An application is opened by the applicant executing Start
Participant OP ([MOD-PP-MSG-1]) toward the competent onboarding validator,
paying the applicable `validation_fees` and the protocol's trust-deposit
increment; the DIDComm validation session that follows is the venue for
identity verification (Chapter 6) and evidence evaluation (Chapter 7).

[ECS-LIFE-3] An applicant MAY cancel its pending onboarding process at any
time via Cancel Participant OP Last Request ([MOD-PP-MSG-6]).

### 8.2 Agreement and activation

[ECS-LIFE-4] Before activation, the applicant MUST have executed the
Participant Candidate Agreement for its role; the agreement's
confidentiality and cooperation clauses bind from signature, and full
participant status attaches only at activation.

[ECS-LIFE-5] Activation is the onboarding validator's execution of Set
Participant OP to Validated ([MOD-PP-MSG-3]), setting the `VALIDATED`
state with `effective_from` / `effective_until` per the schema's validity
periods, anchoring the completed Evidence Checklist digest per
[ECS-ACC-8], and — where an active SchemaAuthorizationPolicy exists —
accompanied by IAC/VAC issuance per [ECS-ACC-3]; the on-chain `VALIDATED`
state is the constitutive act of accreditation.

[ECS-LIFE-6] An onboarding process that has not reached `VALIDATED` state
within the Annex A activation window lapses: the onboarding validator MUST
close it, and the applicant may re-apply without prejudice.

### 8.3 Operation

[ECS-LIFE-7] A validated Participant MUST operate in conformance with this
framework, its Participant Candidate Agreement, and the
SchemaAuthorizationPolicy under which it was accredited, for the entire
validity of its permission.

[ECS-LIFE-8] A Participant whose validation is due to expire MUST renew it
via Renew Participant OP ([MOD-PP-MSG-2]) with its existing onboarding
validator, which re-verifies the deltas against the then-active criteria;
renewal is only possible with the same, still-active validator, so if the
Participant's onboarding validator has itself been revoked, the
Participant MUST obtain a new permission by starting a new onboarding
process ([MOD-PP-MSG-1]) with another competent onboarding validator.

[ECS-LIFE-9] Requalification at renewal is conducted under the criteria in
effect at renewal time, not those of the original accreditation.

[ECS-LIFE-10] The Council owes decision-service levels symmetric to those
it imposes: renewal reviews are subject to the same clocks as initial
applications ([ECS-ACC-11]), and a renewal filed before expiry that
remains undecided at expiry MUST NOT lapse by reason of the reviewing
body's delay alone.

[ECS-LIFE-11] Availability asymmetry: a Participant's issuance operations
MAY degrade or pause, but its revocation capability, revocation-registry
availability, and the accuracy of its on-chain permission state MUST NOT
be allowed to degrade; a Participant unable to honor this MUST notify per
[ECS-LIFE-12] and request suspension.

### 8.4 Notification

[ECS-LIFE-12] A Participant MUST notify its onboarding validator (and the
Council, for Council-validated roles) of: any breach of this framework or
security incident affecting its duties, within 72 hours of discovery; any
compromise of key material used in its ECS role, within 24 hours; any
change of control, within the Annex A disclosure period; and any
insolvency or dissolution event, immediately.

[ECS-LIFE-13] The Council owes participants no less: it MUST give at
least 30 days' notice of material changes to this framework or its
Controlled Documents (except emergency security measures, which require
prompt notice and after-the-fact ratification per Chapter 13).

### 8.5 Suspension

[ECS-LIFE-14] A suspension is executed on-chain by the Participant's
onboarding validator shortening the Participant's `effective_until` via
Set Participant Effective Until ([MOD-PP-MSG-8]), after the due process of
Chapter 11 — the protocol permits only the direct onboarding validator to
execute this act on an OP-managed entry, so where the Council is not the
direct onboarding validator it MUST direct the competent Issuer Grantor to
execute the shortening and, failing cooperation, MAY proceed to revocation
([MOD-PP-MSG-9]), which the Council as ecosystem controller can always
execute; a suspension notice MUST state the grounds by requirement
identifier, the cure conditions, and the review path.

[ECS-LIFE-15] No suspension may be indefinite: a suspension review, on the
Participant's request, MUST conclude with one of exactly three outcomes —
reinstatement, continued suspension with stated cure conditions, or
termination — and a suspension unresolved after the Annex A
auto-termination period terminates the Participant automatically.
Reinstatement of a previously suspended Participant MUST be recorded on
the public record together with the fact and duration of the suspension.

### 8.6 Termination

[ECS-LIFE-16] Termination of a permission is executed by Revoke
Participant ([MOD-PP-MSG-9]) by an authorized actor (an ancestor
onboarding validator in the branch, the grantee itself, or the Council as
ecosystem controller); an involuntary termination of an issuer opens the
Grace Period of Annex A, during which: the terminated issuer's permission
is dead immediately ("write death first" — it MUST NOT issue), credentials
it issued continue to verify, holders migrate to a surviving issuer, and
at the end of the Grace Period the issuer's unexpired credentials are
revoked.

[ECS-LIFE-17] Where a termination is grounded in fraud or in damage
quantifiable against the Participant's trust deposit, the Council or the
competent ancestor onboarding validator MAY additionally execute Slash
Participant Trust Deposit ([MOD-PP-MSG-12]), under the constraints of
Chapter 11; slashed amounts are burned by the protocol ([MOD-TD-MSG-7]),
and the slashed Participant may return only after Repay Participant
Slashed Trust Deposit ([MOD-PP-MSG-13]) and fresh accreditation.

[ECS-LIFE-18] A terminating issuer (voluntary or involuntary) MUST:
notify every affected holder of the termination and of the migration
deadline within 10 days of the termination act; refrain from any new
issuance from the moment of termination; revoke its unexpired credentials
no later than the end of the Grace Period; archive its issuance evidence
per the Annex A retention period and hand it over to the Council or a
successor issuer on request; and destroy its issuance key material after
the Grace Period, attesting destruction to the Council.

[ECS-LIFE-19] If a terminating issuer defaults on its notification duty,
the Council MUST take over notification of affected holders and MAY hold
the defaulting issuer liable for the cost.

[ECS-LIFE-20] An issuer MUST NOT transfer its holder portfolio to another
issuer on its own initiative; migration is each holder's choice among
accredited issuers.

### 8.7 Transition

[ECS-LIFE-21] A voluntary exit requires 30 days' written notice to the
Participant's onboarding validator and triggers the duties of
[ECS-LIFE-18]; the public record MUST state the nature of every departure
of an accredited Participant (voluntary exit, expiry without renewal, or
termination with its ground), symmetrically with accreditations.

## 9. Fees and Economics

*Non-normative note:* the ECS ecosystem's economics are protocol
mechanics, not commercial terms. Fees are denominated in trust units (TU)
per the schema configuration of Table 2 and recorded per Participant entry
(`validation_fees`, `issuance_fees`, `verification_fees`); trust deposits
accrue and behave exactly as the VPR specification defines — every
increment is computed as the `trust_deposit_rate` share of the trust fees
of the operation, so the fee values this chapter sets directly determine
how much deposit accrues.

### 9.1 Launch fee schedule

[ECS-FEE-1] The `validation_fees`, `issuance_fees`, and
`verification_fees` for every Council-held Participant entry in the four
ECS trees are set to the Annex A values (0 TU at launch); a Participant
other than the Council MUST NOT charge fees for ECS operations except per
[ECS-FEE-5].

> **[DECISION]** *Launch values of 0 TU for validation, issuance, and
> verification fees on all four schemas.* Rationale: the ECS are the
> bootstrap layer of the entire network — every Verifiable Service needs
> them before it can do anything else — and pricing the on-ramp would tax
> adoption exactly when the network needs participants most. Disclosed
> consequence: trust-deposit increments are computed by protocol as the
> `trust_deposit_rate` share of the trust fees of each operation, so at
> 0 TU fees **no ECS trust deposit accrues** — launch-cohort Participants
> carry no slashable ECS deposit, and the financially-backed rung (f) of
> the sanctions ladder ([ECS-SANC-3]) is inoperative until non-zero fees
> activate. The alternative — small non-zero fees from day one to fund
> grantor operations and build deposit collateral — is viable later via
> the Annex A change process and [ECS-FEE-5]; Founding Members should
> confirm the zero-fee launch with this trade-off in view.

[ECS-FEE-2] Trust-deposit mechanics are protocol-defined: where fees are
non-zero, every applicant and Participant MUST fund the trust-deposit
increments the VPR protocol requires (the `trust_deposit_rate` share of
the applicable trust fees), and the Council MUST NOT promise their return
(trust deposits are non-withdrawable by design); at the zero-fee launch
schedule no ECS trust-deposit increment accrues.

### 9.2 Economic firewall

[ECS-FEE-3] The Council MUST NOT contribute funds of any form to the
operations of any ECS Participant — no grants, subsidies, fee waivers
targeted at individual parties, loans, or guarantees; this operationalizes
the Council's hard limit against grant-making.

[ECS-FEE-4] The Council MUST NOT derive discretionary revenue from ECS
sanctions: slashed deposits are burned by the protocol, and no fee or
penalty under this framework may be routed to the Council beyond the
protocol-defined flows.

### 9.3 Fee autonomy of grantors and issuers

[ECS-FEE-5] If and when non-zero fees are activated by amendment of
Annex A, an Issuer Grantor or issuer MAY set its own `validation_fees`,
`issuance_fees`, and `verification_fees` within the published bounds of
Annex A, MUST publish its fee values, MUST apply them uniformly to all
applicants of the same (schema, role), and MUST give 30 days' notice of
increases.

[ECS-FEE-6] An applicant for a fee-earning accredited role MUST
demonstrate sustainable financing of its role operations as part of its
Evidence Checklist, and MUST reaffirm it at each renewal.

[ECS-FEE-7] No Participant may impose contractual lock-in or exclusivity
on holders or downstream applicants; a holder MAY migrate to any
accredited issuer at any time.

*Non-normative honesty note:* protocol switching costs exist even without
contractual lock-in — where fees are non-zero, a fresh onboarding process
means new trust-deposit increments, and deposits are non-withdrawable.
This framework bans adding contractual friction on top; it does not
pretend the protocol friction away.

## 10. Trust Assurance

*This chapter adds no obligations for Participants.* It defines how
conformance with the obligations stated elsewhere in this framework is
asserted, evidenced, and evaluated; its normative statements bind only the
Council's own assurance practice.

### 10.1 Mechanism classes

[ECS-TA-1] Assurance mechanisms in the ECS ecosystem are classified in
exactly three classes, and the Council MUST name the class of every
assurance claim it makes or relies on under this framework:
(a) **cryptographic/automatic** — enforced by the VPR protocol or by
cryptography (permission state and expiry, trust deposits, slashing,
digest-anchored documents, digest-anchored Evidence Checklists,
issuance-time anchoring); (b) **attested** — self-certification against
published criteria, reviewed before validation; (c) **assessed** —
evaluation by a party other than the asserter (committee review,
third-party audit).

*Non-normative note:* class (a) is the dominant column of the ECS
assurance matrix — most MUSTs in this framework are machine-enforced or
machine-evidenced on-chain, which is the ECS ecosystem's structural
advantage over paper-only frameworks. The derived, non-normative Trust
Assurance Matrix (Annex B) maps every requirement identifier of this
framework to its class, responsible role, and evidence. The Matrix is
deferred to a Controlled Document rather than shipped as an annex of this
draft because it is derived row-by-row from the ratified requirement set:
it can be frozen only once ratification freezes the identifiers, and
publishing a derivative before its source invites divergence.

### 10.2 Assurance posture at launch

[ECS-TA-2] At launch, the required assurance level for accredited roles is
self-certification: the applicant's completed, digest-anchored Evidence
Checklist plus committee review before validation; the Council MUST NOT
require third-party audits of launch-cohort applicants.

[ECS-TA-3] The Council MUST publish, in advance of applying them, the
escalation drivers that will raise required assurance to attested or
assessed levels for a (schema, role) — at minimum: aggregate credential
volume, aggregate trust-deposit value at risk, and entry of regulated
sectors relying on the schema — and any escalation applies only at
renewal, never retroactively mid-validity.

[ECS-TA-4] On-chain state proves registration and permission status; it
does not prove off-chain conduct. No party, including the Council, SHALL
claim more than reasonable assurance from ECS mechanisms, and relying
parties may infer less, but not more.

### 10.3 Monitoring

[ECS-TA-6] The Council SHOULD monitor conformance signals derivable from
public chain data via trust resolvers and indexers — including
revocation-registry availability, permission-state divergence, and
expired-but-unrenewed permissions — and MAY open a review under Chapter 11
on persistent anomalies.

### 10.4 Honest residuals

*This section is non-normative.* Relying parties should know what this
framework does **not** assure: (1) **revocation latency** — a verifier
caching credential or permission state may honor a revoked credential
until its cache refreshes; (2) **whitelist centralization** — trust-root
status is a social convention of VS/VUA operators ([WL]), and a widely
shared default whitelist is a concentration risk this framework can
acknowledge but not remove; (3) **slashes are burned, not compensating** —
a damaged party gains accountability from a slash, never restitution;
(4) **identity-verification quality** — verification is performed by
accredited humans and processes and is assured by classes (b) and (c),
not by the protocol. The Council answers for the efficacy of these rules,
not for the conduct of every Participant; accreditation is not a conduct
guarantee.

## 11. Sanctions and Disputes

### 11.1 Scope and grounds

[ECS-SANC-1] This chapter governs sanctions at ECS-ecosystem level only;
network-level sanctions (including network slashing via governance
proposal) are governed exclusively by Network GF chapters [NGF-SANC] and
[NGF-DISP], and nothing here reaches into any other ecosystem.

[ECS-SANC-2] Sanctions may be grounded only in enumerated **Cause**:
material breach of this framework or a Controlled Document binding the
Participant; material breach of the Participant Candidate Agreement;
material inaccuracy in accreditation evidence or breach of the continuing
accuracy duty ([ECS-ACC-14]); breach of the neutrality duty
([ECS-ACC-13]); failure of the availability asymmetry ([ECS-LIFE-11]);
unlawful use ([ECS-GEN-9]); fraud in issuance or verification; or an
unreported change of control past its disclosure deadline.

### 11.2 The graduated ladder

[ECS-SANC-3] Sanctions MUST proceed by the least severe sufficient rung of
the following ladder, each rung executed only after the due process of
[ECS-SANC-5]: (a) written warning; (b) remediation order with a cure
period per Annex A; (c) permission restriction (conditions on issuance, or
shortening of `effective_until` via [MOD-PP-MSG-8], executed by the direct
onboarding validator per [ECS-LIFE-14]); (d) suspension
(§8.5); (e) revocation of the permission ([MOD-PP-MSG-9]) with the Grace
Period duties of §8.6; (f) ecosystem slash of the trust deposit
([MOD-PP-MSG-12], burned per [MOD-TD-MSG-7], return conditioned on
[MOD-PP-MSG-13]).

[ECS-SANC-4] A slash under rung (f) MUST be proportionate to the gravity
and gain of the violation, sized against a published schedule in the
Operational Annex, and MUST NOT be a first-resort measure absent fraud;
repeat violations of the same Cause within 12 months escalate one rung
above the previous sanction.

### 11.3 Due process

[ECS-SANC-5] Before any on-chain sanction act, the respondent MUST
receive: written notice stating the alleged Cause with the requirement
identifiers concerned and the evidence; the applicable cure period
(Annex A), except where the violation is ongoing fraud or an active
security threat, in which case protective suspension MAY precede notice by
no more than 5 days; and the identity of the deciding body.

[ECS-SANC-6] Sanction decisions MUST be taken by Council members that are
disinterested in the matter (no related-party interest in the respondent
or a direct competitor-complainant), applying an engagement filter per the
Council's committee rules; if fewer than five qualifying members exist,
the qualifying members recommend and the General Assembly decides.

[ECS-SANC-7] Every sanction decision MUST be published with written
reasons on the Council's public record, symmetrically with
accreditations; publication MAY redact personal data and active-security
detail.

[ECS-SANC-8] A permission granted through a procedurally defective
process is reviewable, not void: it remains effective until reviewed and
ratified, amended, or revoked, so that defects do not cascade invalidity
through credential chains onto innocent holders.

### 11.4 Revocation requests and challenges

[ECS-SANC-9] Any party MAY submit a revocation request or challenge
against an ECS credential or accreditation, stating one of the enumerated
grounds of the relevant framework chapter with evidence; the competent
issuer or the Council MUST verify the requester's identity and the ground,
and MUST respond with a reasoned decision within 15 days.

### 11.5 Appeals and disputes

[ECS-SANC-10] A sanctioned or refused party MAY appeal within the Annex A
appeal window to a review body other than the one that decided: decisions
of an Issuer Grantor appeal to the Council; decisions of the Council or
its committee appeal to a panel of disinterested members not involved in
the original decision; the final internal appeal lies to the General
Assembly.

[ECS-SANC-11] An appeal against a slash (rung f) suspends its on-chain
execution until the appeal is decided, unless the deciding body finds, in
writing, an imminent-harm ground for immediate execution.

[ECS-SANC-12] Disputes between ECS Participants that do not allege Cause
are resolved by: (a) good-faith bilateral negotiation; (b) failing that,
mediation facilitated by the Council's chartered committee; (c) failing
that, a reasoned Council decision, appealable per [ECS-SANC-10];
association-side legal disputes follow the arbitration provisions of the
Council's statutes and the Network GF.

[ECS-SANC-13] Every sanction decision and every appeal decision under this
chapter is subject to a decision deadline (Initial Parameter, Annex A)
running from complete referral or, where the respondent is given a cure
period or response window, from the respondent's complete response; a
matter undecided at the deadline escalates automatically to the General
Assembly, per the vacancy pattern of [ECS-ACC-5].

### 11.6 Public claims and marks

[ECS-TA-5] A party MAY publicly claim accreditation or conformance under
this framework if and only if the claim is true as a pure function of live
on-chain state per the collapse rule of [ECS-GEN-13] (VALIDATED,
unexpired, unrevoked, not slashed); any such claim MUST embed or link the
DID that lets a relying party resolve live status, and a party whose
permission ceases to satisfy the rule MUST remove the claim within
5 days.

## 12. Privacy and Data Protection

[ECS-PRIV-1] No personal data SHALL be written to the Verana network in
connection with the ECS ecosystem: on-chain entries carry identifiers,
digests, permission state, and fee data only, and evidence lives
off-chain with the party that collected it.

[ECS-PRIV-2] Every Participant processing personal data in an ECS role
(notably Persona issuers and Issuer Grantors) MUST comply with the data
protection law applicable to it, and, where no such law applies, MUST
apply the Swiss Federal Act on Data Protection as its material minimum.

[ECS-PRIV-3] Issuance evidence MUST be limited to what the applicable
Evidence Checklist requires (data minimization), retained no longer than
the Annex A retention period, and protected with controls proportionate
to its sensitivity.

[ECS-PRIV-4] The consent rules of [ECS-PER-7] (recorded consent,
withdrawal-triggers-revocation, deletion of published derivatives) apply
to every publication of personal data under this framework.

[ECS-PRIV-5] Verifiers MUST NOT retain personal data from ECS credential
presentations beyond the purpose and duration for which it was presented,
and MUST NOT use UserAgent presentations for cross-context correlation
([ECS-UA-7]).

*Non-normative note on digests:* the network anchors JCS digests of W3C
credentials to establish objective issuance time. A digest is
deliberately non-reversible and is anchored without the underlying data;
the design intent is that anchored digests are not usable as personal
data, and the UserAgent schema goes further by using AnonCreds, whose
derived presentations are unlinkable by construction. The Council states
this rationale here, in advance, rather than leaving the question to
enforcement.

## 13. Amendment

[ECS-AMND-1] An amendment to this framework MUST be adopted by the Council
under the voting rule of Network GF [NGF-GOV-6] to [NGF-GOV-8], after a
public comment period of no fewer than 30 days on the published draft,
with a published disposition of comments.

[ECS-AMND-2] Once the network is live, an adopted amendment takes legal
effect only through on-chain activation of a new
`GovernanceFrameworkVersion` ([MOD-GF-MSG-1] / [MOD-GF-MSG-2]); for
material changes the version's `active_since` MUST lie at least 30 days
after adoption, and the active version is immutable.

[ECS-AMND-3] Each row of this document's version history MUST correspond
one-to-one with an on-chain version activation (once live), naming the
adopting resolution.

[ECS-AMND-4] Emergency security amendments MAY bypass the comment period,
with prompt public notice and ratification by the ⅔ supermajority at the
next Council decision cycle; an unratified emergency amendment lapses.

[ECS-AMND-5] Changes to Annex A Initial Parameters follow the change
process stated per parameter, and every parameter change MUST be
published with a written justification naming the trade-offs considered,
together with a human-readable description of the change and its expected
effect; the Council MUST review all Annex A parameters in an open public
review at least annually.

[ECS-AMND-6] Controlled Documents (Annex B) amend on their own lighter
track — committee proposal, 15-day public comment, Council adoption —
and MUST NOT contradict this framework; on conflict this framework
controls.

## 14. Transition

*Non-normative note:* this chapter states how the ECS ecosystem gets from
draft to operating, with the same event-triggered honesty as the Council's
own bootstrap.

[ECS-TRAN-1] The recruitment sequence for ECS Ecosystem Participants is:
(a) this framework is delivered and ratified; (b) recruitment opens
(target Q4 2026), in parallel with ongoing Council recruitment; (c) the
initial cohort of Participants is accredited and permissioned in time for
mainnet launch (target Q1 2027); the Council MUST NOT accredit any
Participant before the criteria of [ECS-ACC-1] for its role are published.

[ECS-TRAN-2] Until dedicated tooling exists, candidates express interest
through the veranacouncil.org contact form (inquiry type "ECS
participant"); expressions of interest are non-binding, create no
priority other than FIFO position once a complete application is filed,
and are not published.

[ECS-TRAN-3] Pre-incorporation, 2060 OÜ as transitional steward MAY
administer the candidate pipeline of [ECS-TRAN-2] (intake and due
diligence preparation) but holds no accreditation power under this
framework; all accreditation decisions are Council decisions per
Chapter 7, and every steward function under this framework sunsets
automatically at mainnet launch.

[ECS-TRAN-4] Accreditations decided before the network is live MUST be
executed on-chain (Chapter 8 activation) as part of mainnet genesis or
immediately thereafter, and each pre-mainnet accreditation MUST be
re-verified as still meeting its criteria if more than 12 months elapse
between decision and on-chain activation.

[ECS-TRAN-5] Any "founding participant" designation or visual distinction
granted to the initial cohort MUST carry a published sunset date.

## Annex A. Initial Parameters

*This annex is normative.* Every quantified threshold of this framework is
collected here. Values marked "schema config" are written into the
CredentialSchema entries per Table 2. The protocol caps every validity
period at 3650 days (GlobalVariables).

| # | Parameter | Initial value | Change process |
| --- | --- | --- | --- |
| A1 | `issuer_grantor_validation_validity_period` (Organization, Persona) | 365 days | [ECS-AMND-5] + schema config |
| A2 | `issuer_validation_validity_period` (all four schemas) | 365 days | [ECS-AMND-5] + schema config |
| A3 | `verifier_validation_validity_period` (all four schemas) | 365 days | [ECS-AMND-5] + schema config |
| A4 | `holder_validation_validity_period` (Service, Organization, Persona) | 365 days | [ECS-AMND-5] + schema config |
| A5 | `holder_validation_validity_period` (UserAgent) | 0 (no holder onboarding; `PERMISSIONLESS`) | [ECS-AMND-5] + schema config |
| A6 | Credential lifetime (`validUntil` − `validFrom`): Organization, Persona, Service | ≤ 365 days | [ECS-AMND-5] |
| A7 | Credential lifetime: UserAgent | no fixed expiry; revocation-based | [ECS-AMND-5] |
| A8 | `validation_fees` (all schemas, all roles) | 0 TU | [ECS-AMND-5] |
| A9 | `issuance_fees` (all schemas) | 0 TU | [ECS-AMND-5] |
| A10 | `verification_fees` (all schemas) | 0 TU | [ECS-AMND-5] |
| A11 | Fee upper bound once fees activate ([ECS-FEE-5]) | 0 TU until amended | [ECS-AMND-5] |
| A12 | Grace Period after involuntary issuer termination | 90 days | [ECS-AMND-5] |
| A13 | Persona identity-proofing recency ([ECS-PER-3]) | ≤ 30 days before issuance | [ECS-AMND-5] |
| A14 | Applicant evidence window ([ECS-ACC-11]) | 60 days | [ECS-AMND-5] |
| A15 | Completeness-check period ([ECS-ACC-11]) | 10 days | [ECS-AMND-5] |
| A16 | Substantive-review period ([ECS-ACC-11]) | 60 days | [ECS-AMND-5] |
| A17 | Concurrent substantive reviews workload cap ([ECS-ACC-10]) | 5 | [ECS-AMND-5] |
| A18 | Activation window before an onboarding process lapses ([ECS-LIFE-6]) | 180 days | [ECS-AMND-5] |
| A19 | Cure period, standard ([ECS-SANC-3] rung b) | 15 days | [ECS-AMND-5] |
| A20 | Cure period, core duties (revocation availability, permission-state accuracy, fraud-adjacent) | 5 days | [ECS-AMND-5] |
| A21 | Suspension auto-termination clock ([ECS-LIFE-15]) | 180 days | [ECS-AMND-5] |
| A22 | Appeal window ([ECS-SANC-10]) | 30 days from notified decision | [ECS-AMND-5] |
| A23 | Change-of-control disclosure period ([ECS-ACC-14]) | 30 days | [ECS-AMND-5] |
| A24 | Incident / breach notice ([ECS-LIFE-12]) | 72 hours | [ECS-AMND-5] |
| A25 | Key-compromise notice ([ECS-LIFE-12]) | 24 hours | [ECS-AMND-5] |
| A26 | Notice of material framework changes ([ECS-LIFE-13]) | ≥ 30 days | [ECS-AMND-1] |
| A27 | Evidence retention period ([ECS-ORG-12], [ECS-PER-9], [ECS-LIFE-18]) | validity period of the supported permission + 24 months | [ECS-AMND-5] |
| A28 | Revocation-request response deadline ([ECS-SANC-9]) | 15 days | [ECS-AMND-5] |
| A29 | Key-rotation announcement deadline ([ECS-ROOT-7]) | 7 days | [ECS-AMND-5] |
| A30 | Public-claim removal deadline ([ECS-TA-5]) | 5 days | [ECS-AMND-5] |
| A31 | Sanction / appeal decision deadline ([ECS-SANC-13]) | 60 days | [ECS-AMND-5] |

> **[DECISION]** *Annex A values A1–A7, A12–A31.* The validity periods
> (365 days), Grace Period (90 days), proofing recency (30 days), and the
> process clocks are recommendations synthesized from operating precedents
> (GLEIF's 90-day grace period and 60/10/60-day qualification clocks;
> Sovrin's 180-day no-limbo rules; NIST/eIDAS proofing practice), chosen
> for a small launch-cohort Council. None is dictated by the
> specifications; Founding Members should confirm each value at
> ratification.

## Annex B. Schedule of Controlled Documents

*This annex is normative as to the list; the documents bind per
[ECS-AMND-6] once adopted.* Only documents the Council genuinely plans are
listed; each has an owner and a target date.

| Controlled Document | Charter (one sentence) | Owner | Target |
| --- | --- | --- | --- |
| Participant Candidate Agreement | The uniform agreement executed by every applicant for a permissioned ECS role, derived from this framework (replaces the abandoned participant MoU) | Council (accreditation committee drafts) | Q4 2026, before recruitment opens |
| ECS Onboarding and Identity Verification Operational Annex | Ceremony scripts, challenge formats, recognized registry and eID lists, sanctions-screening levels, slash schedule, and the ECS Ecosystem DID key-management procedures | Council (accreditation committee) | Q4 2026, before recruitment opens |
| SchemaAuthorizationPolicy documents, per gated (schema, ISSUER) and (schema, VERIFIER) | The objective accreditation criteria per [ECS-ACC-1](a), published on-chain (url + digest_sri) — the protocol accepts policies only for the `ISSUER` and `VERIFIER` roles | Council | With schema creation; before first application intake |
| Criteria Controlled Documents, per gated (schema, ISSUER_GRANTOR) and (schema, HOLDER) | The objective accreditation criteria per [ECS-ACC-1](b), digest-anchored and resolvable per [ECS-GEN-7] | Council | Before first application intake |
| Evidence Checklists, per gated (schema, role) | The uniform evidence instrument whose completed digest is anchored per [ECS-ACC-8] | Council (accreditation committee) | Q4 2026 |
| Trust Assurance Matrix (derived, non-normative) | Mapping of every requirement identifier to assurance class, responsible role, and evidence ([ECS-TA-1]) | Council | Before mainnet (Q1 2027) |

## Version History

| Version | Date | Status | Summary |
| --- | --- | --- | --- |
| 0.1 | 2026-07-05 | Draft | First draft for co-authoring by Founding Members. |
