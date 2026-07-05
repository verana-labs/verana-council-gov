# Template Ecosystem Governance Framework (Template EGF)

| Field | Value |
| --- | --- |
| Document Name | Template Ecosystem Governance Framework (Template EGF) |
| Version | DRAFT 0.1 |
| Status | Draft for co-authoring by Founding Members |
| Governs | Nothing by itself — a voluntary scaffold; the `[TEGF-n]` requirements of section 5 bind only ecosystems that derive their EGF from this template or represent their EGF as conformant with this template |
| Governed By | The Verana Council Association (in formation), acting through the mechanisms of Network GF chapter [NGF-GOV] |
| Approved By | Pending — Incorporation General Assembly, target Q3 2026 |
| Approval Date | Pending |
| License | CC-BY-SA 4.0 |
| Anchoring | Git history and public URL in `verana-labs/verana-council-gov` now; on-chain `GovernanceFrameworkDocument` (`url` + `digest_sri`) once the network is live |

> **Status: DRAFT 0.1.** This is a first draft prepared for co-authoring by the
> Founding Members of the Verana Council Association, for ratification at the
> Q3 2026 Incorporation General Assembly. Where this document states protocol
> facts, the [Verifiable Trust specification](https://verana-labs.github.io/verifiable-trust-spec/)
> and the [Verifiable Public Registry (VPR) specification](https://verana-labs.github.io/verifiable-trust-vpr-spec/)
> prevail. Where it states entity facts, the Council's definitions record and
> public record prevail. During the pre-incorporation period, 2060 OÜ acts as
> transitional steward of the Council; every steward power carries an
> event-triggered sunset (see Network GF chapter [NGF-TRAN]).

## 1. Welcome: Creating an Ecosystem on Verana

*This section is non-normative.*

Anyone can create an ecosystem on the Verana network. No application to the
Verana Council is required, no approval is given or needed, and no fee is
payable to the Council. Ecosystem creation is permissionless by protocol
design: any organization that registers a Corporation entry on the Verifiable
Public Registry (VPR) can create an Ecosystem entry, publish its own
Ecosystem Governance Framework (EGF), define its own credential schemas, and
operate its own participant tree — all without asking anybody.

This template exists to make that easy. It is a fill-in-the-blanks scaffold
for writing an EGF that:

- works with the VPR's on-chain mechanics out of the box (onboarding modes,
  permission trees, trust deposits, fees, slashing, governance-framework
  anchoring);
- satisfies, by construction, the mandatory-content requirements that the
  Verana Network Governance Framework (Network GF) chapter [NGF-EGF] places on
  every EGF published on the network; and
- avoids the failure modes documented across a decade of real-world
  governance frameworks: unnumbered rules, zombie suspensions, sanctions
  without due process, dead links, and thresholds written as adjectives
  instead of numbers.

Three things this template is **not**:

- **It is not a gate.** Using this template is voluntary. You may write your
  EGF from scratch, so long as it satisfies Network GF chapter [NGF-EGF].
- **It is not an endorsement.** Using this template does not imply any
  endorsement, accreditation, certification, or recognition of your ecosystem
  by the Verana Council. Creating an ecosystem is not the same as being
  trusted; trust on Verana is earned through the choices of relying parties.
- **It is not a straitjacket.** Almost everything here is a suggested
  default you may edit. The few things you must keep are marked as such and
  listed in section 5.

The Council practices what it publishes: the **ECS Ecosystem Governance
Framework (ECS-EGF)** — the framework governing the four Essential Credential
Schemas — is the worked example of this template. When an instruction below
feels abstract, read the corresponding section of the ECS-EGF to see it
filled in for a real ecosystem.

## 2. How to Use This Template

*This section is non-normative, except where it restates requirements defined
in section 5.*

### 2.1 The three-mode convention

Everything from section T1 onward is template material, written in three
modes:

1. **Suggested text** (plain text). Default wording you can keep as-is or
   edit. It is written so that an ecosystem produces a valid EGF by
   *editing*, not authoring from a blank page.
2. **⟨Angle-bracket fields⟩**. Mandatory fill-ins. Every ⟨field⟩ must be
   replaced with your ecosystem's own value before publication. Where a
   sensible default exists, it is shown as ⟨field — suggested: value⟩.
3. **Instruction blocks**, rendered as blockquotes beginning with
   "*Instruction:*". Authoring guidance addressed to you, the EGF author.
   Every Instruction block must be deleted before publication — it is
   scaffolding, not framework text.

### 2.2 The completion rule

Because published EGFs are anchored on-chain by digest, completion is
machine-checkable: a finished EGF contains no "*Instruction:*" blocks and no
unresolved "⟨" / "⟩" fill-in markers. Requirement [TEGF-4] in section 5 makes
this the activation rule — an EGF derived from this template must not be
anchored at ecosystem creation or activated on-chain while any of either
remains. A simple text search over the digest-anchored document verifies
compliance.

### 2.3 Silence is never ambiguous

Where a section genuinely does not apply to your ecosystem, write
"**No stipulation.**" rather than deleting the section. A deliberately empty
slot tells readers you considered the topic and decided it needs no rule; a
missing section tells them nothing.

### 2.4 Where to get help

- The **ECS-EGF** is the worked example of every section below.
- The **Network GF** defines the constitutional floor every EGF must respect,
  including chapter [NGF-EGF] (requirements for EGFs) — Annex A of this
  template maps each of its mandatory-content items to the template section
  that satisfies it.
- The **VT and VPR specifications** define every protocol object this
  template references. This template never restates the specs; where it
  summarizes them, the specs prevail.

## 3. Conformance

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in [BCP 14](https://www.rfc-editor.org/info/bcp14)
[RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174)
when, and only when, they appear in all capitals, as shown here.

Normativity in this document has two distinct scopes:

- The `[TEGF-n]` requirements in section 5 are normative **for users of this
  template**: an ecosystem claiming to have derived its EGF from this
  template is bound by them.
- The suggested text in sections T1–T14 is **not normative as written
  here**. It becomes normative only inside the EGF an ecosystem publishes,
  where it binds that ecosystem's own participants under that ecosystem's own
  authority.

Sections marked "*This section is non-normative.*" contain no requirements in
either scope.

## 4. Terminology

Terms defined in the [Verifiable Trust specification](https://verana-labs.github.io/verifiable-trust-spec/)
and the [VPR specification](https://verana-labs.github.io/verifiable-trust-vpr-spec/)
are used with the meanings given there and are not redefined here. This
includes: Corporation, Ecosystem, CredentialSchema, Participant, onboarding
process, trust deposit, trust unit, Verifiable Service, Verifiable User
Agent, and the participant roles ECOSYSTEM, ISSUER_GRANTOR, VERIFIER_GRANTOR,
ISSUER, VERIFIER, HOLDER.

The following local terms are used in this document. Definitions contain no
normative keywords.

- **Ecosystem Governance Framework (EGF)**: the set of governance documents
  an ecosystem publishes on-chain as its `GovernanceFrameworkVersion` /
  `GovernanceFrameworkDocument` entries, together constituting the rules of
  that ecosystem.
- **Ecosystem governance authority (EGA)**: the organization accountable for
  an ecosystem's EGF — the ecosystem-level counterpart of the VPR
  specification's "governance authority". Never abbreviated to "GA" in
  Council documents; "General Assembly" is always spelled out.
- **Network GF**: the Verana Network Governance Framework, the constitutional
  layer that every EGF on the Verana network supplements and must not
  contradict.
- **Network validator**: an operator of a consensus node securing the Verana
  network chain. Only Verana Council members operate network validators.
- **Onboarding validator**: the Participant that validates an applicant in an
  on-chain onboarding process (the "validator" of the VPR's Participant
  module). Unrelated to network validators; the bare word "validator" is
  avoided throughout.
- **Instruction block**: a blockquote beginning with "*Instruction:*",
  addressed to the EGF author and deleted before publication.
- **Fill-in field**: a mandatory placeholder written between ⟨angle
  brackets⟩.
- **Suggested text**: template prose an ecosystem may keep or edit.
- **Grace Period**: a defined time window following an involuntary
  revocation during which already-issued credentials remain verifiable while
  affected parties migrate.
- **Controlled Document**: a separately versioned document referenced from an
  EGF, revisable through the EGF's stated amendment process.
- **Member**: a member of the Verana Council Association (a Swiss Verein).
  Distinct from **Participant**, which is strictly an on-chain role in an
  ecosystem's permission tree. This template never uses "member" for
  ecosystem roles.

## 5. Template Requirements

This section is normative for any ecosystem that derives its EGF from this
template or represents its EGF as conformant with this template.

- **[TEGF-1]** An ecosystem MUST NOT represent its use of this template, or
  the existence of its ecosystem on the Verana network, as an endorsement,
  accreditation, certification, or approval by the Verana Council.
- **[TEGF-2]** Before publication, the EGF author MUST replace every
  fill-in field with the ecosystem's own value.
- **[TEGF-3]** Before publication, the EGF author MUST delete every
  Instruction block.
- **[TEGF-4]** An EGF derived from this template MUST NOT be anchored as
  version 1 at ecosystem creation (Create New Ecosystem, [MOD-ES-MSG-1]) or
  activated on-chain (Increase Active Governance Framework Version,
  [MOD-GF-MSG-2]) while any Instruction block or unresolved fill-in field
  remains in any of its `GovernanceFrameworkDocument` entries. Version 1
  activates atomically at ecosystem creation, so it MUST be complete before
  [MOD-ES-MSG-1] is executed.
- **[TEGF-5]** The EGF MUST retain a layering clause equivalent in substance
  to section T2.3: a statement that the EGF supplements and does not
  supersede the Verana Network Governance Framework, and that on conflict
  the Network GF controls.
- **[TEGF-6]** The EGF MAY tighten requirements the Network GF places on
  ecosystem participants; it MUST NOT loosen them.
- **[TEGF-7]** Where a template section does not apply, the EGF MUST state
  "No stipulation." rather than omit the section, so that silence is
  distinguishable from oversight.
- **[TEGF-8]** Every published `GovernanceFrameworkDocument` URL MUST be
  publicly resolvable without authentication; the on-chain `digest_sri` is
  the canonical identity of each document version, and web copies that do not
  match it have no effect.
- **[TEGF-9]** Regardless of how closely this template is followed, the
  published EGF MUST satisfy every requirement of Network GF chapter
  [NGF-EGF]; conformance with this template is an aid, not a substitute.
- **[TEGF-10]** Every quantified threshold in the EGF MUST be stated as a
  number (not an adjective) and MUST be listed in the EGF's Initial
  Parameters annex together with its change process.
- **[TEGF-11]** Every uniquely addressable requirement in the EGF SHOULD
  carry a stable bracketed identifier with the ecosystem's own prefix, carry
  exactly one RFC 2119 keyword, and be addressed to a named role.
  Identifiers, once assigned, MUST NOT be reused or renumbered.
- **[TEGF-12]** An EGF derived from this template is an adaptation of a
  CC-BY-SA 4.0 work: it MUST be licensed under CC-BY-SA 4.0 (or a compatible
  license per the CC-BY-SA 4.0 terms) and MUST attribute the Verana Council
  Association as the author of the template.
- **[TEGF-13]** The EGF MUST NOT require any conduct that would cause a
  participant to breach law applicable to that participant, and MUST state
  this (the legal-safety clause of section T2.5).
- **[TEGF-14]** The EGF MUST NOT place personal data on-chain, and MUST NOT
  require any participant to do so (see section T12).

> *Instruction blocks begin from here. Everything from section T1 onward is
> template material: keep or edit the plain text, resolve every ⟨field⟩, and
> delete every Instruction block — including this one — before publication.*

## T1. Document Metadata and Status

> *Instruction:* This block becomes the front matter of your EGF. The table
> mirrors the on-chain fields of your Ecosystem and its
> `GovernanceFrameworkVersion` / `GovernanceFrameworkDocument` entries, so a
> reader can verify the document against the chain and vice versa. Fill the
> on-chain rows after executing the publication sequence in Annex B; version
> 1 is anchored and activated atomically when the Ecosystem entry is created
> ([MOD-ES-MSG-1]), so complete this document and publish it at a stable URL
> before that step. Choose a short stable requirement-ID
> prefix for your ecosystem (2–5 uppercase letters, e.g. "HLTH" for a health
> ecosystem); it is used in every requirement identifier below.

| Field | Value |
| --- | --- |
| Document Name | ⟨Ecosystem Name⟩ Ecosystem Governance Framework |
| Version | ⟨integer, starting at 1⟩ |
| Status | ⟨Draft / Active⟩ |
| Governs | The ⟨Ecosystem Name⟩ ecosystem on the Verana network |
| Governed By | ⟨Legal name of the ecosystem governance authority⟩ |
| Requirement-ID prefix | ⟨PREFIX⟩ |
| Ecosystem DID | ⟨did:…⟩ |
| Corporation DID | ⟨did:… of the Corporation entry controlling this Ecosystem⟩ |
| Corporation `policy_address` | ⟨on-chain policy account address of the Corporation entry⟩ |
| Primary language | ⟨IETF language tag, e.g. "en"⟩ |
| On-chain GF version | ⟨GovernanceFrameworkVersion number⟩ |
| Active since | ⟨active_since timestamp, once activated⟩ |
| Document URL | ⟨publicly resolvable URL, no authentication⟩ |
| Document digest | ⟨digest_sri as anchored on-chain⟩ |
| License | ⟨CC-BY-SA 4.0⟩ |
| Contact | ⟨email or DIDComm endpoint of the EGA⟩ |

> *Instruction:* Keep a change-log table under this metadata block. Its rows
> MUST correspond one-to-one with on-chain `GovernanceFrameworkVersion`
> activations: one row per activated version, with date and a one-line
> description. Active on-chain versions are immutable; corrections always
> mean a new version.

| Version | Date | Description |
| --- | --- | --- |
| 1 | ⟨date⟩ | Initial version |

## T2. Introduction, Scope and Purpose

### T2.1 Purpose

*This section is non-normative.*

The ⟨Ecosystem Name⟩ ecosystem exists to ⟨one-paragraph mission: what
credential-based trust problem this ecosystem solves, for whom⟩.

> *Instruction:* Keep the purpose to one paragraph and keep it inside your
> actual authority: state objectives your EGF has the mechanisms to achieve.
> Do not promise outcomes (such as fraud elimination) that no governance
> framework can deliver; state what your rules make verifiable instead.

### T2.2 Scope

This framework governs:

- the credential schemas listed in section T6 and no others;
- the participants holding on-chain permissions in the ⟨Ecosystem Name⟩
  permission tree, in the roles defined in section T7; and
- the conduct of the ecosystem governance authority itself, as stated in
  section T4.

This framework does not govern the Verana network, other ecosystems, or any
party that has not accepted it under section T2.4.

### T2.3 Layering

This framework supplements and does not supersede the Verana Network
Governance Framework; on conflict the Network GF controls.

Within this ecosystem's own document stack, precedence is: the Network GF,
then this framework, then its Controlled Documents, then participant
agreements and checklists. A lower document tightens but never loosens a
higher one.

> *Instruction:* The first sentence of T2.3 is mandatory boilerplate
> ([TEGF-5]) — retain its substance (supplement-not-supersede; the Network
> GF controls on conflict), adapting the wording if needed. It is what keeps
> hundreds of autonomous, never-approved EGFs coherent on one network.

### T2.4 Acceptance

Participation in this ecosystem — starting or renewing an onboarding process,
holding a permission, issuing, verifying, or holding credentials under a
schema of this ecosystem — constitutes acceptance of the version of this
framework active on-chain at the time of the relevant act.

### T2.5 Legal safety

Nothing in this framework requires any party to act in breach of law
applicable to it. Where compliance with this framework would breach
applicable law, the party MUST notify the ecosystem governance authority and
the parties MUST seek a conforming alternative.

## T3. Conformance and Terminology

Suggested text:

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 (RFC 2119, RFC 8174)
when, and only when, they appear in all capitals, as shown here.

Terms defined in the Verifiable Trust specification and the VPR specification
are used with the meanings given there. Local terms:

- ⟨term⟩: ⟨definition — no normative keywords inside definitions⟩

> *Instruction:* Define only terms local to your ecosystem (sector jargon,
> your role names, your assurance levels). Never redefine a spec term, and
> never hide a MUST inside a definition — auditors scan requirement IDs, not
> glossaries. Disambiguate "network validator" vs "onboarding validator" if
> your text needs either.

## T4. Ecosystem Governance Authority

### T4.1 Identification

The ecosystem governance authority (EGA) of the ⟨Ecosystem Name⟩ ecosystem
is:

| Field | Value |
| --- | --- |
| Legal name | ⟨legal name⟩ |
| Legal form and registry | ⟨e.g. GmbH, registered at …, registration number …⟩ |
| Legal jurisdiction | ⟨country / state of the EGA⟩ |
| Governing law of this framework | ⟨governing law⟩ |
| Registered address | ⟨address⟩ |
| Public contact | ⟨email⟩ |
| DIDComm contact | ⟨DID with DIDComm service endpoint⟩ |
| Website | ⟨URL⟩ |

- [⟨PREFIX⟩-EGA-1] The EGA MUST keep the identification table above accurate
  and MUST publish a corrected framework version within ⟨days — suggested:
  30⟩ days of any change to it.
- [⟨PREFIX⟩-EGA-2] The EGA MUST maintain control of the Ecosystem DID and
  the Corporation `policy_address` stated in section T1, and MUST publish
  its procedures for key rotation and for orderly migration or abandonment
  of the Ecosystem DID.
- [⟨PREFIX⟩-EGA-3] The EGA MUST designate an intake channel for reports of
  suspected violations of this framework, together with an escalation path
  for the case where the channel's administrator is itself the subject of
  the report.
- [⟨PREFIX⟩-EGA-4] If a body designated in this framework is vacant or
  unable to act, its duties revert to ⟨the EGA's supreme decision-making
  organ, e.g. its board or assembly of participants⟩ until the vacancy is
  filled.

> *Instruction:* Section T4.2 below matters more than it looks. Your
> Ecosystem DID is what relying parties resolve, whitelist, and terminate
> trust resolution at; its integrity carries your entire trust graph. Sector
> ecosystems rarely think of DID lifecycle governance unprompted — say now
> what happens at genesis, on key rotation, and if you ever walk away.

### T4.2 Ecosystem DID lifecycle

- [⟨PREFIX⟩-EGA-5] The EGA MUST publish, at ⟨list of at least two
  independent publication points, e.g. this document and the EGA website⟩,
  the Ecosystem DID and any planned change to it, with at least ⟨days —
  suggested: 30⟩ days' notice before a migration takes effect.
- [⟨PREFIX⟩-EGA-6] If the EGA permanently ceases to operate this ecosystem,
  it MUST publish an abandonment notice, revoke or wind down outstanding
  permissions per section T8, and MUST NOT transfer control of the Ecosystem
  DID to another party without publishing the transfer.

### T4.3 What the EGA answers for

*This section is non-normative.*

Each role in this ecosystem answers for its own function. The EGA answers
for the efficacy and fair administration of these rules — not for the
conduct of every participant. A permission granted under this framework
records that published criteria were met at validation time; it is not a
guarantee of ongoing good conduct. Relying parties retain their own
obligation to decide, per purpose, whether a verified credential is valid
for their use.

## T5. Ecosystem On-Chain Setup

Suggested text:

The ⟨Ecosystem Name⟩ ecosystem exists on the Verana VPR as:

- a Corporation entry (DID and `policy_address` per section T1), created via
  Create New Corporation [MOD-CO-MSG-1];
- an Ecosystem entry (Ecosystem DID, primary language) created via Create
  New Ecosystem [MOD-ES-MSG-1], which anchors and activates version 1 of
  this framework (url + digest_sri) atomically at creation;
- subsequent versions of this framework, anchored via [MOD-GF-MSG-1] and
  activated via [MOD-GF-MSG-2];
- one CredentialSchema entry per schema in section T6, created via
  [MOD-CS-MSG-1]; and
- a root ECOSYSTEM Participant entry per schema, created via Create Root
  Participant [MOD-PP-MSG-7], anchoring the permission tree of section T7.

> *Instruction:* Annex B gives the exact message sequence with explanations.
> If you publish objective accreditation criteria as on-chain
> SchemaAuthorizationPolicy documents ([MOD-CS-MSG-5]/[MOD-CS-MSG-6]),
> reference them here and in section T8; once a policy is active, the VPR
> obliges the granting corporation to issue an Issuer Authorization
> Credential (IAC) or Verifier Authorization Credential (VAC) to each
> successfully onboarded candidate.

## T6. Credential Schemas

> *Instruction:* Repeat the pattern below once per credential schema. Keep
> the section skeleton identical across schemas — holding the boilerplate
> constant is what makes the differences between schemas auditable. The
> on-chain configuration table mirrors the fields of [MOD-CS-MSG-1]; every
> value you write here must equal the value you submit on-chain.
>
> **Choosing onboarding modes** — this is the single most consequential set
> of choices in your EGF. The VPR offers, per schema:
>
> - `issuer_onboarding_mode` and `verifier_onboarding_mode`, each one of:
>   - `OPEN` — anyone may act in the role without an onboarding process.
>     Lowest friction, no vetting; appropriate for low-risk schemas or where
>     verification is meant to be universal. Note that OPEN does not mean
>     free: per-operation fees may still apply. OPEN role-holders must still
>     self-create a Participant entry on-chain (Self Create Participant,
>     [MOD-PP-MSG-14]) before acting — the entry anchors their trust deposit
>     and remains subject to revocation and slashing by the ecosystem.
>   - `GRANTOR_ONBOARDING_PROCESS` — candidates onboard with an intermediary
>     grantor (ISSUER_GRANTOR / VERIFIER_GRANTOR) that your ecosystem has
>     itself onboarded. Choose this to delegate vetting at scale, e.g. one
>     grantor per country or industry segment.
>   - `ECOSYSTEM_ONBOARDING_PROCESS` — candidates onboard directly with the
>     ecosystem (you). Maximum control, no delegation; appropriate for small
>     or high-assurance issuer sets.
> - `holder_onboarding_mode`, one of:
>   - `ISSUER_ONBOARDING_PROCESS` — holders get a Participant entry through
>     an onboarding process with an issuer; enables on-chain revocation
>     status checks and holder-side validation fees.
>   - `PERMISSIONLESS` — holders need no Participant entry (and issuers
>     cannot charge validation fees to candidate holders through the VPR).
> - Validity periods, in days, per role (`issuer_grantor_`,
>   `verifier_grantor_`, `issuer_`, `verifier_`,
>   `holder_validation_validity_period`): 0 means never expires; each is
>   capped by the network's GlobalVariables maxima (3650 days at Verana
>   genesis, changeable by governance proposal). Shorter periods force
>   requalification;
>   longer periods lower friction. Pick numbers, and repeat them in your
>   Initial Parameters annex.
> - `pricing_asset_type` and `pricing_asset`: `TU` (trust unit — a stable
>   unit converted via the network's on-chain exchange rate; the
>   VPR-native default), `COIN` (a token available on the chain, e.g.
>   `uvna`), or `FIAT` (chain used for settlement recording only; payment
>   happens off-chain). Trust deposits are always handled in the native
>   denom regardless of this choice.
> - `digest_algorithm` for credentials issued under the schema, per the VT
>   specification (SHA384 or SHA512).

### T6.⟨n⟩ ⟨Schema Name⟩ Credential

#### Purpose and credential definition

*This subsection is non-normative.*

⟨What this credential attests, about which subjects, for which relying
parties.⟩

The canonical JSON schema is published at ⟨permanent URL⟩ with digest
⟨digest_sri of the `json_schema`⟩. The JSON schema stored on-chain (JCS
canonical form) is authoritative.

#### On-chain configuration

| Field | Value |
| --- | --- |
| `issuer_onboarding_mode` | ⟨OPEN / GRANTOR_ONBOARDING_PROCESS / ECOSYSTEM_ONBOARDING_PROCESS⟩ |
| `verifier_onboarding_mode` | ⟨OPEN / GRANTOR_ONBOARDING_PROCESS / ECOSYSTEM_ONBOARDING_PROCESS⟩ |
| `holder_onboarding_mode` | ⟨ISSUER_ONBOARDING_PROCESS / PERMISSIONLESS⟩ |
| `issuer_grantor_validation_validity_period` | ⟨days, 0 to the network maximum — suggested: 365⟩ |
| `verifier_grantor_validation_validity_period` | ⟨days, 0 to the network maximum — suggested: 365⟩ |
| `issuer_validation_validity_period` | ⟨days, 0 to the network maximum — suggested: 365⟩ |
| `verifier_validation_validity_period` | ⟨days, 0 to the network maximum — suggested: 365⟩ |
| `holder_validation_validity_period` | ⟨days, 0 to the network maximum — suggested: 365⟩ |
| `pricing_asset_type` | ⟨TU / COIN / FIAT — suggested: TU⟩ |
| `pricing_asset` | ⟨"tu", denom, or currency code⟩ |
| `digest_algorithm` | ⟨SHA384 / SHA512⟩ |

> **[DECISION]** The template suggests 365-day validity periods for every
> role and TU as the pricing asset. Neither the specs nor the Network GF fix
> defaults; 365 days aligns annual requalification with common audit cycles,
> and TU insulates fee schedules from token volatility. Alternatives (0 =
> never expire; COIN pricing) are legitimate per-ecosystem choices —
> Founding Members should confirm or replace these suggested defaults.

#### Issuer policies

- [⟨PREFIX⟩-⟨SCH⟩-1] Before issuing a ⟨Schema Name⟩ credential, an issuer
  MUST verify ⟨the evidence checklist for this schema: which claims are
  checked against which sources, at which level of assurance⟩.
- [⟨PREFIX⟩-⟨SCH⟩-2] An issuer MUST retain the evidence of each issuance
  decision for ⟨retention period — suggested: the validity period of the
  issued credential⟩, off-chain, and MUST NOT place any of it on-chain.
- [⟨PREFIX⟩-⟨SCH⟩-3] An issuer MUST revoke a credential within ⟨days —
  suggested: 7⟩ days of learning that a ground listed in ⟨enumerated
  revocation grounds⟩ applies, and MUST notify the holder.

> *Instruction:* Anchor levels of assurance to established frameworks
> (eIDAS, NIST 800-63, ISO/IEC 29115) rather than inventing criteria; for
> organization-identity schemas, consider a negative evidence rule
> (documents found solely through links provided by the applicant are not
> acceptable). Every bespoke criterion you invent is one you must maintain
> forever.

#### Holder policies

⟨Obligations of holders, or "No stipulation."⟩

#### Verifier policies

⟨Obligations of verifiers — e.g. permitted purposes, data handling after
verification — or "No stipulation."⟩

## T7. Roles and Role Stacking

Suggested text:

This ecosystem uses the VPR participant roles with the meanings fixed by the
VPR specification:

| Role | In this ecosystem |
| --- | --- |
| ECOSYSTEM | The EGA's own root Participant entries (one per schema), anchoring each permission tree |
| ISSUER_GRANTOR | ⟨who they are, per schema — or "not used"⟩ |
| VERIFIER_GRANTOR | ⟨who they are, per schema — or "not used"⟩ |
| ISSUER | ⟨eligibility summary, detailed in section T8⟩ |
| VERIFIER | ⟨eligibility summary, or "open per schema configuration"⟩ |
| HOLDER | ⟨who holds credentials of this ecosystem⟩ |

- [⟨PREFIX⟩-ROLE-1] An organization acting in more than one role is bound by
  the terms of each role it acts in; obligations attach per role and per
  schema, and holding one role neither confers nor excuses another.
- [⟨PREFIX⟩-ROLE-2] A grantor that also acts as an issuer under the same
  schema MUST NOT validate its own applications; such applications MUST be
  routed to ⟨another grantor / the EGA⟩.

> *Instruction:* Do not import corporate-membership vocabulary here: on
> Verana, "member" belongs to associations, "Participant" to permission
> trees. If your ecosystem defines sub-bodies (committees, expert panels),
> give each a one-page charter: purpose, composition, enumerated
> responsibilities, and the statement that it recommends but does not bind
> the EGA unless this framework says otherwise.

## T8. Participant Lifecycle

> *Instruction:* This is the state machine every regulated role moves
> through. Keep the eight stage names — they are shared vocabulary across
> all Verana governance documents — and put a number in every ⟨bracket⟩.
> This template deliberately imposes **no entity-category qualification
> bars** as defaults: no legal-form lists, no minimum operating history, no
> revenue floors. Ecosystem creation and participation on Verana are open by
> design; add such bars only if your sector genuinely requires them, and if
> you do, pair them with a catch-all category with escalated evidence so no
> legitimate applicant is structurally excluded.

### T8.1 Qualification

- [⟨PREFIX⟩-LIFE-1] The EGA MUST publish objective eligibility criteria per
  role and per schema before accepting applications, ⟨optionally: as
  on-chain SchemaAuthorizationPolicy documents ([MOD-CS-MSG-5] /
  [MOD-CS-MSG-6]), url + digest_sri⟩.
- [⟨PREFIX⟩-LIFE-2] The validating party (the EGA or the responsible
  grantor) MUST evaluate applicants against the published criteria only, and
  MUST NOT refuse an applicant that meets them. An applicant that meets all
  published criteria is entitled to validation.
- [⟨PREFIX⟩-LIFE-3] The validating party MUST process applications in the
  order received and MUST decide within ⟨days — suggested: 30⟩ days of
  receiving a complete application; undecided applications escalate to
  ⟨the EGA's supreme decision-making organ⟩.

> **[DECISION]** The 30-day decision service level is a template suggestion
> (GLEIF runs 60-day review clocks; Hedera uses 14-day evaluation minimums).
> Sources fix the *existence* of decision deadlines, not the number.
> Founding Members should confirm the suggested default.

### T8.2 Application

- [⟨PREFIX⟩-LIFE-4] Applicants apply by starting an on-chain onboarding
  process (Start Participant OP, [MOD-PP-MSG-1]) with the designated
  onboarding validator for the role and schema, and by completing the
  DIDComm validation session defined in ⟨the ecosystem's onboarding
  procedure / operational annex⟩.
- [⟨PREFIX⟩-LIFE-5] Refusals MUST state written reasons against the
  published criteria. A refused applicant MAY re-apply at any time; no
  cooldown applies.

### T8.3 Activation

- [⟨PREFIX⟩-LIFE-6] Validation is effected on-chain by Set Participant OP to
  Validated ([MOD-PP-MSG-3]). An approval not activated within ⟨activation
  window — suggested: 180⟩ days of the approval decision expires and the
  application lapses.

### T8.4 Operation

- [⟨PREFIX⟩-LIFE-7] Participants MUST requalify every ⟨requalification
  period — suggested: the schema's validation validity period⟩ by renewing
  their onboarding process ([MOD-PP-MSG-2]) under the criteria in effect at
  renewal time.
- [⟨PREFIX⟩-LIFE-8] A participant operating services on which relying
  parties depend for revocation or permission-state information MUST keep
  that information available at least ⟨availability % — suggested: 99.0⟩ %
  measured monthly. Issuance capacity MAY degrade; revocation and
  permission-state availability MUST NOT.

### T8.5 Notification

- [⟨PREFIX⟩-LIFE-9] Participants MUST notify the EGA within ⟨days —
  suggested: 7⟩ days of: a change of control; loss or suspected compromise
  of keys material to their role; insolvency events; or any fact that makes
  their qualification evidence materially inaccurate.
- [⟨PREFIX⟩-LIFE-10] The EGA owes participants at least ⟨notice days —
  suggested: 30⟩ days' notice of material changes to this framework before
  their entry into force (see section T14), and the same notice of changes
  to published criteria affecting requalification.

### T8.6 Suspension

- [⟨PREFIX⟩-LIFE-11] Suspension follows the sanctions ladder of section T11.
  A suspension unresolved after ⟨auto-termination days — suggested: 180⟩
  days becomes termination automatically.

### T8.7 Termination

- [⟨PREFIX⟩-LIFE-12] On termination (voluntary or sanctioned), the leaving
  participant MUST: revoke its unexpired credentials or hand their
  administration to the EGA per the transition plan; notify affected holders
  and subordinate participants with a migration deadline of at least
  ⟨Grace Period days — suggested: 90⟩ days; archive its qualification and
  issuance evidence; and destroy role keys after the archive is secured. If
  the leaving participant defaults on notification, the EGA MUST take over
  notification and MAY hold the participant liable.

> **[DECISION]** The 90-day Grace Period default follows GLEIF's
> production-tested `gracePeriod ≥ 90 days` (disable-then-migrate: the
> terminated party is disabled immediately; downstream credentials keep
> verifying while holders migrate). Shorter periods punish innocent holders;
> longer ones prolong reliance on a terminated party. Founding Members
> should confirm the default.

### T8.8 Transition

- [⟨PREFIX⟩-LIFE-13] A participant MUST NOT transfer its portfolio of
  holders or subordinate participants to another participant on its own
  initiative; migrations follow the affected parties' own choices within
  the Grace Period, with the EGA as backstop.

## T9. Trust Assurance

*Section T9.1 is non-normative.*

### T9.1 The assurance ladder

This ecosystem's assurance mechanisms map to on-chain primitives as follows.
Each rung is adopted per schema and per role, based on the risk of the
credential concerned; higher rungs are added, not substituted.

| Rung | Mechanism | On-chain realization |
| --- | --- | --- |
| Financially backed pledge | Every participant's non-withdrawable trust deposit, growing with usage and slashable on violation | Trust deposit per Participant entry |
| Vetting | Evaluation of the applicant against published criteria in a live validation session | DIDComm onboarding validation ([MOD-PP-MSG-1]/[MOD-PP-MSG-3]) |
| Registration | The public, queryable record that a party holds a role under this framework | VALIDATED Participant entry with validity window |
| Certification | A revocable credential attesting accreditation against published criteria | IAC/VAC issued under an active SchemaAuthorizationPolicy |
| Discontinuance | Removal of a non-conforming party's status, visible to every relying party | Revocation [MOD-PP-MSG-9]; slash [MOD-PP-MSG-12]; repay [MOD-PP-MSG-13] |
| Referential trust | Recognition of this ecosystem by relying parties that choose to trust it | Whitelisting of the Ecosystem DID by Verifiable Services and User Agents |

> *Instruction:* Select rungs per schema; do not mandate expensive
> third-party audit where on-chain state already proves the fact. If your
> sector is regulated (health, finance), name the external audit or
> certification regime you require as an upper rung, anchored to existing
> standards (ISO 27001, SOC 2, eIDAS) — accept existing certifications as
> evidence rather than inventing a bespoke audit.

### T9.2 Risk derivation

> *Instruction:* Derive requirements from risks, not habits. For each schema,
> fill one row per material risk in the five-column pattern below (a
> SHOULD-level exercise before first activation — publish it as a
> non-normative annex). Honest residual-risk disclosure shares the residual
> risk with relying parties instead of hiding it.

| Objective | Risk | Requirement (ID) | Responsible role | Assurance mechanism |
| --- | --- | --- | --- | --- |
| ⟨…⟩ | ⟨…⟩ | ⟨[⟨PREFIX⟩-…]⟩ | ⟨…⟩ | ⟨on-chain / attested / assessed⟩ |

### T9.3 Assurance ceiling

- [⟨PREFIX⟩-TA-1] Conformance claims under this framework assert that
  published criteria were met at validation time and that on-chain state is
  as recorded; they MUST NOT be represented as guarantees of ongoing
  off-chain conduct.

## T10. Fees and Business Model

Suggested text:

Fees in this ecosystem are set per Participant entry in the schema's pricing
asset (section T6): `validation_fees` (paid by an applicant to its
onboarding validator per validation period), `issuance_fees` (paid to the
issuer per issuance), and `verification_fees` (paid to the permission holder
per verification). A share of fees paid (`trust_deposit_rate`, a network
parameter) accrues to trust deposits rather than being paid out; trust
deposits are non-withdrawable by design. Where the network's agent-reward
parameters apply, issuers and verifiers additionally pay the protocol-defined
user-agent and wallet-user-agent reward shares on pay-per operations.

| Role / schema | validation_fees | issuance_fees | verification_fees |
| --- | --- | --- | --- |
| ⟨role @ schema⟩ | ⟨amount or 0⟩ | ⟨amount or 0⟩ | ⟨amount or 0⟩ |

- [⟨PREFIX⟩-FEE-1] ⟨Either: "Participants set their own fees within the
  bounds published in this table" — or: "Fees are fixed as tabled above." If
  the ecosystem charges nothing, state: "This ecosystem charges no
  ecosystem-level fees; protocol fees and trust-deposit mechanics still
  apply."⟩
- [⟨PREFIX⟩-FEE-2] A fee-earning grantor or onboarding validator MUST
  evaluate applicants only against published criteria and MUST NOT use its
  position to disadvantage competitors (see [⟨PREFIX⟩-LIFE-2]).
- [⟨PREFIX⟩-FEE-3] Participants MUST NOT impose contractual lock-in or
  exclusivity preventing a holder or subordinate participant from switching
  to another issuer or grantor. Protocol-level switching costs (fresh
  onboarding fees, trust-deposit increments) exist and are disclosed here.
- [⟨PREFIX⟩-FEE-4] Participants MUST be sustainably financed for their role;
  the EGA MAY require evidence of sustainability at qualification and
  requalification.

> *Instruction:* State your ecosystem's business model honestly, including a
> zero-fee model if that is the choice. Amounts are Initial Parameters: put
> every number in Annex C of your EGF with its change process. Remember that
> slashed deposits are burned, not paid to victims — sanctions are
> deterrence, not compensation; do not describe them as insurance.

## T11. Sanctions and Appeals

### T11.1 Grounds

- [⟨PREFIX⟩-SANC-1] Sanctions MAY be imposed only for the enumerated
  grounds: ⟨list — e.g. breach of an identified requirement of this
  framework; material inaccuracy in qualification evidence; failure to
  revoke per [⟨PREFIX⟩-⟨SCH⟩-3]; failure of the notification duties in
  T8.5⟩. Subjective or reputational grounds, if any, require ⟨a qualified
  vote of disinterested decision-makers — e.g. two-thirds⟩, written reasons,
  and are appealable per T11.4.

### T11.2 The ladder

- [⟨PREFIX⟩-SANC-2] Sanctions proceed through the following rungs; a rung
  MAY be skipped only where written reasons establish that lesser measures
  cannot address the violation:

  1. **Warning** — written notice citing the exact requirement violated.
  2. **Remediation order** — a binding plan with a cure window of ⟨cure
     window days — suggested: 15⟩ days (⟨shorter cure days — suggested: 5⟩
     days for violations endangering relying parties) and day-counted
     milestones.
  3. **Permission restriction** — conditions on the participant's activity
     (e.g. no new issuances) pending remediation.
  4. **Suspension** — the participant is publicly designated suspended and
     MUST NOT perform the suspended role; unresolved suspension
     auto-terminates after ⟨auto-termination days — suggested: 180⟩ days
     per [⟨PREFIX⟩-LIFE-11].
  5. **Revocation** — the permission is revoked on-chain (Revoke
     Participant, [MOD-PP-MSG-9]), triggering the termination duties of
     T8.7.
  6. **Trust-deposit slash** — for grave or repeated violations, the
     ecosystem slashes the participant's trust deposit (Slash Participant
     Trust Deposit, [MOD-PP-MSG-12]). Slashed amounts are burned by the
     protocol — the EGA gains nothing from punishing. Re-participation
     requires repaying the slashed amount (Repay Participant Slashed Trust
     Deposit, [MOD-PP-MSG-13]) and fresh qualification.

- [⟨PREFIX⟩-SANC-3] Every sanction decision MUST be published with its
  grounds and reasons, and recorded symmetrically: suspension, lifting of
  suspension, termination, and reinstatement all appear on the public
  record. A reinstated participant's record MUST disclose the prior
  sanction.
- [⟨PREFIX⟩-SANC-4] Repetition of a violation within ⟨recidivism window —
  suggested: 12⟩ months of a closed sanction re-enters the ladder one rung
  higher.

### T11.3 Due process

- [⟨PREFIX⟩-SANC-5] Before any on-chain sanction act, the respondent MUST
  receive written notice of the alleged violation with the exact requirement
  IDs, the evidence, the proposed rung, and the cure window; and MUST have
  the opportunity to respond in writing.
- [⟨PREFIX⟩-SANC-6] Sanction decisions MUST be taken by decision-makers
  free of conflicts of interest in the matter; a conflicted decision-maker
  is excluded from the deliberation and the denominator.
- [⟨PREFIX⟩-SANC-7] A permission granted through a procedurally defective
  process is reviewable, not automatically void; the EGA MUST review it
  promptly and ratify, cure, or revoke it. Credentials issued in good faith
  under it before the review decision are not invalidated retroactively by
  the defect alone.

### T11.4 Appeal

- [⟨PREFIX⟩-SANC-8] A sanctioned party MAY appeal within ⟨appeal window
  days — suggested: 30⟩ days to ⟨an appeal body different from the body
  that imposed the sanction — e.g. a panel of disinterested participants,
  or the EGA's supreme decision-making organ⟩, which MUST decide with
  written reasons within ⟨days — suggested: 30⟩ days. An appeal undecided at
  that deadline ⟨consequence — suggested: escalates automatically to the
  EGA's supreme decision-making organ, and the sanction under appeal is
  stayed until that organ decides⟩. ⟨Final recourse:
  e.g. arbitration under ⟨rules⟩ seated in ⟨seat⟩, or the courts of
  ⟨jurisdiction⟩.⟩
- [⟨PREFIX⟩-SANC-9] Filing an appeal suspends execution of a trust-deposit
  slash (rung 6) until the appeal is decided, unless the EGA states written
  reasons why delay endangers relying parties. Rungs 1–5 remain effective
  pending appeal.

> *Instruction:* Never let the same body prosecute, decide, and hear the
> appeal. If your ecosystem is small, name an external appeal mechanism
> (arbitration) rather than pretending independence you cannot staff.
> Avoid your-home-forum clauses for disputes touching natural persons.

### T11.5 Revocation requests

- [⟨PREFIX⟩-SANC-10] Any party MAY submit a revocation request against a
  credential or permission of this ecosystem, stating one of the enumerated
  grounds of ⟨the applicable revocation grounds, e.g. per
  [⟨PREFIX⟩-⟨SCH⟩-3]⟩ together with supporting evidence. Before acting, the
  competent issuer or the EGA MUST verify the identity and standing of the
  requester and the stated ground, and MUST respond to the requester with a
  reasoned decision within ⟨days — suggested: 15⟩ days.

## T12. Privacy and Data Handling

- [⟨PREFIX⟩-PRIV-1] No participant may place personal data on-chain, and
  nothing in this framework requires it. On-chain entries are limited to
  registrations: DIDs, permissions, digests, fees, and timestamps.
- [⟨PREFIX⟩-PRIV-2] Qualification and issuance evidence containing personal
  data MUST be held off-chain by the party that collected it, protected per
  ⟨applicable data-protection law — e.g. GDPR⟩, retained no longer than
  ⟨retention period⟩, and disclosed only per this framework or law.
- [⟨PREFIX⟩-PRIV-3] For credentials whose subject is a natural person:
  consent to issuance MUST be recorded; withdrawal of consent is a mandatory
  revocation ground; and published derivatives of the credential MUST be
  deleted (not merely flagged) upon revocation for consent withdrawal.
- [⟨PREFIX⟩-PRIV-4] ⟨Data-protection roles: who is controller and processor
  for each processing operation this framework requires — or "No
  stipulation." if no personal data is processed.⟩

## T13. Public Claims and Trust Marks

- [⟨PREFIX⟩-CLAIM-1] A party MAY publicly claim participation, accreditation,
  or conformance under this framework if and only if its on-chain permission
  is VALIDATED, within its validity period, not revoked, and not slashed,
  and its Corporation is not subject to an unrepaid network-level
  trust-deposit slash (see Network GF [NGF-PART-9], which owns the
  network-level collapse rule). A slashed permission permanently loses
  claimable status; re-participation requires repayment and a new permission
  per rung 6 of [⟨PREFIX⟩-SANC-2]. All such claims MUST cease
  while any of those conditions fails.
- [⟨PREFIX⟩-CLAIM-2] No party is required to advertise participation; a
  party that chooses to MUST do so in the form prescribed here and MUST
  include ⟨its DID / a resolvable reference⟩ so relying parties can resolve
  live on-chain status. The on-chain permission state is the authoritative
  status signal; any badge or listing is derivative.
- [⟨PREFIX⟩-CLAIM-3] Discoverability: this framework is discoverable from
  the Ecosystem DID via the on-chain `GovernanceFrameworkDocument` entries.
  Authorization queries about this ecosystem's participants (per the ToIP
  Trust Registry Query Protocol supported by the VPR query API) resolve
  against live permission state: authorized means VALIDATED, within
  validity, not revoked, not slashed, and the Corporation not under an
  unrepaid network-level trust-deposit slash (Network GF [NGF-PART-9]).

## T14. Amendment and Versioning

- [⟨PREFIX⟩-AMND-1] This framework is amended by ⟨the EGA's amendment organ
  and decision rule — e.g. a two-thirds decision of ⟨organ⟩⟩. Amendments
  affecting participant obligations MUST be published for comment at least
  ⟨comment days — suggested: 30⟩ days before adoption.
- [⟨PREFIX⟩-AMND-2] An adopted amendment is published as a new
  `GovernanceFrameworkDocument` ([MOD-GF-MSG-1]) and enters into force only
  upon on-chain activation ([MOD-GF-MSG-2]). For material changes, the
  activation date MUST lie at least ⟨notice days — suggested: 30⟩ days
  after adoption. Active versions are immutable; corrections are new
  versions.
- [⟨PREFIX⟩-AMND-3] Versions are sequential integers starting at 1,
  assigned by on-chain activation order. The change log in section T1 lists
  one row per activated version.
- [⟨PREFIX⟩-AMND-4] Emergency amendments necessary to protect relying
  parties MAY shorten the notice periods, with written reasons published at
  activation and review at the next ordinary decision of ⟨organ⟩.

> **[DECISION]** The 30-day comment and notice defaults mirror the Network
> GF's own amendment runway so that ecosystem participants never face
> shorter notice from their ecosystem than from the network. Sources fix
> "notice with the amendment process" as mandatory EGF content but not the
> ecosystem-level number; Founding Members should confirm the mirrored
> default.

## T15. Recognized External Ecosystems

⟨List any external ecosystems, trust frameworks, or authorities this
ecosystem recognizes, with the scope and instrument of recognition — or:⟩

**No stipulation.**

> *Instruction:* Keep this section even if empty. Recognition is a peer,
> non-exclusive referral — it asserts no authority over the recognized
> ecosystem. If you later bridge to another trust framework (for example by
> accepting its credentials as qualification evidence), this is where the
> bridge is declared.

## Annex A. Network GF Interface Checklist

*This annex is non-normative for the ecosystem's participants; it is the
conformance-by-construction map required for the EGF author.*

> *Instruction:* Network GF chapter [NGF-EGF] enumerates the mandatory
> content of every EGF on the Verana network. The table below maps each
> mandatory-content item to the template section that satisfies it. Keep
> this annex in your published EGF (with the middle column pointing at your
> own section numbers): it lets any reader — and any tool — check
> conformance mechanically. If you restructured the template, update the
> mapping; if you deleted a row's section, you are non-conformant.

| Network GF chapter [NGF-EGF] item | Satisfied by | How |
| --- | --- | --- |
| Published on-chain as `GovernanceFrameworkVersion` / `GovernanceFrameworkDocument`, digest-anchored, with language | T1 + Annex B | Metadata block mirrors the on-chain fields; publication sequence anchors url + digest_sri per language |
| Document-control metadata block | T1 | Front-matter table with change log mapped 1:1 to version activations |
| Identified EGA with public contact | T4.1 | Identification table incl. legal name, contact, DIDComm endpoint |
| Legal jurisdiction stated | T4.1 | Jurisdiction and governing-law rows |
| Does not contradict the Network GF; layering clause | T2.3 + [TEGF-5]/[TEGF-6] | Supplement-not-supersede clause (retained in substance); tighten-never-loosen rule |
| Scope defined | T2.2 | Schemas, participants, EGA self-binding; explicit non-scope |
| Roles per schema defined | T6 + T7 | Per-schema configuration and role table on VPR role semantics |
| Onboarding requirements per role | T8 (+ T6 issuer policies) | Published objective criteria, application, activation, requalification |
| Sanctions and appeal defined | T11 | Graduated ladder pre-wired to [MOD-PP-MSG-9]/[-12]/[-13]; independent appeal |
| Fee schedule or its absence | T10 | Fee table incl. explicit zero-fee statement option |
| Privacy and data-handling commitments | T12 | Off-chain evidence rules, retention, consent triple |
| Amendment process with notice period | T14 | Comment window, notice runway, on-chain activation as entry into force |
| Issuer termination duties | T8.7 ([⟨PREFIX⟩-LIFE-12]) | Revoke unexpired credentials, notify holders with Grace Period, archive evidence, destroy keys |
| Verified revocation requests | T11.5 ([⟨PREFIX⟩-SANC-10]) | Enumerated grounds; requester identity and standing verified before acting; day-counted response deadline |
| Revocation-availability asymmetry | T8.4 ([⟨PREFIX⟩-LIFE-8]) | Issuance may degrade; revocation and permission-state availability may not |
| No personal data on-chain | T12 ([⟨PREFIX⟩-PRIV-1]) + [TEGF-14] | Registrations-only rule |
| Lawful-purpose / legal-safety clause | T2.5 + [TEGF-13] | No requirement to breach applicable law |
| No misrepresentation of Council endorsement | [TEGF-1] + T13 | Endorsement disclaimer; claims gated on live on-chain state |

## Annex B. Publication Instructions: The VPR Message Sequence

*This annex is non-normative. The VPR specification is authoritative for
every message named here.*

> *Instruction:* Execute in this order. Keep this annex in your EGF (it
> documents how your on-chain footprint was created), or move it to an
> operational runbook — your choice.

1. **Create New Corporation ([MOD-CO-MSG-1]).** Register your organization
   on the VPR: a Corporation entry with your DID and primary language,
   created atomically with the group and group policy account whose unique
   `policy_address` signs for you thereafter. The message requires the
   initial group members, a decision policy, and the public URL +
   `digest_sri` of your version-1 Corporation governance framework (CGF)
   document. Any account can submit this; no permission is needed.
2. **Create New Ecosystem ([MOD-ES-MSG-1]).** Create the Ecosystem entry
   under your Corporation: your Ecosystem DID, primary language, and the
   public URL + `digest_sri` of your completed EGF (this document) in that
   language. Version 1 of your governance framework is created **and
   activated atomically** by this message — there is no separate anchoring
   or activation step for version 1, and a version 1 can never be added or
   activated afterwards. Per [TEGF-4], do not execute this message while any
   Instruction block or unresolved ⟨field⟩ remains: the active version is
   immutable, and this is your EGF's legal moment of entry into force. This
   DID is what relying parties will resolve and whitelist.
3. **Later versions only — Add Governance Framework Document
   ([MOD-GF-MSG-1]) then Increase Active Governance Framework Version
   ([MOD-GF-MSG-2]).** For every version after the first: anchor, per
   language, a `GovernanceFrameworkDocument` (public URL + `digest_sri`)
   attached to a `GovernanceFrameworkVersion` greater than the active
   version — only future versions are editable — then activate it.
   Activation requires a document in the ecosystem's primary language, and
   per [TEGF-4] must not happen while Instruction blocks or unresolved
   ⟨fields⟩ remain. Active versions are immutable; corrections are new
   versions.
4. **Create New Credential Schema ([MOD-CS-MSG-1]).** One message per schema
   in section T6, submitting exactly the configuration values tabled there
   (JSON schema, onboarding modes, validity periods, pricing asset, digest
   algorithm). The on-chain schema identifiers assigned here MAY be pinned
   into a subsequent framework version.
5. **Create Root Participant ([MOD-PP-MSG-7]).** Create the ECOSYSTEM root
   Participant entry that anchors each schema's permission tree; all
   grantor, issuer, and verifier permissions descend from it through
   onboarding processes.
6. **Optional — Create / Activate Schema Authorization Policy
   ([MOD-CS-MSG-5] / [MOD-CS-MSG-6]).** Publish your objective accreditation
   criteria per (schema, role) as versioned on-chain policy documents
   (url + digest_sri) and activate them. While a policy is active, the
   granting corporation must issue an Issuer Authorization Credential (IAC)
   or Verifier Authorization Credential (VAC) to each successfully onboarded
   candidate.

## Annex C. Parameter Collection Sheet (Initial Parameters)

> *Instruction:* Every number you chose above must appear here, per
> [TEGF-10], with its change process. This becomes your EGF's Initial
> Parameters annex; parameters change only through the amendment process of
> section T14 unless a lighter process is stated per row. Suggested defaults
> shown are template recommendations, not requirements.

| Parameter | Where set | Initial value | Change process |
| --- | --- | --- | --- |
| Validation validity periods (per role, per schema) | T6 | ⟨days — suggested: 365⟩ | ⟨T14⟩ |
| Pricing asset (per schema) | T6 | ⟨TU / COIN / FIAT — suggested: TU⟩ | ⟨T14⟩ |
| Credential revocation deadline | T6 issuer policies | ⟨days — suggested: 7⟩ | ⟨T14⟩ |
| Evidence retention period | T6 / T12 | ⟨suggested: validity period⟩ | ⟨T14⟩ |
| EGA metadata correction deadline | T4.1 | ⟨days — suggested: 30⟩ | ⟨T14⟩ |
| Ecosystem DID migration notice | T4.2 | ⟨days — suggested: 30⟩ | ⟨T14⟩ |
| Application decision service level | T8.1 | ⟨days — suggested: 30⟩ | ⟨T14⟩ |
| Activation window (approval expiry) | T8.3 | ⟨days — suggested: 180⟩ | ⟨T14⟩ |
| Requalification period | T8.4 | ⟨suggested: validity period⟩ | ⟨T14⟩ |
| Availability floor (revocation / permission state) | T8.4 | ⟨% — suggested: 99.0⟩ | ⟨T14⟩ |
| Participant notification deadline | T8.5 | ⟨days — suggested: 7⟩ | ⟨T14⟩ |
| EGA notice of material changes | T8.5 / T14 | ⟨days — suggested: 30⟩ | ⟨T14⟩ |
| Auto-termination of unresolved suspension | T8.6 / T11 | ⟨days — suggested: 180⟩ | ⟨T14⟩ |
| Grace Period after involuntary revocation | T8.7 | ⟨days — suggested: 90⟩ | ⟨T14⟩ |
| Cure windows (standard / endangering) | T11.2 (rung 2) | ⟨days — suggested: 15 / 5⟩ | ⟨T14⟩ |
| Recidivism window | T11.2 | ⟨months — suggested: 12⟩ | ⟨T14⟩ |
| Appeal window / appeal decision deadline | T11.4 | ⟨days — suggested: 30 / 30⟩ | ⟨T14⟩ |
| Revocation-request response deadline | T11.5 | ⟨days — suggested: 15⟩ | ⟨T14⟩ |
| Amendment comment window | T14 | ⟨days — suggested: 30⟩ | ⟨T14⟩ |
| Amendment notice before activation (material) | T14 | ⟨days — suggested: 30⟩ | ⟨T14⟩ |
| Fee amounts (per role, per schema) | T10 | ⟨amounts or 0⟩ | ⟨T14 or lighter fee-schedule process⟩ |

## Annex D. Design Questions, Pre-Answered

*This annex is non-normative.*

> *Instruction:* A completeness self-check before publication. Every
> question below must be answerable from your finished EGF; the right-hand
> column shows where the template answers it with a VPR-native default.
> Delete this annex, or keep it as a reader's map — your choice.

| Question | Template answer |
| --- | --- |
| Who governs, and who governs the governor? | T4.1 identification; T4.3 accountability allocation; T2.3 Network GF as the floor |
| How does a party join? | T8.1–T8.3: published objective criteria → onboarding process [MOD-PP-MSG-1] → validation [MOD-PP-MSG-3] |
| How does a party leave, voluntarily or not? | T8.6–T8.8 and T11: suspension, termination, Grace Period, portfolio non-transfer |
| How are rules enforced? | T11 ladder pre-wired to [MOD-PP-MSG-9]/[-12]/[-13]; deposits as the financial backstop |
| Who pays whom, for what? | T10 fee table on `validation_fees` / `issuance_fees` / `verification_fees`; trust-deposit mechanics |
| What incentive does anyone have to behave? | Non-withdrawable deposits (burned on slash), requalification, public symmetric record, referential trust |
| How do relying parties check status? | T13: claims as a pure function of live on-chain permission state; TRQP-compatible queries |
| How do the rules change? | T14: comment window, notice runway, on-chain activation as entry into force |
| What happens if the EGA disappears? | T4.2 DID lifecycle and abandonment; [⟨PREFIX⟩-EGA-4] vacancy fallback |

## Version History

| Version | Date | Status | Summary |
| --- | --- | --- | --- |
| 0.1 | 2026-07-05 | Draft | First draft for co-authoring by Founding Members |
