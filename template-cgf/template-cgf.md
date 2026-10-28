# Template Corporation Governance Framework (Template CGF)

| Field | Value |
| --- | --- |
| Document Name | Template Corporation Governance Framework (Template CGF) |
| Version | DRAFT 0.1 |
| Status | Draft for co-authoring by Founding Members |
| Governs | Nothing by itself — a voluntary scaffold; the `[TCGF-n]` requirements of section 5 bind only corporations that derive their CGF from this template or represent their CGF as conformant with this template |
| Governed By | The Verana Council Association (in formation), acting through the mechanisms of Network GF chapter [NGF-GOV] |
| Approved By | Pending — Incorporation General Assembly, target Q4 2026 |
| Approval Date | Pending |
| License | CC-BY-SA 4.0 |
| Anchoring | Git history and public URL in `verana-labs/verana-council-gov` now; on-chain `GovernanceFrameworkDocument` (`url` + `digest_sri`) once the network is live |

> **Status: DRAFT 0.1.** This is a first draft prepared for co-authoring by
> the Founding Members of the Verana Council Association, for ratification at
> the Q4 2026 Incorporation General Assembly. Where this document states
> protocol facts, the [Verifiable Trust specification](https://verana-labs.github.io/verifiable-trust-spec/)
> and the [Verifiable Public Registry (VPR) specification](https://verana-labs.github.io/verifiable-trust-vpr-spec/)
> (version 5, draft) prevail. Where it states entity facts, the Council's
> definitions record and public record prevail. During the pre-incorporation
> period, 2060 OÜ acts as transitional steward of the Council; every steward
> power carries an event-triggered sunset (see Network GF chapter [NGF-TRAN]).

## 1. Welcome: Registering a Corporation on Verana

*This section is non-normative.*

Every organization that acts on the Verana network does so through a
**Corporation** entry on the Verifiable Public Registry (VPR). The
Corporation is the registry's actor: it is anchored by a `policy_address`
account that signs on its behalf, it controls zero or more Ecosystems, it
owns zero or more Participant entries in its own or third-party ecosystems,
it delegates day-to-day signing to operator accounts, and it holds the trust
deposit that backs everything it does.

Creating a Corporation is permissionless: any account can do it, no
application to the Verana Council is required, and no fee is payable to the
Council. But the protocol asks one thing of every corporation at the moment
of creation: the public URL and digest of **version 1 of its Corporation
Governance Framework (CGF)**. Create New Corporation ([MOD-CO-MSG-1]) has no
optional variant — a Corporation without a CGF cannot exist, and version 1 is
anchored and activated atomically with the entry.

The CGF answers a different question from an Ecosystem Governance Framework
(EGF). An EGF says how an *ecosystem* is run: its schemas, its roles, who may
issue and verify. A CGF says who the *organization behind a Corporation
entry* is, how it decides, who is allowed to sign for it, how it protects
its keys, and what happens when it changes or disappears. Every ecosystem
governance authority, every issuer, every verifier, every grantor on Verana
has one. Most of them will be short.

This template exists to make that easy. It is a fill-in-the-blanks scaffold
for writing a CGF that:

- mirrors the VPR's on-chain Corporation mechanics out of the box (the
  group and its decision policy, operator authorizations and fee grants, DID
  rotation, trust-deposit accounting, governance-framework anchoring);
- satisfies, by construction, the few duties the Verana Network Governance
  Framework (Network GF) places on every corporation (chapter 6, section 6.2,
  [NGF-PART-3] to [NGF-PART-5]); and
- gives relying parties, ecosystem governance authorities, and onboarding
  validators one predictable place to read who they are dealing with.

Three things this template is **not**:

- **It is not a gate.** Using this template is voluntary. You may write your
  CGF from scratch, so long as it respects the Network GF.
- **It is not an endorsement.** Using this template does not imply any
  endorsement, accreditation, certification, or recognition of your
  organization by the Verana Council. Registering a Corporation is not the
  same as being trusted; trust on Verana is earned inside ecosystems, through
  onboarding processes and the choices of relying parties.
- **It is not an EGF.** If your Corporation controls an Ecosystem, that
  ecosystem's rules belong in its EGF, authored from the Template EGF. The
  CGF only points to them (section T7).

The Council practices what it publishes: the Council's own Corporation entry
anchors the **Network Governance Framework** itself as its version-1 CGF
document (Network GF [NGF-TRAN-6]), and the Network GF chapter [NGF-GOV]
is the worked example of a corporation stating how it decides and who may
act for it.

### 1.1 Short form

Most corporations on Verana control no ecosystem: they are issuers,
verifiers, grantors, or holders in ecosystems run by others. For them, this
template reduces to a **short form**: complete sections T1, T2, T4, T5, T6,
T9, T11, and T13 in full, and answer every other section with
"**No stipulation.**" or a one-line pointer. A short-form CGF fits on two
pages. Section 2.3 explains why the empty sections are kept.

## 2. How to Use This Template

*This section is non-normative, except where it restates requirements defined
in section 5.*

### 2.1 The three-mode convention

Everything from section T1 onward is template material, written in three
modes:

1. **Suggested text** (plain text). Default wording you can keep as-is or
   edit. It is written so that a corporation produces a valid CGF by
   *editing*, not authoring from a blank page.
2. **⟨Angle-bracket fields⟩**. Mandatory fill-ins. Every ⟨field⟩ must be
   replaced with your organization's own value before publication. Where a
   sensible default exists, it is shown as ⟨field — suggested: value⟩.
3. **Instruction blocks**, rendered as blockquotes beginning with
   "*Instruction:*". Authoring guidance addressed to you, the CGF author.
   Every Instruction block must be deleted before publication — it is
   scaffolding, not framework text.

### 2.2 The completion rule

Because published CGFs are anchored on-chain by digest, completion is
machine-checkable: a finished CGF contains no "*Instruction:*" blocks and no
unresolved "⟨" / "⟩" fill-in markers. Requirement [TCGF-4] in section 5 makes
this the anchoring rule — a CGF derived from this template must not be
anchored at Corporation creation or activated on-chain while any of either
remains. A simple text search over the digest-anchored document verifies
compliance.

Version 1 deserves special care: it is created **and activated** by Create
New Corporation ([MOD-CO-MSG-1]) in the same transaction, and no version 1 can
ever be added or re-activated afterwards. Publish the finished version-1
document at a stable public URL, compute its digest, and only then execute
the creation message.

### 2.3 Silence is never ambiguous

Where a section genuinely does not apply to your organization, write
"**No stipulation.**" rather than deleting the section. A deliberately empty
slot tells readers you considered the topic and decided it needs no rule; a
missing section tells them nothing. Short-form CGFs (section 1.1) rely on
this convention heavily.

### 2.4 Where to get help

- The **Network GF** chapter [NGF-GOV] shows a corporation describing its own
  decision rules, denominators, committees, vacancy fallback, and
  anti-capture measures; chapter 6, section 6.2 states the duties
  every corporation owes the network.
- The **Template EGF** is the companion scaffold for the ecosystems your
  Corporation controls; its sections T4 (ecosystem governance authority) and
  T14 (amendment) use the same patterns as sections T4 and T13 below.
- The **VT and VPR specifications** define every protocol object this
  template references: `Corporation`, `OperatorAuthorization`,
  `VSOperatorAuthorization`, `FeeGrant`, `TrustDeposit`,
  `GovernanceFrameworkVersion`, `GovernanceFrameworkDocument`. This template
  never restates the specs; where it summarizes them, the specs prevail.

## 3. Conformance

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in [BCP 14](https://www.rfc-editor.org/info/bcp14)
[RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174)
when, and only when, they appear in all capitals, as shown here.

Normativity in this document has two distinct scopes:

- The `[TCGF-n]` requirements in section 5 are normative **for users of this
  template**: a corporation claiming to have derived its CGF from this
  template is bound by them.
- The suggested text in sections T1–T13 is **not normative as written
  here**. It becomes normative only inside the CGF a corporation publishes,
  where it binds that corporation, its group members, and its operators
  under that corporation's own authority.

Sections marked "*This section is non-normative.*" contain no requirements in
either scope.

## 4. Terminology

Terms defined in the [Verifiable Trust specification](https://verana-labs.github.io/verifiable-trust-spec/)
and the [VPR specification](https://verana-labs.github.io/verifiable-trust-vpr-spec/)
are used with the meanings given there and are not redefined here. This
includes: Corporation, Ecosystem, CredentialSchema, Participant, corporation
governance framework (CGF), ecosystem governance framework (EGF), operator,
VS operator, fee grant, trust deposit, trust unit, Verifiable Service,
Verifiable User Agent, and the participant roles ECOSYSTEM, ISSUER_GRANTOR,
VERIFIER_GRANTOR, ISSUER, VERIFIER, HOLDER.

The following local terms are used in this document. Definitions contain no
normative keywords.

- **Corporation entry**: the on-chain `Corporation` record (its `id`, `did`,
  `policy_address`, `language`, `active_version`), as distinct from the legal
  entity that controls it.
- **Registered organization**: the legal or organizational entity that
  controls a Corporation entry and is accountable for its CGF. The
  corporation-level counterpart of the Template EGF's "ecosystem governance
  authority".
- **Group**: the Cosmos SDK `x/group` group created atomically with the
  Corporation entry by [MOD-CO-MSG-1]; its group policy account is the
  Corporation's `policy_address`. Group membership, proposals, and votes are
  managed through `x/group` directly, not through VPR messages.
- **Group member**: an account listed in the group with a voting weight.
  Distinct from a *Member* of the Verana Council Association and from a
  *Participant* in an ecosystem; this template never uses "member" alone.
- **Decision policy**: the `x/group` rule (threshold or percentage, with its
  voting period and minimum execution period) under which the group adopts
  proposals that the `policy_address` then executes.
- **Operator**: an account holding an `OperatorAuthorization` from the
  Corporation to sign enumerated VPR message types on its behalf, optionally
  with spend limits, a period, an expiration, and a fee grant.
- **VS operator**: a Verifiable Service agent account holding a
  `VSOperatorAuthorization` from the Corporation, scoped to specific
  Participant entries. Operator and VS operator authorizations are mutually
  exclusive for a given grantee.
- **Network GF**: the Verana Network Governance Framework, the constitutional
  layer that every governance framework on the Verana network supplements
  and must not contradict.
- **Instruction block**: a blockquote beginning with "*Instruction:*",
  addressed to the CGF author and deleted before publication.
- **Fill-in field**: a mandatory placeholder written between ⟨angle
  brackets⟩.
- **Suggested text**: template prose a corporation may keep or edit.
- **Controlled Document**: a separately versioned document referenced from a
  CGF, revisable through the CGF's stated amendment process.

## 5. Template Requirements

This section is normative for any corporation that derives its CGF from this
template or represents its CGF as conformant with this template.

- **[TCGF-1]** A corporation MUST NOT represent its use of this template, or
  the existence of its Corporation entry on the Verana network, as an
  endorsement, accreditation, certification, or approval by the Verana
  Council.
- **[TCGF-2]** Before publication, the CGF author MUST replace every fill-in
  field with the organization's own value.
- **[TCGF-3]** Before publication, the CGF author MUST delete every
  Instruction block.
- **[TCGF-4]** A CGF derived from this template MUST NOT be anchored as
  version 1 at Corporation creation (Create New Corporation, [MOD-CO-MSG-1])
  or activated on-chain (Increase Active Governance Framework Version,
  [MOD-GF-MSG-2] without `ecosystem_id`) while any Instruction block or
  unresolved fill-in field remains in any of its `GovernanceFrameworkDocument`
  entries. Version 1 activates atomically at Corporation creation, so it MUST
  be complete before [MOD-CO-MSG-1] is executed.
- **[TCGF-5]** The CGF MUST retain a layering clause equivalent in substance
  to section T2.3: a statement that the CGF supplements and does not
  supersede the Verana Network Governance Framework, that on conflict the
  Network GF controls, and that for acts within an ecosystem the EGF of that
  ecosystem controls over the CGF.
- **[TCGF-6]** The CGF MUST NOT loosen any requirement the Network GF places
  on corporations, and MUST NOT purport to govern any ecosystem, any other
  corporation, or any participant other than the corporation's own group
  members and operators. Ecosystem rules belong in an EGF.
- **[TCGF-7]** Where a template section does not apply, the CGF MUST state
  "No stipulation." rather than omit the section, so that silence is
  distinguishable from oversight.
- **[TCGF-8]** Every published `GovernanceFrameworkDocument` URL MUST be
  publicly resolvable without authentication, registration, or payment; the
  on-chain `digest_sri` is the canonical identity of each document version,
  and web copies that do not match it have no effect ([NGF-PART-4]).
- **[TCGF-9]** The CGF MUST state the decision policy of the Corporation's
  group (section T5) consistently with the group's on-chain configuration,
  and the corporation MUST publish a new CGF version within the deadline of
  section T5 whenever the on-chain decision policy changes.
- **[TCGF-10]** Every quantified threshold in the CGF MUST be stated as a
  number (not an adjective) and MUST be listed in the CGF's Initial
  Parameters annex together with its change process.
- **[TCGF-11]** Every uniquely addressable requirement in the CGF SHOULD
  carry a stable bracketed identifier with the corporation's own prefix,
  carry exactly one RFC 2119 keyword, and be addressed to a named role.
  Identifiers, once assigned, MUST NOT be reused or renumbered.
- **[TCGF-12]** A CGF derived from this template is an adaptation of a
  CC-BY-SA 4.0 work: it MUST be licensed under CC-BY-SA 4.0 (or a compatible
  license per the CC-BY-SA 4.0 terms) and MUST attribute the Verana Council
  Association as the author of the template.
- **[TCGF-13]** The CGF MUST NOT require any conduct that would cause the
  corporation, a group member, or an operator to breach law applicable to
  them, and MUST state this (the legal-safety clause of section T2.5).
- **[TCGF-14]** The CGF MUST NOT place personal data on-chain, MUST NOT
  require any party to do so ([NGF-PART-5]), and SHOULD identify natural
  persons in the document itself only by function unless applicable law
  requires a name or the person has consented to publication.

> **[DECISION]** The Network GF today binds corporations through three rules
> only ([NGF-PART-3] accurate registration and DID control, [NGF-PART-4]
> resolvable CGF documents consistent with on-chain digests, [NGF-PART-5]
> lawful purpose and no personal data). It has no mandatory-contents chapter
> for CGFs comparable to chapter [NGF-EGF] for EGFs, and [NGF-POW-2] lists
> the Network GF, the ECS-EGF, and the Template EGF as the Council's
> maintained documents but not this template. Founding Members should decide
> whether (a) to keep the CGF floor minimal and leave this template purely
> voluntary, or (b) to add a short chapter to the Network GF making an
> identified registered organization, a stated decision policy, an operator
> disclosure rule, and a contact channel mandatory CGF contents, and to add
> this template to [NGF-POW-2]. This draft assumes (a) and is written so that
> (b) can be adopted later without changing the template's sections.

> *Instruction blocks begin from here. Everything from section T1 onward is
> template material: keep or edit the plain text, resolve every ⟨field⟩, and
> delete every Instruction block — including this one — before publication.*

## T1. Document Metadata and Status

> *Instruction:* This block becomes the front matter of your CGF. The table
> mirrors the on-chain fields of your Corporation entry and its
> `GovernanceFrameworkVersion` / `GovernanceFrameworkDocument` entries, so a
> reader can verify the document against the chain and vice versa. Rows
> marked "once created" cannot be known before [MOD-CO-MSG-1] executes:
> leave them as "assigned at creation" in version 1 and pin them in version
> 2, or publish them on the stable URL's landing page. Choose a short stable
> requirement-ID prefix for your organization (2–5 uppercase letters); it is
> used in every requirement identifier below. The Corporation `language` is
> immutable after creation and must match the language of the version-1
> document.

| Field | Value |
| --- | --- |
| Document Name | ⟨Organization Name⟩ Corporation Governance Framework |
| Version | ⟨integer, starting at 1⟩ |
| Status | ⟨Draft / Active⟩ |
| Governs | The Corporation entry of ⟨Organization Name⟩ on the Verana network: its group, its operators, and its conduct as a corporation |
| Governed By | ⟨Legal name of the registered organization⟩ |
| Requirement-ID prefix | ⟨PREFIX⟩ |
| Corporation DID | ⟨did:…⟩ |
| Corporation `id` | ⟨uint64 — assigned at creation⟩ |
| Corporation `policy_address` | ⟨group policy account address — assigned at creation⟩ |
| Primary language | ⟨IETF language tag, e.g. "en" — immutable after creation⟩ |
| On-chain CGF version | ⟨GovernanceFrameworkVersion number⟩ |
| Active since | ⟨active_since timestamp, once activated⟩ |
| Document URL | ⟨publicly resolvable URL, no authentication⟩ |
| Document digest | ⟨digest_sri as anchored on-chain⟩ |
| License | ⟨CC-BY-SA 4.0⟩ |
| Contact | ⟨email or DIDComm endpoint of the registered organization⟩ |

> *Instruction:* Keep a change-log table under this metadata block. Its rows
> MUST correspond one-to-one with on-chain `GovernanceFrameworkVersion`
> activations of your Corporation entry: one row per activated version, with
> date and a one-line description. Active on-chain versions are immutable;
> corrections always mean a new version.

| Version | Date | Description |
| --- | --- | --- |
| 1 | ⟨date⟩ | Initial version, anchored at Corporation creation |

## T2. Introduction, Scope and Purpose

### T2.1 Purpose

*This section is non-normative.*

⟨Organization Name⟩ maintains a Corporation entry on the Verana network in
order to ⟨one paragraph: what the organization does on Verana — e.g. govern
the ⟨X⟩ ecosystem; issue ⟨Y⟩ credentials as an accredited issuer in the ⟨Z⟩
ecosystem; operate Verifiable Services for its customers⟩. This framework
states who the organization is, how it decides, who may sign on its behalf,
and how it handles its keys, deposits, and obligations on the network.

> *Instruction:* Keep the purpose to one paragraph. Do not describe ecosystem
> rules, credential schemas, or participant criteria here — those belong in
> the EGF of the ecosystem concerned. If the organization controls
> ecosystems, name them and point to section T7.

### T2.2 Scope

This framework governs:

- the registered organization's conduct as the controller of the
  Corporation entry identified in section T1;
- the members of the Corporation's group and the operators and VS operators
  authorized by it, in that capacity; and
- the registered organization's handling of the DID, keys, trust deposit,
  and governance documents attached to the Corporation entry.

This framework does not govern the Verana network, any ecosystem (including
ecosystems this Corporation controls, which are governed by their own EGFs),
any other corporation, or the holders of credentials this organization
issues.

### T2.3 Layering

This framework supplements and does not supersede the Verana Network
Governance Framework; on conflict the Network GF controls. For any act of
this Corporation within an ecosystem — as ecosystem governance authority,
grantor, issuer, verifier, or holder — the Ecosystem Governance Framework of
that ecosystem controls over this framework.

Within this organization's own document stack, precedence is: the Network
GF, then the applicable EGF for acts within its ecosystem, then this
framework, then its Controlled Documents. A lower document tightens but
never loosens a higher one.

> *Instruction:* The first paragraph of T2.3 is mandatory boilerplate
> ([TCGF-5]) — retain its substance, adapting the wording if needed. The
> EGF-over-CGF rule matters: a corporation cannot use its own CGF to
> contract out of the rules of an ecosystem it joined.

### T2.4 Acceptance

The registered organization is bound by this framework as its author. Each
operator it authorizes accepts the version of this framework in force
before its first use of the authorization, through Accept Corporation
Governance Framework ([MOD-GF-MSG-4]), and each later version within the
grace period set at activation ([⟨PREFIX⟩-OPS-5], [⟨PREFIX⟩-AMND-5]); an
authorization whose holder has not accepted is unusable (VPR [GF-CHECK-2]).
Group members act through the group's decision policy and accept nothing
on-chain; the registered organization binds them ⟨by its internal rules /
by their mandate⟩. The registered organization accepted the Network GF
version in force when it created its Corporation entry (`ngf_version`,
[MOD-CO-MSG-1]) and accepts each later version, and the EGF of every
ecosystem it participates in before its first act there, through Accept
Governance Framework Version ([MOD-GF-MSG-3]), as those frameworks provide.

### T2.5 Legal safety

Nothing in this framework requires any party to act in breach of law
applicable to it. Where compliance with this framework would breach
applicable law, the party MUST notify ⟨the organization's accountable organ,
e.g. its board⟩ and the parties MUST seek a conforming alternative.

## T3. Conformance and Terminology

Suggested text:

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
"OPTIONAL" in this document are to be interpreted as described in BCP 14
(RFC 2119, RFC 8174) when, and only when, they appear in all capitals.

Terms defined in the Verifiable Trust and VPR specifications and in the
Verana Network Governance Framework are used with the meanings given there.
The following local terms apply:

⟨Local terms, or: **No stipulation.**⟩

> *Instruction:* Define only terms local to your organization (internal organ
> names, product names used in section T6 or T7). Never redefine a VPR or
> Network GF term.

## T4. The Registered Organization

### T4.1 Identification

The registered organization controlling the Corporation entry identified in
section T1 is:

| Field | Value |
| --- | --- |
| Legal name | ⟨legal name⟩ |
| Legal form and registry | ⟨e.g. GmbH, registered at …, registration number …⟩ |
| Legal jurisdiction | ⟨country / state of incorporation⟩ |
| Governing law of this framework | ⟨governing law⟩ |
| Registered address | ⟨address⟩ |
| Public contact | ⟨email⟩ |
| DIDComm contact | ⟨DID with DIDComm service endpoint, or "none"⟩ |
| Website | ⟨URL⟩ |
| Accountable organ | ⟨the organ that answers for this framework, e.g. the board of directors⟩ |

- [⟨PREFIX⟩-ORG-1] The registered organization MUST keep the identification
  table above accurate and MUST publish a corrected framework version within
  ⟨days — suggested: 30⟩ days of any change to it ([NGF-PART-3]).
- [⟨PREFIX⟩-ORG-2] The registered organization MUST disclose, in this
  section, any change of control affecting it within ⟨days — suggested: 30⟩
  days of the change becoming effective, and MUST notify the ecosystem
  governance authority of every ecosystem in which it holds a Participant
  entry, where that ecosystem's EGF so requires.
- [⟨PREFIX⟩-ORG-3] The registered organization MUST be a single legal or
  organizational entity. Where several affiliated entities act on Verana,
  each MUST control its own Corporation entry with its own CGF, and this
  section MUST name the affiliation.

> *Instruction:* [⟨PREFIX⟩-ORG-3] follows from the VPR's one-DID-one-Corporation
> and DID-ownership invariants: a Corporation entry is the unit of
> accountability, and relying parties must be able to map it to exactly one
> accountable legal entity. Unincorporated groups (an open-source project, a
> consortium without legal personality) may register a Corporation; state
> the organizational form honestly and name the natural or legal person who
> answers for it.

### T4.2 Corporation DID lifecycle

- [⟨PREFIX⟩-ORG-4] The registered organization MUST control the Corporation
  DID stated in section T1 and MUST keep its DID document resolvable
  ([NGF-PART-3]).
- [⟨PREFIX⟩-ORG-5] The registered organization MUST publish, at ⟨list of at
  least two independent publication points, e.g. this document and the
  organization's website⟩, the Corporation DID and any planned rotation of
  it (Update Corporation, [MOD-CO-MSG-2]), with at least ⟨days — suggested:
  30⟩ days' notice before the rotation takes effect, except in the key
  compromise case of section T9.
- [⟨PREFIX⟩-ORG-6] A DID rotation MUST be recorded in the next version of
  this framework, with the old and new DID and the block height or date of
  the rotation.

> *Instruction:* The Corporation DID is what ecosystems resolve when they
> validate you and what indexers display next to every Participant entry you
> own. The VPR forbids a DID from being claimed by two corporations, or by an
> Ecosystem or Participant entry owned by another corporation; rotating to a
> DID you do not control will abort. Say now what happens at genesis, on
> rotation, and on compromise (section T9).

### T4.3 What the registered organization answers for

*This section is non-normative.*

The registered organization answers for every message signed by its
`policy_address`, whether executed through a group proposal or by an
authorized operator, and for keeping this framework accurate. It does not
answer for the rules of ecosystems it does not control, nor for the conduct
of other participants in ecosystems it does control (the EGF of that
ecosystem allocates that accountability). A Corporation entry records that an
organization exists on the network and how it is governed; it is not a
statement of trustworthiness.

## T5. Decision-Making: The Group and Its Decision Policy

> *Instruction:* This section is the heart of a CGF. The Corporation entry
> is governed exclusively through its `x/group` group policy: the group
> members vote on proposals under the decision policy, and the
> `policy_address` executes what passes. The account that submitted Create
> New Corporation holds no privilege afterwards. Mirror the on-chain
> configuration here so that a reader can check it against the chain
> (`GroupsByMember`, `GroupPolicyInfo`), and say which off-chain decision
> authorizes a group member to vote YES.

### T5.1 Group composition

The Corporation's group has the following members at the active version of
this framework:

| Group member (function) | Account | Weight |
| --- | --- | --- |
| ⟨function, e.g. "Chief Executive Officer" or "Treasury key A"⟩ | ⟨account address⟩ | ⟨weight⟩ |
| ⟨function⟩ | ⟨account address⟩ | ⟨weight⟩ |
| ⟨function⟩ | ⟨account address⟩ | ⟨weight⟩ |

Total weight: ⟨sum⟩.

> *Instruction:* Identify group members by function, not by personal name,
> unless law requires or the person consents ([TCGF-14]). Account addresses
> are already public on-chain. A single-member group (weight 1, threshold
> 1) is valid and common for small organizations; say so plainly rather
> than inventing committees. Groups of 3 or more with a threshold above
> half are RECOMMENDED for any corporation that controls an ecosystem or
> holds grantor roles.

### T5.2 Decision policy

| Field | Value |
| --- | --- |
| Policy type | ⟨ThresholdDecisionPolicy / PercentageDecisionPolicy⟩ |
| Threshold or percentage | ⟨e.g. weight 2 of 3 / 67%⟩ |
| Voting period | ⟨duration, e.g. 72h⟩ |
| Minimum execution period | ⟨duration, e.g. 0s⟩ |

- [⟨PREFIX⟩-GOV-1] The tables of sections T5.1 and T5.2 MUST reflect the
  group's on-chain configuration. Whenever group membership, weights, or the
  decision policy change on-chain, the registered organization MUST publish
  a new version of this framework within ⟨days — suggested: 30⟩ days
  ([TCGF-9]).
- [⟨PREFIX⟩-GOV-2] A group member MUST vote on a group proposal only as
  authorized by ⟨the off-chain decision that authorizes it, e.g. "a
  resolution of the board of directors" or "the organization's signature
  policy"⟩. A vote cast without that authorization binds the Corporation
  on-chain but is a breach of this framework by the group member.
- [⟨PREFIX⟩-GOV-3] The following acts MUST be decided by group proposal and
  MUST NOT be delegated to an operator: changes to group membership or the
  decision policy; Grant and Revoke Operator Authorization ([MOD-DE-MSG-3],
  [MOD-DE-MSG-4]) except as section T6 allows; Update Corporation DID
  ([MOD-CO-MSG-2]); activation of a new version of this framework
  ([MOD-GF-MSG-2]); ⟨further reserved acts, e.g. creation or archiving of
  an Ecosystem, repayment of a slashed deposit⟩.
- [⟨PREFIX⟩-GOV-4] If ⟨the accountable organ⟩ is vacant or unable to act,
  its duties under this framework revert to ⟨the organization's supreme
  organ, e.g. its general meeting of shareholders⟩ until the vacancy is
  filled.

> *Instruction:* [⟨PREFIX⟩-GOV-3] is where you draw the line between
> governance and operations. Operators (section T6) are for routine,
> high-volume messages: starting and validating onboarding processes,
> issuing and revoking, adjusting deposits. Acts that change who controls
> the Corporation, or that are rare and consequential, stay with the group.
> The VPR itself allows Grant Operator Authorization to be executed by an
> existing operator; if you want it group-only, say so here and do not
> include it in any operator's `msg_types`.

## T6. Operators and Delegation

### T6.1 Operator authorizations

- [⟨PREFIX⟩-OPS-1] The on-chain `OperatorAuthorization` entries of this
  Corporation (List Operator Authorizations, [MOD-DE-QRY-1]) are the
  authoritative list of its operators. The registered organization MUST
  grant operator authorizations only to ⟨eligible grantees, e.g. accounts
  controlled by its employees, its contracted Verifiable Service provider
  named in section T6.3, or its own infrastructure⟩.
- [⟨PREFIX⟩-OPS-2] Every operator authorization MUST enumerate only the
  `msg_types` the operator needs, MUST carry an `expiration` no later than
  ⟨months — suggested: 12⟩ months after grant, and SHOULD carry a
  `spend_limit` with a `period` where the authorized messages move funds
  (trust-deposit adjustments, fees).
- [⟨PREFIX⟩-OPS-3] The registered organization MUST revoke the operator
  authorization of any account whose controller leaves the organization,
  changes function, or is suspected of compromise, within ⟨business days —
  suggested: 2⟩ business days of the event ([MOD-DE-MSG-4]).
- [⟨PREFIX⟩-OPS-4] The registered organization MUST review all active
  operator authorizations at least every ⟨months — suggested: 12⟩ months
  and record the review in ⟨its internal register⟩.
- [⟨PREFIX⟩-OPS-5] An operator MUST accept the version of this framework in
  force before its first use of its authorization ([MOD-GF-MSG-4]), and each
  later version within the grace period the registered organization sets at
  activation ([⟨PREFIX⟩-AMND-5]); until it does, its authorization is
  unusable (VPR [GF-CHECK-2]). The network fee of the acceptance is paid
  ⟨by the operator / by the registered organization through the operator's
  fee grant, whose `msg_types` then list
  `AcceptCorporationGovernanceFramework`⟩.

### T6.2 Fee grants

- [⟨PREFIX⟩-OPS-5] Fee grants (`with_feegrant` on [MOD-DE-MSG-3], or
  Grant Fee Allowance [MOD-DE-MSG-1]) MUST be limited to the `msg_types` of
  the corresponding operator authorization and SHOULD carry a
  `feegrant_spend_limit` per period. The `policy_address` balance that funds
  them is replenished by ⟨the organ or process that funds it⟩.

### T6.3 Verifiable Service operators

⟨Describe the Verifiable Service agents (VS operators) that act for this
Corporation's Participant entries, the provider operating them if
outsourced, and the scope of their `VSOperatorAuthorization` records — or:⟩

**No stipulation.**

- [⟨PREFIX⟩-OPS-6] Where this Corporation's Verifiable Services are operated
  by a third party, the registered organization MUST name the provider in
  this section, MUST keep the provider's `vs_operator` accounts distinct
  from any operator account of section T6.1, and remains fully and
  non-delegably responsible for every message those accounts sign.

> *Instruction:* VS operator authorizations are created in the context of a
> Participant entry (onboarding, root participant creation) and grouped per
> (corporation, vs_operator); their spend and fee budgets are stored in
> `ParticipantAuthorizationRecord` entries. A grantee cannot hold both an
> Operator Authorization and a VS Operator Authorization from the same
> Corporation — plan your accounts accordingly.

## T7. Ecosystems Controlled and Roles Held

### T7.1 Ecosystems controlled by this Corporation

| Ecosystem | Ecosystem DID | EGF URL |
| --- | --- | --- |
| ⟨name⟩ | ⟨did:…⟩ | ⟨URL of the active EGF⟩ |

⟨or:⟩ **No stipulation.** This Corporation controls no Ecosystem.

- [⟨PREFIX⟩-ECO-1] Every Ecosystem controlled by this Corporation MUST be
  governed by its own Ecosystem Governance Framework, published per Network
  GF chapter [NGF-EGF]. This framework states no ecosystem rule.

### T7.2 Participant roles in other ecosystems

*This section is non-normative.*

This Corporation owns Participant entries in ecosystems it does not control.
Each such entry is governed by the EGF of its ecosystem, which this
organization accepted by conduct when it applied. The authoritative list is
the on-chain Participant registry; ⟨optionally: a convenience list is
maintained at ⟨URL⟩⟩.

> *Instruction:* Do not copy your issuer or verifier obligations here; they
> live in the EGFs. The point of T7 is navigation: a reader of your CGF
> should be able to find every governance framework you are bound by.

## T8. Trust Deposit and Financial Standing

Suggested text:

- [⟨PREFIX⟩-FIN-1] The registered organization acknowledges that trust
  deposits on the Verana network are non-withdrawable and that Trust Units
  are non-transferable and non-convertible (Network GF [NGF-ECON-1]), and
  MUST fund the deposits required for its Participant entries from ⟨its
  own treasury / the process named here⟩.
- [⟨PREFIX⟩-FIN-2] If any deposit of this Corporation is slashed by an
  ecosystem ([MOD-PP-MSG-12]) or by the network ([MOD-TD-MSG-5]), ⟨the
  accountable organ⟩ MUST decide within ⟨days — suggested: 30⟩ days whether
  to repay ([MOD-PP-MSG-13], [MOD-TD-MSG-6]) or to contest through the
  appeal path of the sanctioning framework, and MUST record the decision in
  ⟨its internal register⟩. While a network slash is unrepaid, all
  permissions of this Corporation are non-trustable, as the VPR provides.
- [⟨PREFIX⟩-FIN-3] The registered organization MUST keep the
  `policy_address` and its operator accounts funded to meet the fees of the
  messages it is obliged to execute under any EGF it is bound by (in
  particular revocations), so that an obligation never fails for want of
  fees.

> *Instruction:* Keep T8 short. Deposit amounts are set by the schemas you
> participate in, not by you; what you decide is who pays, who decides on
> repayment, and how fast.

## T9. Keys, Security and Incident Handling

- [⟨PREFIX⟩-SEC-1] Group member keys, operator keys, VS operator keys, and
  the keys controlling the Corporation DID MUST be separate keys. Group
  member keys SHOULD be held in hardware or a remote signer and MUST NOT be
  held by a third-party service provider.
- [⟨PREFIX⟩-SEC-2] On suspected or confirmed compromise of an operator key,
  the registered organization MUST revoke the authorization ([MOD-DE-MSG-4])
  within ⟨hours — suggested: 24⟩ hours; on compromise of a group member
  key, it MUST replace the member through a group proposal within ⟨hours —
  suggested: 72⟩ hours; on compromise of the Corporation DID's keys, it MUST
  rotate the DID ([MOD-CO-MSG-2]) without the notice period of
  [⟨PREFIX⟩-ORG-5] and publish the rotation per [⟨PREFIX⟩-ORG-6].
- [⟨PREFIX⟩-SEC-3] The registered organization MUST notify the ecosystem
  governance authority of every ecosystem in which it holds a Participant
  entry of any incident under [⟨PREFIX⟩-SEC-2] within ⟨hours — suggested:
  72⟩ hours, and MUST perform the revocation duties the applicable EGFs
  attach to such incidents.
- [⟨PREFIX⟩-SEC-4] ⟨Further security commitments, e.g. a reference to the
  organization's information-security policy or certification — or:⟩ **No
  stipulation.**

## T10. Lawful Purpose, Privacy and Data Handling

Suggested text:

- [⟨PREFIX⟩-LAW-1] The registered organization MUST use the Verana network
  only for lawful purposes ([NGF-PART-5]).
- [⟨PREFIX⟩-LAW-2] The registered organization MUST NOT write personal data
  to the network, in any message, metadata field (including `group_metadata`
  and `group_policy_metadata`), DID document, or governance framework
  document, and MUST NOT require any operator or group member to do so
  ([NGF-PART-5], [TCGF-14]).
- [⟨PREFIX⟩-LAW-3] Personal data the organization processes off-chain in
  connection with its Verana activities is governed by ⟨its privacy notice
  at ⟨URL⟩ / the data-handling sections of the applicable EGFs⟩.

## T11. Contact, Reports and Disputes

- [⟨PREFIX⟩-DSP-1] The registered organization MUST maintain the contact
  channel of section T4.1 as the intake for questions, notices, and reports
  concerning this Corporation, and MUST acknowledge a report within
  ⟨business days — suggested: 5⟩ business days.
- [⟨PREFIX⟩-DSP-2] Reports that concern the conduct of ⟨the accountable
  organ⟩ itself MAY be escalated to ⟨an independent escalation point, e.g.
  the organization's audit committee, or the EGA of the ecosystem
  concerned⟩.
- [⟨PREFIX⟩-DSP-3] Disputes between this Corporation and a participant or
  ecosystem governance authority of an ecosystem are resolved under the
  dispute mechanism of that ecosystem's EGF; disputes concerning network
  matters follow Network GF chapter 11 (Dispute Resolution). Any residual dispute
  concerning this framework is subject to ⟨governing law⟩ and ⟨forum⟩.

## T12. Continuity and Wind-Down

- [⟨PREFIX⟩-END-1] If the registered organization intends to cease acting
  on the Verana network, it MUST, in this order: publish a notice at the
  publication points of [⟨PREFIX⟩-ORG-5] at least ⟨days — suggested: 90⟩
  days in advance; for every Ecosystem it controls, execute the abandonment
  or migration procedure of that ecosystem's EGF; for every Participant
  entry it owns, perform the exit and termination duties of the applicable
  EGF (including revocation of unexpired credentials); revoke every operator
  and VS operator authorization; and publish a final version of this
  framework recording the wind-down.
- [⟨PREFIX⟩-END-2] The registered organization MUST keep every version of
  this framework that was ever active retrievable at its anchored URL for
  at least ⟨years — suggested: 10⟩ years after the last activation, or
  transfer the hosting to ⟨a named successor or archive⟩ with the digests
  unchanged.
- [⟨PREFIX⟩-END-3] On dissolution, merger, or change of control of the
  registered organization, the successor entity MUST either assume this
  Corporation entry under an amended framework identifying it (section
  T4.1) or wind the entry down per [⟨PREFIX⟩-END-1]. A Corporation entry
  MUST NOT be left under the control of an entity this framework does not
  identify.

> *Instruction:* The VPR has no message that deletes a Corporation entry or
> transfers it to another organization. "Wind-down" therefore means leaving
> the entry inert and truthful: operators revoked, participant entries
> terminated under their EGFs, documents still resolvable. Hosting your CGF
> on a URL you can keep paying for after you stop operating (or on a
> content-addressed archive) is the practical consequence of [TCGF-8].

## T13. Amendment and Versioning

- [⟨PREFIX⟩-AMND-1] This framework is amended by ⟨the organ and decision
  rule, e.g. a resolution of the board of directors⟩, and the resulting
  version is activated on-chain by group proposal per [⟨PREFIX⟩-GOV-3].
- [⟨PREFIX⟩-AMND-2] An adopted amendment is published as a new
  `GovernanceFrameworkDocument` ([MOD-GF-MSG-1] without `ecosystem_id`, one
  document per language, in a version greater than the active one) and
  enters into force only upon on-chain activation ([MOD-GF-MSG-2] without
  `ecosystem_id`), which requires a document in the Corporation's primary
  language. Active versions are immutable; corrections are new versions.
- [⟨PREFIX⟩-AMND-3] Versions are sequential integers starting at 1,
  assigned by on-chain activation order. The change log in section T1 lists
  one row per activated version.
- [⟨PREFIX⟩-AMND-4] Amendments that change sections T4.1, T5, or T6.1 MUST
  be activated within the deadlines those sections set; other amendments
  MAY be activated at any time. ⟨Optionally: material amendments are
  published for comment to ⟨audience⟩ at least ⟨days⟩ days before
  adoption — or:⟩ **No stipulation** on comment periods.
- [⟨PREFIX⟩-AMND-5] Each activation sets an `acceptance_grace` of ⟨days —
  suggested: 30, the network minimum⟩ days, during which operators that
  accepted a former version keep using their authorizations; the registered
  organization notifies its operators at activation. An operator that has
  not accepted by the deadline is blocked until it does, without revocation
  of its authorization.

> *Instruction:* A CGF has no third-party participants to protect, so the
> Template EGF's 30-day comment and notice runway is not needed by default.
> What matters is the opposite direction: the framework must catch up with
> on-chain reality fast ([⟨PREFIX⟩-GOV-1], [⟨PREFIX⟩-ORG-1]). If your
> Corporation controls an ecosystem, consider mirroring the EGF's notice
> period for amendments to section T5, since ecosystem participants rely on
> knowing who controls their EGA.

## Annex A. Network GF Interface Checklist

*This annex is non-normative for the corporation's group members and
operators; it is the conformance-by-construction map for the CGF author.*

> *Instruction:* Network GF chapter 6, section 6.2 states the duties
> of every corporation on the network, and chapters [NGF-PRIN] and [NGF-EGF]
> set the publication rules the CGF inherits. The table maps each to the
> template section that satisfies it. Keep it, or delete it after checking.

| Network GF item | Rule | Template section |
| --- | --- | --- |
| Accurate registration information, kept current | [NGF-PART-3] | T1, T4.1, [⟨PREFIX⟩-ORG-1] |
| Control of the registered DID | [NGF-PART-3] | T4.2, T9 |
| CGF documents publicly resolvable and consistent with on-chain digests | [NGF-PART-4], [NGF-EGF-3] | T1, T13, [TCGF-8], [⟨PREFIX⟩-END-2] |
| Lawful purpose | [NGF-PART-5] | T10 |
| No personal data on-chain | [NGF-PART-5], [NGF-PRIN-7], [NGF-PRIN-10] | T10, [TCGF-14] |
| Deposits non-withdrawable; slash and repay-to-resume | [NGF-ECON-1], [NGF-ECON-3], [NGF-SANC-8] | T8 |
| EGF required for every controlled Ecosystem | [NGF-EGF-3], [NGF-EGF-5] | T7.1 |
| Creation is not endorsement | [NGF-EGF-7] | section 1, [TCGF-1] |
| Dispute tiers for network matters | Network GF chapter 11 | T11 |

## Annex B. Publication Instructions: The VPR Message Sequence

*This annex is non-normative. The VPR specification is authoritative for
every message named here.*

> *Instruction:* Execute in this order. Keep this annex in your CGF (it
> documents how your on-chain footprint was created), or move it to an
> operational runbook — your choice.

1. **Prepare version 1.** Resolve every ⟨field⟩ that can be known before
   creation, delete every Instruction block ([TCGF-2], [TCGF-3]), publish
   the document at a stable public URL in the Corporation's primary
   language, and compute its `digest_sri` (for example
   `sha384-…`). Version 1 is anchored **and activated** by the next step and
   can never be added, replaced, or re-activated afterwards ([TCGF-4]).
2. **Create New Corporation ([MOD-CO-MSG-1]).** Any account submits: the
   initial group `members` (address, weight), the `decision_policy`
   (threshold or percentage), the Corporation `did`, its primary
   `language`, the `doc_url` + `doc_digest_sri` of this document, and the
   `ngf_version` in force, the organization's acceptance of the Network GF
   ([NGF-PART-1]). In one transaction the chain creates the `x/group` group and its policy account
   (which becomes the admin of both; the submitting account keeps no
   privilege), the `Corporation` entry with `active_version` 1, and the
   version-1 `GovernanceFrameworkVersion` and `GovernanceFrameworkDocument`.
   Record the assigned `id` and `policy_address` in section T1.
3. **Grant Operator Authorization ([MOD-DE-MSG-3]).** By group proposal,
   grant each operator of section T6.1 its enumerated `msg_types`, an
   `expiration`, optional spend limits and period, and `with_feegrant` as
   decided in section T6.2. Repeat Revoke ([MOD-DE-MSG-4]) and Grant as
   operators change.
4. **Later versions only — Add Governance Framework Document
   ([MOD-GF-MSG-1]) then Increase Active Governance Framework Version
   ([MOD-GF-MSG-2]), both without `ecosystem_id`.** For every version after
   the first: anchor, per language, a `GovernanceFrameworkDocument` (public
   URL + `digest_sri`) in a version greater than the active one — only
   future versions are editable — then activate it. Activation requires a
   document in the Corporation's primary language and, per [TCGF-4], must
   not happen while Instruction blocks or unresolved ⟨fields⟩ remain.
5. **Update Corporation ([MOD-CO-MSG-2]).** Only on DID rotation (section
   T4.2 or T9). The new DID must not be held by any other Corporation nor by
   an Ecosystem or Participant entry of another corporation.
6. **Ecosystems and participation.** Create New Ecosystem ([MOD-ES-MSG-1])
   with the EGF from the Template EGF for each ecosystem of section T7.1;
   start onboarding processes ([MOD-PP-MSG-1]) in third-party ecosystems for
   the roles of section T7.2. Those sequences are documented in the Template
   EGF, Annex B.

## Annex C. Parameter Collection Sheet (Initial Parameters)

> *Instruction:* Every number you chose above must appear here, per
> [TCGF-10], with its change process. Parameters change only through the
> amendment process of section T13 unless a lighter process is stated per
> row. Suggested defaults shown are template recommendations, not
> requirements.

| Parameter | Where set | Initial value | Change process |
| --- | --- | --- | --- |
| Identification correction deadline | T4.1 | ⟨days — suggested: 30⟩ | ⟨T13⟩ |
| Change-of-control disclosure deadline | T4.1 | ⟨days — suggested: 30⟩ | ⟨T13⟩ |
| DID rotation notice | T4.2 | ⟨days — suggested: 30⟩ | ⟨T13⟩ |
| Group configuration mirror deadline | T5.2 | ⟨days — suggested: 30⟩ | ⟨T13⟩ |
| Decision policy (type, threshold, voting period, execution period) | T5.2 | ⟨values⟩ | ⟨group proposal, then T13 mirror⟩ |
| Operator authorization maximum lifetime | T6.1 | ⟨months — suggested: 12⟩ | ⟨T13⟩ |
| Operator revocation deadline on departure | T6.1 | ⟨business days — suggested: 2⟩ | ⟨T13⟩ |
| Operator review cadence | T6.1 | ⟨months — suggested: 12⟩ | ⟨T13⟩ |
| Slash repay-or-contest decision deadline | T8 | ⟨days — suggested: 30⟩ | ⟨T13⟩ |
| Operator key compromise revocation | T9 | ⟨hours — suggested: 24⟩ | ⟨T13⟩ |
| Group key compromise replacement | T9 | ⟨hours — suggested: 72⟩ | ⟨T13⟩ |
| Incident notification to EGAs | T9 | ⟨hours — suggested: 72⟩ | ⟨T13⟩ |
| Report acknowledgement | T11 | ⟨business days — suggested: 5⟩ | ⟨T13⟩ |
| Wind-down notice | T12 | ⟨days — suggested: 90⟩ | ⟨T13⟩ |
| Document retention after last activation | T12 | ⟨years — suggested: 10⟩ | ⟨T13⟩ |
| Amendment comment period (optional) | T13 | ⟨days or "none"⟩ | ⟨T13⟩ |

## Annex D. Design Questions, Pre-Answered

*This annex is non-normative.*

> *Instruction:* A completeness self-check before publication. Every
> question below must be answerable from your finished CGF; the right-hand
> column shows where the template answers it with a VPR-native default.
> Delete this annex, or keep it as a reader's map — your choice.

| Question | Template answer |
| --- | --- |
| Which legal entity stands behind this Corporation entry? | T4.1 identification; [⟨PREFIX⟩-ORG-3] one entity per entry |
| How does the Corporation decide? | T5: group members by function, weights, decision policy mirrored from `x/group`; [⟨PREFIX⟩-GOV-2] off-chain authorization of votes |
| Who may sign for it day to day, and within what limits? | T6: operator authorizations as the authoritative list, scoped `msg_types`, expiration, spend limits, review cadence |
| Which acts are reserved to the group? | [⟨PREFIX⟩-GOV-3] |
| What happens if a key is compromised? | T9: revoke, replace, rotate, notify EGAs |
| Which governance frameworks is this organization bound by? | T2.3 layering; T7 ecosystems controlled and roles held |
| Who pays deposits and fees, and who decides on repayment after a slash? | T8 |
| How do relying parties verify this document? | T1 metadata mirrors on-chain `url` + `digest_sri`; [TCGF-8] |
| How do the rules change? | T13: new document, new version, on-chain activation as entry into force |
| What happens if the organization disappears or is sold? | T12: notice, EGF wind-down duties, operator revocation, document retention, successor identification |

## Version History

| Version | Date | Status | Summary |
| --- | --- | --- | --- |
| 0.1 | 2026-10-14 | Draft | First draft for co-authoring by Founding Members. Written against VPR specification v5 (draft): Corporation entries anchored by an `x/group` policy address, mandatory version-1 CGF at creation ([MOD-CO-MSG-1]), operator and VS operator authorizations, fee grants, polymorphic Governance Framework module. One `[DECISION]` flag (whether the Network GF should gain a mandatory-contents chapter for CGFs). Recorded acceptance: operators accept the framework before use (T2.4, [⟨PREFIX⟩-OPS-5], [⟨PREFIX⟩-AMND-5]); `ngf_version` at creation (Annex B). |
