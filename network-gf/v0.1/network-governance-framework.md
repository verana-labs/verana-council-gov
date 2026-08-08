# Verana Network Governance Framework

> **Status: DRAFT 0.1 — first draft for co-authoring by Founding Members.** This document is not yet in force. It is ratified at the Incorporation General Assembly of the Verana Council Association (target Q4 2026). Where this document states protocol facts, the [Verifiable Trust specification](https://verana-labs.github.io/verifiable-trust-spec/) and the [Verifiable Public Registry (VPR) specification](https://verana-labs.github.io/verifiable-trust-vpr-spec/) prevail. Where it states entity facts, the Verana entity definitions and the Council public record prevail. During the pre-incorporation period, 2060 OÜ acts as transitional steward; every steward power carries an event-triggered sunset (chapter [NGF-TRAN]).

| Document control | |
| --- | --- |
| Document Name | Verana Network Governance Framework (Network GF) |
| Version | DRAFT 0.1 |
| Status | Draft — for co-authoring by Founding Members |
| Governs | The Verana network (the live, validator-secured VPR chain): the constitutional floor every EGF anchored on it must respect, and the network-facing duties of every participant |
| Governed By | The Verana Council Association (in formation), acting through the mechanisms of chapter [NGF-GOV] |
| Approved By | Pending — Incorporation General Assembly, target Q4 2026 |
| Approval Date | Pending |
| License | Creative Commons Attribution-ShareAlike 4.0 International (CC-BY-SA 4.0) |
| Anchoring | Git history and tagged releases in `verana-labs/verana-council-gov` and a public URL now; on-chain `GovernanceFrameworkDocument` (`url` + `digest_sri`) once the network is live |

## 1. Introduction

*This section is non-normative.*

### 1.1 Purpose

The Verana network is a Verifiable Public Registry (VPR): a public, decentralized "registry of registries" on which ecosystems publish their governance frameworks, credential schemas, and authorizations, so that any relying party can independently resolve who is authorized to issue, verify, or govern credentials in a given context. The VPR stores registrations, not validations — trust decisions and cryptographic verification remain with the relying parties.

The VPR specification states that "a governance framework must define the governance rules that apply to a VPR" and that "a designated governance authority (aka a council) is responsible for enforcing these rules and, when necessary, applying financial sanctions to participants who violate the rules". This document is that governance framework, and the Verana Council Association is that governance authority.

This document is deliberately thin and constitutional. It governs the commons — the shared substrate every ecosystem depends on — and nothing else. It defines who governs the network, through which enumerated powers, under which principles and hard limits; what every network participant owes the commons; what every Ecosystem Governance Framework (EGF) anchored on the network must contain; how network validators operate; how network-level sanctions and disputes work; and how this document itself changes. Operational depth belongs to subordinate documents, above all the ECS Ecosystem Governance Framework (ECS-EGF).

### 1.2 What this document does not govern

Ecosystems on Verana are autonomous. Anyone can create a Corporation and an Ecosystem on the network without the Council's permission. Each ecosystem governs itself under its own EGF, run by its own ecosystem governance authority (EGA). The VPR specification is explicit: "This separation ensures that ecosystems remain autonomous and can tailor governance to their unique needs, without being constrained by the global rules of the VPR." This document accordingly never reaches inside an ecosystem: it constrains what an EGF must *contain* and *publish* (chapter [NGF-EGF]) as a condition of recognition, never what an ecosystem must *decide*.

### 1.3 Document architecture

| Document | Layer | Relationship to this document |
| --- | --- | --- |
| Verifiable Trust specification (VT), VPR specification | Protocol standards, owned and hosted by the Verana Foundation | Sources of truth for all protocol facts; where this document paraphrases them, they prevail |
| **Network Governance Framework** (this document) | Constitutional layer of the network | Governs the commons; every EGF must respect it |
| ECS Ecosystem Governance Framework (ECS-EGF) | The Council's own ecosystem (four Essential Credential Schemas) | An EGF like any other; must itself satisfy chapter [NGF-EGF]; the reference implementation of those requirements |
| Template EGF | Voluntary scaffold for ecosystems authoring their own EGF | Offered, never required; using it implies no endorsement |
| Verana Council Association Statutes, Bylaws, Code of Conduct | Association layer (Swiss law) | Govern the Verein as a legal person; carry no network authority beyond what this document channels through the mechanisms of chapter [NGF-GOV] |

Precedence within the governance stack: for protocol facts, the VT and VPR specifications prevail over every governance document. For network governance, this document prevails over every EGF, and every EGF prevails over the participant agreements and policies published under it. For association-law matters, Swiss law and the Statutes prevail. Ecosystem autonomy sits *below* the line drawn by this document and is unlimited beneath it.

### 1.4 Reading guide

Normative requirements carry stable bracketed identifiers (for example **[NGF-POW-1]**). Identifiers are permanent: they are never renumbered or reused, including after deletion. Sections marked "*This section is non-normative.*" carry no requirements. Quantified thresholds introduced by this document are Initial Parameters, collected in Annex A with their change process. Cross-references to the sibling documents cite chapter identifier prefixes (for example "chapter [ECS-ACC]") because those documents are versioned independently.

## 2. Conformance and Terminology

### 2.1 Conformance

The key words MUST, MUST NOT, REQUIRED, SHALL, SHALL NOT, SHOULD, SHOULD NOT, RECOMMENDED, MAY, and OPTIONAL in this document are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174) when, and only when, they appear in all capitals, as shown here.

Each requirement in this document is addressed to a named role. A statement without an RFC 2119 keyword, or in a section marked non-normative, is informative.

### 2.2 Terminology

Terms defined in the VT specification and the VPR specification (including *corporation*, *ecosystem*, *credential schema*, *participant*, *trust deposit*, *trust unit*, *governance framework*, *governance authority*, *onboarding process*, and the participant roles `ECOSYSTEM`, `ISSUER_GRANTOR`, `VERIFIER_GRANTOR`, `ISSUER`, `VERIFIER`, `HOLDER`) are used with their specification meanings and are not redefined here. Onboarding-mode names are used in their v4 form (`OPEN`, `GRANTOR_ONBOARDING_PROCESS`, `ECOSYSTEM_ONBOARDING_PROCESS`, `ISSUER_ONBOARDING_PROCESS`, `PERMISSIONLESS`).

The following local terms are defined for this document. Definitions carry no normative keywords.

- **Council**: the Verana Council Association, a non-profit Swiss Verein (Art. 60 ZGB), in formation with target incorporation Q4 2026; the governance authority of the Verana network in the sense of the VPR specification.
- **Member** (also **Founding Member**): an organization holding a seat in the Council. Member here always means the Verein member; it is distinct from *Participant*, which is a VPR on-chain role.
- **General Assembly**: the supreme organ of the Verein (Art. 64 ZGB), composed of all seated Members, one vote each. Always spelled out in this document; the abbreviation "GA" is not used, to avoid collision with "governance authority".
- **Board**: the small body elected by the General Assembly that runs and legally represents the association.
- **seated member**: a Member whose admission is complete and whose seat is active (not departed and not suspended).
- **eligible member**: for a given decision, a seated member who is not recused from that decision.
- **network validator**: a consensus node of the Verana chain, operated by a Member. Never abbreviated to bare "validator" where ambiguity is possible.
- **onboarding validator**: the VPR Participant that validates an applicant in an onboarding process (the "validator" of the VPR Participant module). Not a network validator.
- **ecosystem governance authority (EGA)**: the governance authority of an ecosystem, responsible for its EGF.
- **protocol-governance change**: any exercise of an enumerated power of chapter [NGF-POW], including any governance proposal, any change to this document or to a Controlled Document under it, and any network software upgrade adoption.
- **Controlled Document**: a document subordinate to this framework, independently versioned, listed with an owning body, and amendable on the legislative tier of chapter [NGF-AMND].
- **Initial Parameter**: a quantified threshold set by this document, listed in Annex A with its change process.
- **Cause**: with respect to a Member, a violation of applicable law rendering continued membership unlawful; a material breach of this document, the Statutes, the Bylaws, the Code of Conduct, or any Controlled Document binding Members; an insolvency event; or an unreported change of control under [NGF-GOV-13].
- **Related Party**: with respect to an organization, any entity that controls it, is controlled by it, or is under common control with it, where control means holding more than 50% of voting rights or the contractual or de facto power to direct management and policies.
- **Steward Period**: the period from the start of Council formation until mainnet launch during which 2060 OÜ acts as transitional steward (chapter [NGF-TRAN]); individual steward privileges sunset earlier on their own event triggers ([NGF-TRAN-1]).
- **Provisional Governance Period**: the period before mainnet launch during which Council voting is exercised off-chain under chapter [NGF-TRAN].

## 3. Governance Authority

### 3.1 The Verana Council Association

*This paragraph is non-normative.* The Council is the sole body that governs and secures the live Verana network. It is fully separate from the Verana Foundation (which owns and hosts the specifications, stewards the open-source software, and issues and administers — but does not own — the VNA token, and which cannot govern, secure, or operate the network). Membership is free of dues and capital contributions; member liability is excluded by statute (Art. 75a ZGB); seats are capped at 25, organized by sector with soft regional balance.

- **[NGF-GOV-1]** The Council MUST act as the governance authority of the Verana network exclusively through the mechanisms defined in this document, and MUST NOT exercise any network authority outside the enumerated powers of chapter [NGF-POW].
- **[NGF-GOV-2]** The Council MUST maintain a public record of all governance acts, including seatings, departures (with their stated nature), suspensions and their lifting, removal-for-cause rationales, ballots opened and their outcomes, framework versions, and parameter changes. The record is symmetric: exits are recorded, not silent.

### 3.2 Two governance layers

- **[NGF-GOV-3]** The Council MUST keep its two governance layers distinct: association governance (statutes, budget, admissions and expulsions, staff, legal representation), exercised by the General Assembly and the Board under Swiss law and the Statutes; and network governance (this framework, the ECS-EGF, the Template EGF, and network parameters), exercised on-chain via network validator nodes after mainnet launch, and under the Provisional Governance Period rules of chapter [NGF-TRAN] before it.
- **[NGF-GOV-4]** The association MUST recognize on-chain governance outcomes as final for network matters: the General Assembly does not re-vote what the chain has decided, and the chain does not manage the association.
- **[NGF-GOV-5]** The Board MUST NOT hold or exercise any network authority. A Board seat confers no protocol power of any kind. Any Board act purporting to bind the network is void.

### 3.3 Voting rule and denominator discipline

- **[NGF-GOV-6]** Every protocol-governance change MUST be approved by a two-thirds (⅔) supermajority of seated members.
- **[NGF-GOV-7]** The denominator for any Council vote MUST be the number of seated members. Recusal (voluntary or by conflict rule) removes a member's vote from that decision but does not shrink the denominator: abstentions, absences, and recusals all remain in the denominator.
- **[NGF-GOV-8]** A supermajority threshold MUST be computed as the smallest whole number of affirmative votes greater than or equal to the stated fraction of the denominator. The quorum for a vote is the passing threshold itself: a proposal passes when the required number of affirmative votes exists, and fails otherwise, regardless of turnout.

*Worked example (non-normative).* 21 members are seated; 2 are recused from the decision. The denominator is 21. Two-thirds of 21 is 14, so 14 affirmative votes are required. The 2 recused members cannot vote, so at most 19 votes can be cast; if fewer than 14 members vote in favor, the proposal fails in that round.

- **[NGF-GOV-9]** Decisions taken by written or asynchronous consent MUST require the same number of affirmative votes as a vote in a meeting, and MUST allow every eligible member at least 14 days (Initial Parameter) to cast its vote after notice.
- **[NGF-GOV-10]** The off-chain voting rule of the Provisional Governance Period MUST be numerically identical to the on-chain ⅔ rule ([NGF-GOV-6] to [NGF-GOV-8]), so that pre-mainnet and post-mainnet decisions are provably governed by the same arithmetic.

### 3.4 Committees, delegation, and vacancy fallback

- **[NGF-GOV-11]** Council committees (such as the Membership & Seats Committee and the Technical / Validator Committee) MUST be advisory by default: a committee recommends, evaluates, and prepares, and MUST NOT cause any act with on-chain economic or permission effect. Every exercised delegation of decision authority to a committee requires a published charter and is reported on the public record. A committee recommendation is due within the deadline stated in its charter or referral (or, absent one, the decision deadline of [NGF-SANC-13]); an overdue matter reverts to the General Assembly per [NGF-GOV-12].
- **[NGF-GOV-12]** If a body designated by this document or its Controlled Documents is vacant or unable to act, its duties MUST revert to the General Assembly until the body is reconstituted.

### 3.5 Anti-capture: related parties and change of control

- **[NGF-GOV-13]** A Member MUST disclose to the Council any change of control (as defined for Related Parties) affecting it within 14 calendar days (Initial Parameter) of the change becoming effective.
- **[NGF-GOV-14]** A Related-Party group MUST NOT hold more than 1 seat (Initial Parameter) in the Council. The test is applied at admission and re-applied whenever a merger, acquisition, or change of control is disclosed or discovered.
- **[NGF-GOV-15]** Where a disclosed or discovered change places a Related-Party group above the seat cap and the affected Members do not agree within 60 days (Initial Parameter) which seat is relinquished, the seat to be relinquished MUST be selected by random lot among the group's seats, conducted publicly.

> **[DECISION]** The Related-Party seat cap is set at **1** (Hiero uses 2 of 9 TSC seats). For a 25-seat body whose hard limit is "not single-company controlled", one seat per corporate group is the coherent reading of one-member-one-vote; the alternative (cap = 2, tolerating affiliated pairs) would ease recruitment of large conglomerates at the cost of arithmetic dilution of the diversity rule. Founding Members should confirm.

### 3.6 Governance of the governing authority

*This paragraph is non-normative.* Who governs the governor: the Verein's Statutes, Bylaws, and Code of Conduct (association layer, published in `verana-labs/verana-council-gov`), Swiss association law, and the public record of [NGF-GOV-2]. Verana has no external regulatory oversight committee; its structural substitutes are one-member-one-vote, the ⅔ supermajority, the Board's zero network authority, the seat cap with sector and regional diversity, record symmetry, and the Public-Sector Observer track (contractual participation with attendance and voice, no vote).

- **[NGF-GOV-16]** The Council MUST itself comply with this framework. Where this document imposes a duty on ecosystem governance authorities or participants, the Council, acting as the EGA of the ECS ecosystem, is bound identically (see ECS-EGF [ECS-GEN-1] to [ECS-GEN-3]).

### 3.7 Continuity and wind-down

- **[NGF-GOV-17]** The Council MUST NOT be dissolved, and the association MUST NOT otherwise terminate, before it has (a) published all procedures necessary to enable the ongoing operation and evolution of the Verana network without it, and (b) effected the validator-set, key, and governance transitions those procedures require. Network survival precedes association termination.
- **[NGF-GOV-18]** On dissolution, remaining association assets MUST NOT be distributed to Members; they are applied to a non-profit purpose consistent with the association's purpose, as the Statutes provide.
- **[NGF-GOV-19]** Council membership confers no economic claim of any kind: no token allocation, no revenue share, and no distribution on dissolution ([NGF-GOV-18]). The Council MUST NOT create, promise, or simulate any such claim.

## 4. Principles

*The principles in this chapter are stated without normative keywords. They are citable interpretive anchors: the operative chapters of this document give them effect, and where the meaning of a requirement is in doubt, it is resolved in favor of these principles.*

- **[NGF-PRIN-1] Neutrality.** The registry's entire value is neutrality. The network picks no winners: it makes authorization resolvable so anyone can verify it independently.
- **[NGF-PRIN-2] Equality.** One member, one vote. Economic weight and governance power are decoupled, and the protocol says so itself: "Holding a large trust deposit does not grant governance rights in the VPR: participants who generate high transaction volume cannot gain control over the governance of the VPR solely through usage or deposit size" (VPR specification).
- **[NGF-PRIN-3] Openness.** Ecosystem creation is permissionless: any account can create a Corporation and an Ecosystem without Council approval. All registry data is publicly readable. Validation is permissioned; everything else is permissionless.
- **[NGF-PRIN-4] Federalism.** Ecosystems are autonomous: "ecosystems remain autonomous and can tailor governance to their unique needs, without being constrained by the global rules of the VPR" (VPR specification). The Council governs the commons; every ecosystem governs itself.
- **[NGF-PRIN-5] Transparency.** Governance emits a dated, public, citable record; the record is symmetric (exits and suspensions are recorded like admissions); governance documents are digest-anchored and their active versions immutable.
- **[NGF-PRIN-6] Accountability.** The parties who hold power are identified: named organizations govern, named organizations operate validators, and each role answers for its own function.
- **[NGF-PRIN-7] Data minimization.** The network anchors identifiers, schemas, permissions, digests, and revocation references — never personal data or credential contents.
- **[NGF-PRIN-8] Verify, don't trust.** Every guarantee this framework relies on is preferentially enforced by the protocol and verifiable by anyone; human assurance covers only the residue.
- **[NGF-PRIN-9] Proportionality.** Sanctions are graduated, grounded in enumerated causes, and no one profits from punishment: slashed deposits are burned, not paid to the sanctioning party.
- **[NGF-PRIN-10] Legal safety.** Nothing in this framework requires any party to violate applicable law.

**Twin disclaimers.** Council membership grants no economic claim of any kind — no token allocation, no revenue share, no distribution on dissolution ([NGF-GOV-19]). And no economic position grants governance rights — no trust deposit, fee volume, or token holding converts into a vote ([NGF-ECON-13]).

## 5. Enumerated Powers and Hard Limits

### 5.1 Enumerated on-chain powers

*This paragraph is non-normative.* The VPR specification reserves a closed set of module messages to governance: "Some module messages can be executed only through a VPR council governance proposal." That list, reproduced below, is the Council's complete on-chain power inventory.

- **[NGF-POW-1]** The Council's on-chain authority over the network MUST consist exclusively of the following governance-proposal-only messages of the VPR specification, each exercisable only through a governance proposal adopted under [NGF-GOV-6]:

| # | Power | VPR message | Module |
| --- | --- | --- | --- |
| 1 | Update Corporation Module Parameters | [MOD-CO-MSG-3] | Corporation |
| 2 | Update Ecosystem Module Parameters | [MOD-ES-MSG-4] | Ecosystem |
| 3 | Update Credential Schema Module Parameters | [MOD-CS-MSG-4] | Credential Schema |
| 4 | Update Participant Module Parameters | [MOD-PP-MSG-11] | Participant |
| 5 | Update Trust Deposit Module Parameters | [MOD-TD-MSG-4] | Trust Deposit |
| 6 | Slash Trust Deposit (network-level) | [MOD-TD-MSG-5] | Trust Deposit |
| 7 | Create Exchange Rate | [MOD-XR-MSG-1] | Exchange Rate |
| 8 | Set Exchange Rate State | [MOD-XR-MSG-3] | Exchange Rate |
| 9 | Grant Exchange Rate Authorization | [MOD-XR-MSG-4] | Exchange Rate |
| 10 | Revoke Exchange Rate Authorization | [MOD-XR-MSG-5] | Exchange Rate |

- **[NGF-POW-2]** In addition to [NGF-POW-1], the Council MUST author, maintain, and version its own governance framework documents — this Network Governance Framework, the ECS Ecosystem Governance Framework, and the Template EGF — including their on-chain publication and activation for the Council's own Corporation and Ecosystem entries (MOD-GF-MSG-1, MOD-GF-MSG-2), and the adoption of network software upgrades under chapter [NGF-EVOL]. These acts are protocol-governance changes and are gated by [NGF-GOV-6].

### 5.2 Closure

- **[NGF-POW-3]** The Council has no network authority other than [NGF-POW-1] and [NGF-POW-2]. The Council MUST NOT exercise, claim, or construct any other authority over the network, its participants, its ecosystems, or their data.
- **[NGF-POW-4]** No capability extending the Council's network authority beyond [NGF-POW-1] and [NGF-POW-2] MUST be implemented, activated, or exercised before (a) this document has been amended under chapter [NGF-AMND] to enumerate it, and (b) the policies governing its use have been published.

### 5.3 Hard limits

- **[NGF-POW-5]** The Council MUST NOT act as a standards body. The Verifiable Trust and VPR specifications are owned and hosted by the Verana Foundation; the Council adopts and applies them and holds no authority over their content ([NGF-PRIN-1], [NGF-PRIN-6]).
- **[NGF-POW-6]** The Council MUST NOT act as a product vendor, sell products or services, or hold commercial customer contracts ([NGF-PRIN-1]).
- **[NGF-POW-7]** The Council MUST NOT act as the governance authority of any ecosystem other than its own ECS ecosystem, and MUST NOT approve, veto, amend, or overrule any other ecosystem's EGF, accreditations, policies, or penalties ([NGF-PRIN-4]).
- **[NGF-POW-8]** The Council MUST NOT act as a grant-making body and MUST NOT fund, subsidize, or financially guarantee any network participant ([NGF-PRIN-1], [NGF-PRIN-9]).
- **[NGF-POW-9]** The Council MUST NOT issue, own, or claim ownership of the VNA token. Receiving the protocol-defined on-chain funding allocation of [NGF-ECON-12] does not make the Council the token's issuer or owner ([NGF-PRIN-2]).
- **[NGF-POW-10]** The Council MUST NOT be controlled by a single company or Related-Party group; [NGF-GOV-13] to [NGF-GOV-15] operationalize this limit ([NGF-PRIN-2], [NGF-PRIN-6]).

### 5.4 The federal boundary

- **[NGF-POW-11]** The Council MUST NOT apply any sanction, or take any enforcement act, for conduct governed by an ecosystem's EGF. Network-level sanctions (chapter [NGF-SANC]) exist only for network-level violations. The protocol gives the Council no instrument inside an ecosystem, by design: "ecosystems remain autonomous and can tailor governance to their unique needs, without being constrained by the global rules of the VPR" (VPR specification). Sanctions within an ecosystem belong exclusively to that ecosystem's EGA and its onboarding-validator tree.

## 6. Network Participants and Obligations

### 6.1 Acceptance by conduct

- **[NGF-PART-1]** Submitting any transaction to the Verana network constitutes acceptance of the version of this Network Governance Framework active at submission time.
- **[NGF-PART-2]** Participating in an ecosystem — including applying for, holding, or exercising any Participant permission under one of its credential schemas — constitutes acceptance of that ecosystem's EGF version active at the time of the act.

### 6.2 Corporations

- **[NGF-PART-3]** A corporation registered on the network MUST provide accurate registration information, MUST control the DID it registers, and MUST keep both current.
- **[NGF-PART-4]** A corporation that publishes Corporation Governance Framework (CGF) documents MUST ensure they are publicly resolvable per [NGF-EGF-3] and consistent with their on-chain digests.
- **[NGF-PART-5]** A corporation MUST use the network only for lawful purposes and MUST NOT write personal data to the network ([NGF-PRIN-7], [NGF-PRIN-10]).

### 6.3 Ecosystems and ecosystem governance authorities

- **[NGF-PART-6]** An entity that creates an ecosystem on the network and intends it to be relied upon MUST publish and maintain an EGF that satisfies chapter [NGF-EGF]. Creating an ecosystem requires no permission ([NGF-PRIN-3]); recognition of its EGF as conformant is governed by chapter [NGF-EGF].

### 6.4 Schema-tree participants

- **[NGF-PART-7]** A Participant (in any role of the VPR participant tree: `ECOSYSTEM`, `ISSUER_GRANTOR`, `VERIFIER_GRANTOR`, `ISSUER`, `VERIFIER`, `HOLDER`) MUST comply with the active EGF of the ecosystem in which it holds its permission, in addition to this framework.

### 6.5 Module operators

*This paragraph is non-normative.* Indexers, trust resolvers, graph services, and similar modules operate on data derived from the ledger and are permissionless: anyone may run them, without Council membership or approval.

- **[NGF-PART-8]** A module operator SHOULD serve ledger-derived data unmodified and unfiltered, and SHOULD disclose any transformation, caching latency, or filtering it applies.
- **[NGF-PART-9]** A service answering Trust Registry Query Protocol (TRQP) authorization queries against the network MUST apply the following collapse rule: `authorized: true` for a (authority, entity, action, resource) tuple if and only if the corresponding permission is in the `VALIDATED` state, within its validity period, not revoked, not ecosystem-slashed (an ecosystem-slashed permission is permanently non-authorized: repayment per MOD-PP-MSG-13 only enables the corporation to obtain a new permission, never revives the slashed one), and its corporation is not network-slashed with the slash unrepaid. The Council owns this definition; module operators do not define their own.
- **[NGF-PART-10]** A module operator SHOULD support reconstruction of permission state as of a given past time, to allow verification of authorizations at issuance time.

### 6.6 Accountability allocation and residual risk

- **[NGF-PART-11]** Each role answers only for its own function, and accountability does not delegate: an EGA answers for its EGF and its accreditation diligence, an onboarding validator for its validation diligence, an issuer for its issuance conduct, a network validator for its node. The Council answers for the efficacy and maintenance of this framework — not for the conduct of participants it does not control.
- **[NGF-PART-12]** A party MUST NOT represent on-chain permission state as a guarantee of off-chain conduct. On-chain state proves registration and permission status — verification-grade facts — never validation: whether data or a counterparty is acceptable for a purpose remains each relying party's own decision. Relying parties may infer less assurance than the registry provides, but not more.

## 7. Economic Rules of the Commons

### 7.1 Purposes

*This section is non-normative.* Before mechanisms, purposes. Trust deposits exist to make participation economically accountable: they deter abuse, keep departed participants answerable to the ecosystems they used, and sustain demand for the network's native token. Trust fees remunerate the work of validation, issuance, and verification. Agent rewards stimulate wallet and user-agent adoption. The exchange-rate mechanism exists so that fees can be denominated in a stable Trust Unit while settling in the native token. None of these mechanisms confers governance power ([NGF-PRIN-2]).

### 7.2 Trust deposits

- **[NGF-ECON-1]** Trust deposits are non-withdrawable by protocol design. The Council MUST NOT create, promise, or simulate any mechanism for withdrawing a trust deposit.
- **[NGF-ECON-2]** Trust deposits grow with usage at the rate `trust_deposit_rate` (Initial Parameter, Annex A) and yield block rewards per `trust_deposit_block_reward_share`, capped at `trust_deposit_max_yield_rate` (Initial Parameters, Annex A). Changes to these values are parameter changes under [NGF-ECON-10].
- **[NGF-ECON-3]** Slashed trust deposits — ecosystem-level (MOD-PP-MSG-12, burned via MOD-TD-MSG-7) and network-level (MOD-TD-MSG-5) — are burned, never paid to the sanctioning party or to any victim. The Council MUST NOT direct slashed value to any account ([NGF-PRIN-9]).
- **[NGF-ECON-13]** No economic position grants governance rights: neither a trust deposit, nor fee volume, nor any token holding converts into a vote or any other governance power ([NGF-PRIN-2]).

### 7.3 Fees

- **[NGF-ECON-4]** Network fees (chain execution fees) and trust fees (validation, issuance, and verification fees defined in Participant entries, in the schema's pricing asset) are distinct and MUST be presented distinctly in any Council communication about network costs.
- **[NGF-ECON-5]** Trust-fee amounts are set by ecosystems and their participants within the protocol's fee mechanics, not by the Council. The Council MUST NOT set, cap, or prescribe any ecosystem's fees.
- **[NGF-ECON-6]** Agent reward rates (`user_agent_reward_rate`, `wallet_user_agent_reward_rate`) are Initial Parameters (Annex A), changed only under [NGF-ECON-10].

### 7.4 Trust Unit and the exchange-rate mechanism

- **[NGF-ECON-7]** The creation of an exchange rate, the enabling or disabling of an exchange rate, and the granting or revocation of an exchange-rate authorization are exercisable only through governance proposals (MOD-XR-MSG-1, -3, -4, -5; see [NGF-POW-1]). Routine rate updates (MOD-XR-MSG-2) are performed by the operators so authorized.
- **[NGF-ECON-8]** Every exchange-rate authorization granted by the Council MUST identify the authorized operator on the public record and MUST set both protocol guardrails: `min_interval` (anti-spam minimum time between updates) and `max_deviation_bps` (circuit breaker on the relative change per update), at the initial values of Annex A.
- **[NGF-ECON-9]** A rate movement exceeding the circuit breaker MUST be effected only through a fresh governance proposal, per the VPR specification.

> **[DECISION]** Initial guardrail values proposed in Annex A: `min_interval` = 1 hour, `max_deviation_bps` = 1000 (10% per update). The VPR specification makes both optional per authorization; this document makes setting them mandatory. Alternative: leave them unset for launch-phase flexibility, at the cost of an unguarded oracle. Founding Members should confirm the values.

### 7.5 Parameter accountability

- **[NGF-ECON-10]** Every parameter change (any GlobalVariables value, any module parameter, any exchange-rate state or authorization) MUST (a) be adopted by governance proposal under [NGF-GOV-6], (b) be accompanied by a published written justification naming the trade-offs against the principles of chapter [NGF-PRIN], and (c) ship a human-readable description of the change and its expected effect.
- **[NGF-ECON-11]** The Council MUST conduct an open public review of all network parameters and exchange-rate state at least once per year, with the review's inputs and conclusions published.

### 7.6 Council funding

- **[NGF-ECON-12]** After mainnet launch, the Council's operations are funded by a protocol-defined on-chain allocation. The Council MUST publish an annual public accounting of this allocation and its use. Fees otherwise flow as the protocol defines; the Council MUST NOT treat network fee flows as discretionary revenue.

## 8. Requirements for Ecosystem Governance Frameworks

### 8.1 Scope and posture

- **[NGF-EGF-1]** This chapter applies to every EGF anchored on the Verana network. Conformance with this chapter is a **recognition criterion** — a property that relying parties, wallets, and the Council itself may check and rely on — and is never an approval gate: no EGF requires Council approval to exist, publish, or operate ([NGF-PRIN-3], [NGF-PRIN-4]).
- **[NGF-EGF-2]** An EGF MUST NOT contradict this Network Governance Framework. An EGF MAY tighten requirements of this framework within its own ecosystem; it MUST NOT loosen them.

### 8.2 Publication and durability

- **[NGF-EGF-3]** An EGF MUST be published on-chain as one or more `GovernanceFrameworkVersion` entries with `GovernanceFrameworkDocument` entries (language, `url`, `digest_sri`) per the VPR specification, and each document URL MUST be publicly resolvable without authentication, registration, or payment. The chain-anchored digest is canonical: where a web copy and the anchored digest disagree, the document matching the digest is the EGF.
- **[NGF-EGF-4]** An EGA MUST keep every version of its EGF that was ever active retrievable. Availability of issuance services may degrade; availability of governance documents, revocation state, and permission state must not.

### 8.3 Mandatory contents

- **[NGF-EGF-5]** An EGF MUST contain all of the following:

  1. **Identified EGA** — the legal name, legal jurisdiction, and a working contact channel of the ecosystem governance authority accountable for the EGF.
  2. **Scope** — the domain, credential schemas, and community the EGF governs.
  3. **Roles** — the roles it uses per credential schema, expressed in the VPR participant-tree vocabulary.
  4. **Onboarding requirements per role** — the criteria and process by which each role is granted, consistent with the schema's onboarding modes.
  5. **Sanctions ladder and appeal** — a graduated sanctions ladder with enumerated grounds, notice and cure mechanics, the on-chain acts that execute each rung, and an appeal path to a body other than the one that sanctioned.
  6. **Fee schedule** — the ecosystem's fees, or an explicit statement that there are none.
  7. **Privacy and data-handling commitments** — how the EGA and its participants handle personal data off-chain, and the ecosystem's data-protection posture.
  8. **Amendment process with notice** — how the EGF changes, including a public notice period before material changes take effect.
  9. **Layering clause** — an explicit statement that the EGF supplements and does not supersede this Network Governance Framework, and that on conflict this framework controls.
  10. **Issuer termination duties** — on an issuer's exit or termination, the duty to revoke its unexpired credentials, archive its issuance evidence, and destroy its issuance keys, with notification of affected holders.
  11. **Verified revocation requests** — enumerated grounds on which revocation may be requested, and a duty to verify the identity and standing of the requester before acting.
  12. **Revocation-availability asymmetry** — a commitment that, whatever service degradation occurs, revocation status and permission state remain available.
  13. **Lawful purpose** — a commitment that the ecosystem and its participants use the network only for lawful purposes.
  14. **Document-control metadata block** — the document name, version, status, the EGA it is governed by, and its license, with a change log whose rows correspond one-to-one with on-chain `GovernanceFrameworkVersion` activations.

- **[NGF-EGF-6]** An EGF MUST NOT require or cause personal data to be written to the network ([NGF-PRIN-7]).
- **[NGF-EGF-7]** An EGF MUST NOT state or imply that the ecosystem's creation, registration, or operation constitutes endorsement, approval, or accreditation by the Verana Council. Creation is not endorsement.
- **[NGF-EGF-8]** An EGF MUST NOT govern, or claim authority over, any ecosystem other than its own.

### 8.4 The Template EGF

- **[NGF-EGF-9]** The Council MUST maintain and publish the Template EGF as a voluntary scaffold whose completion yields an EGF satisfying this chapter by construction. Use of the Template EGF is OPTIONAL and implies no Council endorsement.

## 9. Network Validator Standards

### 9.1 Eligibility and duty

- **[NGF-VAL-1]** Only seated Members of the Council MAY operate a network validator node of the Verana network.
- **[NGF-VAL-2]** Every seated Member MUST operate a network validator node. Membership and validator operation are one status: Founding Member = Verein member = General Assembly voter = validator operator.
- **[NGF-VAL-3]** Before mainnet launch, a seated Member SHOULD operate a testnet validator node throughout the formation period and demonstrate testnet readiness per the criteria of the Technical / Validator Committee — the readiness step for the genesis validator set. A seated Member that has not demonstrated readiness at genesis retains its seat and vote, and MUST join the validator set upon demonstrating readiness, no later than 90 days (Initial Parameter) after mainnet launch; failure to join within that window is a breach of [NGF-VAL-2].

### 9.2 Operational duties

- **[NGF-VAL-4]** A Member MUST operate its node in conformance with the validator operations documentation published by the Council as a Controlled Document (owner: Technical / Validator Committee).
- **[NGF-VAL-5]** A Member MUST maintain node availability of at least the sanction floor of 95% over any 30-day window (Initial Parameter), and SHOULD target 99.5% (Initial Parameter). Aspiration and enforcement do not share one number: only the floor triggers the sanctions ladder.
- **[NGF-VAL-6]** A Member MUST keep its consensus key unique to a single running node at any time, MUST NOT operate two nodes signing with the same consensus key, and SHOULD protect consensus keys with an HSM or remote signer. Consensus keys, node-operator keys, and governance keys MUST be separate keys.
- **[NGF-VAL-7]** A Member MUST report any suspected compromise of its validator keys or infrastructure to the Council within 24 hours (Initial Parameter) of detection, and MUST report material incidents affecting its node's operation within 72 hours (Initial Parameter).
- **[NGF-VAL-8]** A Member MUST apply network software upgrades adopted under chapter [NGF-EVOL] within the upgrade window stated in the adopting proposal (default 14 days for non-emergency upgrades, Initial Parameter).

### 9.3 Delegated operation

- **[NGF-VAL-9]** A Member MAY contract the technical operation of its node to a third-party operator, provided the Member discloses the operator to the Council, the operator does not operate nodes for any other Member, and the Member remains fully and non-delegably responsible for every duty of this chapter.

> **[DECISION]** Delegated operation is permitted with non-delegable accountability (the Hedera pattern), because several target Members (governments, standards bodies) do not run datacenter operations in-house. The one-operator-per-Member restriction prevents an operator from becoming a de facto multi-seat validator cartel. Alternative: prohibit delegation entirely (stronger decentralization optics, materially smaller candidate pool). Founding Members should confirm.

### 9.4 Terms, renewal, and exit

- **[NGF-VAL-10]** Validator service runs in fixed terms of 3 years (Initial Parameter) with formal renewal by the Council. Renewal review evaluates the record of this chapter's duties.
- **[NGF-VAL-11]** A departing Member MUST cooperate in an orderly handover: announced exit date, continued operation until the announced date or a Council-agreed earlier date, and clean removal from the validator set without harming liveness. Where immediate departure is legally compelled, the Member MUST notify the Council without delay.

### 9.5 Protocol enforcement mapping

- **[NGF-VAL-12]** Automatic protocol penalties (jailing for downtime, tombstoning for double-signing, and similar consensus-level mechanisms) apply as implemented by the chain and are not Council sanctions. A jailing or tombstoning event MUST be reviewed under chapter [NGF-SANC] to determine whether a duty of this chapter was also breached; persistent or unremedied breach of this chapter is Cause.

## 10. Network-Level Sanctions

### 10.1 Scope and enumerated grounds

- **[NGF-SANC-1]** Network-level sanctions exist only for network-level violations. The exhaustive grounds are: (a) fraud against the network or its registries; (b) violation of this framework's requirements addressed to the sanctioned party; (c) violation of protocol-governance rules (including validator duties of chapter [NGF-VAL] where the party is a Member); and (d) unlawful use of the network. Conduct governed by an ecosystem's EGF is sanctioned by that ecosystem alone ([NGF-POW-11]).

### 10.2 The graduated ladder

- **[NGF-SANC-2]** Sanctions MUST proceed through a graduated ladder, applying the least severe rung adequate to the violation: (1) written warning; (2) remediation order with a day-counted cure period; (3) restriction of permissions or functions; (4) suspension; (5) revocation or termination (for Members: removal for Cause); (6) network-level trust-deposit slash (MOD-TD-MSG-5). A rung MAY be skipped only where written reasons establish that lesser measures cannot address the violation.
- **[NGF-SANC-3]** The default cure period for a remediation order is 30 days, reducible to 5 days for violations threatening network integrity (Initial Parameters).
- **[NGF-SANC-4]** Recidivism — a repeat of a violation of the same ground within 12 months (Initial Parameter) of a closed sanction — re-enters the ladder at the rung above the previously applied one.

### 10.3 Due process

- **[NGF-SANC-5]** Before any sanction beyond a written warning, the respondent MUST receive written notice citing the exact requirements alleged to be violated and the evidence, and MUST have the opportunity to respond within the cure period.
- **[NGF-SANC-6]** Sanction decisions MUST be adjudicated by a Sanctions Panel composed of all seated members that are (a) unconflicted with respect to the matter and (b) engaged (attended at least 2 of the last 3 Council meetings). The Panel is decision-capable only if at least 5 members qualify (Initial Parameter); otherwise it issues a written recommendation to the unconflicted remainder of the General Assembly, which decides.
- **[NGF-SANC-7]** Every sanction decision MUST be issued with written reasons and published on the public record ([NGF-GOV-2]). Reinstatements MUST be published with the same visibility as the sanction.

### 10.4 Execution

- **[NGF-SANC-8]** A network-level slash MUST be executed only by a governance proposal adopted under [NGF-GOV-6] (MOD-TD-MSG-5). The slashed amount is burned. While the slash is unrepaid, all permissions linked to the slashed corporation are non-trustable, per the VPR specification; repayment restores standing (repay-to-resume).
- **[NGF-SANC-9]** Sanction proceeds MUST NOT accrue to the Council, any Member, or any complainant ([NGF-PRIN-9]).

### 10.5 No limbo

- **[NGF-SANC-10]** A suspension not resolved within 180 days (Initial Parameter) automatically converts to the next ladder rung decision: the Sanctions Panel MUST, before the clock expires, either lift the suspension, extend it once with written reasons for at most 90 further days (Initial Parameter), or proceed to rung 5.
- **[NGF-SANC-11]** A permission or decision found procedurally defective is reviewable, not void: it MUST be reviewed and ratified, amended, or terminated as soon as reasonably practicable, so that voidness does not cascade through credential chains and harm innocent holders.

### 10.6 Appeal

- **[NGF-SANC-12]** A sanctioned party MUST have an appeal to a body other than the one that decided the sanction; the General Assembly (excluding conflicted members) is the final internal appeal instance. For network slashes, the appeal window (30 days, Initial Parameter) runs before execution of the slash except where delay threatens network integrity, in which case execution may precede appeal with written reasons.
- **[NGF-SANC-13]** Every sanction and appeal decision is subject to a decision deadline of 60 days (Initial Parameter) from complete referral; an undecided matter escalates automatically to the General Assembly ([NGF-GOV-12]).

### 10.7 Intake

- **[NGF-SANC-14]** The Council MUST maintain a public intake channel through which any person may report suspected network-level violations, and MUST publish aggregate intake statistics annually while keeping case details confidential until decision.

## 11. Dispute Resolution

### 11.1 Jurisdiction boundary

- **[NGF-DISP-1]** Disputes MUST be routed by subject matter as follows:

| Dispute | Forum |
| --- | --- |
| Conduct governed by an ecosystem's EGF (accreditation, ecosystem sanctions, ecosystem fees) | That ecosystem's EGA and its EGF's dispute process — never the Council |
| Network-level violations (chapter [NGF-SANC]) | Sanctions Panel → General Assembly appeal |
| Challenges to registry entries or Council registry operations | Challenge process of [NGF-DISP-2] |
| Association-law disputes (membership, statutes, liability) | General Assembly; then arbitration seated in Switzerland as the Statutes provide |
| Protocol-fact disputes (what the specs mean) | The VT/VPR specifications and their maintenance process at the Verana Foundation — not a Council decision |

### 11.2 Tiers

- **[NGF-DISP-2]** Any person MAY challenge the accuracy of a registry entry or Council governance act through the intake channel; the Council MUST respond within 30 days (Initial Parameter).
- **[NGF-DISP-3]** Disputes between parties subject to this framework MUST first be pursued in good-faith bilateral discussion for at least 30 days (Initial Parameter), then MAY be referred to mediation by a Council-designated mediator or committee (costs shared equally), before any escalation to the General Assembly or, for association-law matters, arbitration.
- **[NGF-DISP-4]** Every dispute-resolution stage carries the decision deadline and escalation path of [NGF-SANC-13]. Nothing in this chapter bars urgent provisional relief before a competent court, or any party's non-waivable statutory rights.

## 12. Chain Evolution

### 12.1 Upgrade adoption

- **[NGF-EVOL-1]** Adoption of any network software upgrade is a protocol-governance change: it MUST be approved under [NGF-GOV-6] and executed as an on-chain software-upgrade proposal (or, before mainnet, under the Provisional Governance Period rules).
- **[NGF-EVOL-2]** A non-emergency upgrade SHOULD be deployed and observed on the test network before mainnet adoption, and its adopting proposal MUST state the upgrade window for validators ([NGF-VAL-8]).

### 12.2 Release provenance

- **[NGF-EVOL-3]** The Verana Foundation hosts, stewards, and maintains the network's open-source software; the Council decides adoption. The Council MUST adopt only releases whose provenance is verifiable (published source, tagged release, published checksums or signatures), and MUST record the adopted release identity in the adopting proposal.

### 12.3 Emergency security patches

- **[NGF-EVOL-4]** Where a vulnerability threatens network integrity or user funds, the Council MAY adopt an emergency patch through a fast path: approval by ⅔ of seated members with the voting window shortened to no less than 48 hours (Initial Parameter), and deferred publication of vulnerability details until remediation is deployed.
- **[NGF-EVOL-5]** Every emergency act under [NGF-EVOL-4] MUST be submitted for retroactive ratification at the next ordinary Council vote, and no later than 30 days after the act (Initial Parameter), with full written reasons published at ratification. An emergency act not ratified by that deadline lapses; at the same vote the Council MUST adopt and schedule any reverting or replacing measure the lapse requires, with written reasons published.

> **[DECISION]** The emergency fast path keeps the full ⅔ threshold and shortens only the deliberation window (48 hours minimum), rather than lowering the threshold to a smaller emergency committee. Rationale: a lower threshold is the single most abusable clause in any constitution; a 25-member body can realistically clear ⅔ within 48 hours for a genuine emergency. Alternative: a security committee empowered to act with retroactive ratification, which is faster but concentrates power. Founding Members should confirm.

## 13. Amendment

### 13.1 Two tiers

- **[NGF-AMND-1]** This document amends on the constitutional tier; Controlled Documents under it amend on the legislative tier. Each Controlled Document MUST be listed in Annex B with a named owning body and a target date; a Controlled Document MUST NOT contradict this document.
- **[NGF-AMND-2]** Constitutional-tier amendments MUST respect the Purpose (chapter 1) and Principles (chapter [NGF-PRIN]) of this framework.

### 13.2 Procedure

- **[NGF-AMND-3]** Any seated Member MAY propose an amendment. Proposals MUST undergo a public comment period of at least 30 days (Initial Parameter), open to anyone, conducted in the public repository; the Council MUST publish a disposition of comments before the vote. The vote MUST be opened within 60 days (Initial Parameter) of the published disposition of comments, failing which the proposal lapses and MAY be re-filed.
- **[NGF-AMND-4]** Adoption of a constitutional-tier amendment requires a ⅔ vote under [NGF-GOV-6]. Adoption of a legislative-tier change requires the process stated in the Controlled Document, and in the absence of one, [NGF-GOV-6].
- **[NGF-AMND-5]** Once the network is live, every adopted version after the first MUST be published on-chain (MOD-GF-MSG-1) and activated (MOD-GF-MSG-2); the first version is anchored and auto-activated within the creation of the Council's Corporation entry ([NGF-TRAN-6]). For material changes, the new version's `active_since` MUST lie at least 30 days (Initial Parameter) after adoption. Editorial (non-material) corrections MAY activate without the notice runway, as a new version, never as an in-place edit: active versions are immutable by protocol.
- **[NGF-AMND-6]** The version history table of this document MUST correspond one-to-one with on-chain version activations once the network is live. Versions are sequential integers starting at 1 (drafts carry 0.x numbers); this paragraph is the framework's versioning policy.
- **[NGF-AMND-7]** The Council MUST review this framework at least annually, together with the parameter review of [NGF-ECON-11], and publish the review outcome even when no change is proposed.
- **[NGF-AMND-8]** Emergency amendments follow [NGF-EVOL-4] and [NGF-EVOL-5], applied to the document instead of software.

### 13.3 Invariants

- **[NGF-AMND-9]** The following invariants MUST NOT be amended except by a vote satisfying [NGF-GOV-6] in which the ⅔ threshold is computed over **all seated members with no reduction for recusal**, and any clause benefiting a specific Member is amendable only without that Member's vote: one member, one vote; the 25-seat cap; membership coupled to validator duty ([NGF-VAL-1], [NGF-VAL-2]); the Board's zero network authority ([NGF-GOV-5]); the enumerated-powers closure ([NGF-POW-3]); trust-deposit non-withdrawability ([NGF-ECON-1]); burned-not-paid ([NGF-ECON-3]); record symmetry ([NGF-GOV-2]); and this clause itself.

> **[DECISION]** The invariants clause entrenches the constitutional core behind the standard ⅔-of-all-seated-members threshold ([NGF-GOV-6], [NGF-GOV-7]) plus beneficiary exclusion, rather than a higher fraction (¾ or unanimity). Rationale: a small body should not be able to amend its own capture-resistance during a membership trough; unanimity would make honest evolution impossible. Founding Members should confirm the mechanism.

## 14. Transition and Provisional Governance

### 14.1 The Steward Period

*This paragraph is non-normative.* While the Council is in formation, 2060 OÜ holds a time-boxed stewardship: it covers the association's costs (legal drafting, incorporation, the council platform, secretariat), runs the candidacy pipeline (due diligence, opening admission ballots), designated the seed cohort of 3 with published rationale, and lists Observers.

- **[NGF-TRAN-1]** The steward's privileges are exactly those enumerated above and expire on event triggers, not dates: (a) the power to designate members directly ended upon the fourth candidacy — from candidate #4 onward every admission is decided solely by the ⅔ peer vote; (b) all pre-incorporation seatings and steward acts are ratified en bloc at the constitutive (Incorporation) General Assembly, and upon incorporation the power to list Observers passes from the steward to the Board; (c) the entire steward role terminates at mainnet launch. Upon each trigger, the corresponding privilege reverts automatically to the mechanism of this framework, with no further act or vote required.
- **[NGF-TRAN-2]** During the Steward Period, the steward MUST NOT vote other than as one seated Member among the others, and steward acts MUST be published on the public record like any governance act.

### 14.2 The Provisional Governance Period

- **[NGF-TRAN-3]** Before mainnet launch, Council voting — including admissions — is exercised off-chain: one ballot per candidate (accept/refuse, never head-to-head), asynchronous 14-day voting window (Initial Parameter), threshold and denominator per [NGF-GOV-6] to [NGF-GOV-10].
- **[NGF-TRAN-4]** The Provisional Governance Period ends at mainnet launch: from that moment all Council voting, admissions included, moves on-chain and is exercised via network validator nodes. This sunset is automatic and requires no vote.

### 14.3 Ratification and cutover

- **[NGF-TRAN-5]** This document is submitted for ratification at the Incorporation General Assembly (target Q4 2026), together with the en-bloc ratification of [NGF-TRAN-1](b).
- **[NGF-TRAN-6]** At mainnet launch: the genesis validator set consists of the seated Members that have demonstrated testnet readiness per [NGF-VAL-3], with not-yet-ready seated Members joining per the cure path of [NGF-VAL-3]; the genesis GlobalVariables are the values of Annex A; and the Council MUST anchor the then-current version of this document on-chain within the creation of its own Corporation entry (MOD-CO-MSG-1, whose mandatory v1 governance-framework document parameters carry this document's `url` and `digest_sri`), and the ECS-EGF within the creation of its Ecosystem entry (MOD-ES-MSG-1), as its first governance acts. Subsequent versions publish and activate via MOD-GF-MSG-1 and MOD-GF-MSG-2 ([NGF-AMND-5]).
- **[NGF-TRAN-7]** Any founding-era distinction (such as the "Founding Member" designation) is historical only and confers no right or power beyond those of any seated Member.

## 15. Annex A — Initial Parameters

*Normative.* Each parameter below is an Initial Parameter of this framework. On-chain parameters take these values at genesis and change only by governance proposal per [NGF-ECON-10]. Document parameters change by amendment of this document per chapter [NGF-AMND].

### A.1 Protocol GlobalVariables (VPR [GLO])

| Parameter | Initial value | Change process |
| --- | --- | --- |
| `credential_schema_schema_max_size` | 8192 | Governance proposal ([NGF-ECON-10]) |
| `credential_schema_issuer_grantor_validation_validity_period_max_days` | 3650 | Governance proposal ([NGF-ECON-10]) |
| `credential_schema_verifier_grantor_validation_validity_period_max_days` | 3650 | Governance proposal ([NGF-ECON-10]) |
| `credential_schema_issuer_validation_validity_period_max_days` | 3650 | Governance proposal ([NGF-ECON-10]) |
| `credential_schema_verifier_validation_validity_period_max_days` | 3650 | Governance proposal ([NGF-ECON-10]) |
| `credential_schema_holder_validation_validity_period_max_days` | 3650 | Governance proposal ([NGF-ECON-10]) |
| `trust_deposit_share_value` | 1 | Governance proposal ([NGF-ECON-10]) |
| `trust_deposit_rate` | 0.20 | Governance proposal ([NGF-ECON-10]) |
| `trust_deposit_max_yield_rate` | 0.20 | Governance proposal ([NGF-ECON-10]) |
| `trust_deposit_block_reward_share` | 0.20 | Governance proposal ([NGF-ECON-10]) |
| `wallet_user_agent_reward_rate` | 0.10 | Governance proposal ([NGF-ECON-10]) |
| `user_agent_reward_rate` | 0.10 | Governance proposal ([NGF-ECON-10]) |

### A.2 Exchange-rate authorization guardrails

| Parameter | Initial value | Change process |
| --- | --- | --- |
| `min_interval` (per authorization) | 1 hour | Governance proposal ([NGF-ECON-8]) |
| `max_deviation_bps` (per authorization) | 1000 (10%) | Governance proposal ([NGF-ECON-8]) |

### A.3 Governance process parameters

| Parameter | Requirement | Initial value | Change process |
| --- | --- | --- | --- |
| Asynchronous voting window | [NGF-GOV-9], [NGF-TRAN-3] | 14 days | Amendment ([NGF-AMND]) |
| Change-of-control disclosure period | [NGF-GOV-13] | 14 calendar days | Amendment ([NGF-AMND]) |
| Related-Party seat cap | [NGF-GOV-14] | 1 seat | Amendment ([NGF-AMND]) |
| Related-Party relinquishment negotiation window | [NGF-GOV-15] | 60 days | Amendment ([NGF-AMND]) |
| Public comment period (amendments) | [NGF-AMND-3] | 30 days | Amendment ([NGF-AMND]) |
| Vote-opening deadline after disposition of comments | [NGF-AMND-3] | 60 days | Amendment ([NGF-AMND]) |
| Notice runway before material-change activation | [NGF-AMND-5] | 30 days | Amendment ([NGF-AMND]) |
| Annual framework and parameter review | [NGF-AMND-7], [NGF-ECON-11] | yearly | Amendment ([NGF-AMND]) |

### A.4 Validator parameters

| Parameter | Requirement | Initial value | Change process |
| --- | --- | --- | --- |
| Genesis readiness cure window | [NGF-VAL-3] | 90 days | Amendment ([NGF-AMND]) |
| Availability sanction floor (30-day window) | [NGF-VAL-5] | 95% | Amendment ([NGF-AMND]) |
| Availability target | [NGF-VAL-5] | 99.5% | Amendment ([NGF-AMND]) |
| Key-compromise report clock | [NGF-VAL-7] | 24 hours | Amendment ([NGF-AMND]) |
| Material-incident report clock | [NGF-VAL-7] | 72 hours | Amendment ([NGF-AMND]) |
| Default upgrade window (non-emergency) | [NGF-VAL-8] | 14 days | Amendment ([NGF-AMND]) |
| Validator term | [NGF-VAL-10] | 3 years | Amendment ([NGF-AMND]) |

> **[DECISION]** Validator terms are set at 3 years with formal renewal (defs fixes "fixed validator terms with formal renewal" without a number; 3 years matches the Hedera minimum term and gives institutional members procurement-compatible planning horizons). Alternative: 2 years, favoring faster rotation. Founding Members should confirm.

### A.5 Sanctions and disputes parameters

| Parameter | Requirement | Initial value | Change process |
| --- | --- | --- | --- |
| Default cure period | [NGF-SANC-3] | 30 days | Amendment ([NGF-AMND]) |
| Accelerated cure period (network-integrity threats) | [NGF-SANC-3] | 5 days | Amendment ([NGF-AMND]) |
| Recidivism window | [NGF-SANC-4] | 12 months | Amendment ([NGF-AMND]) |
| Sanctions Panel activation threshold | [NGF-SANC-6] | 5 qualifying members | Amendment ([NGF-AMND]) |
| Suspension auto-resolution clock | [NGF-SANC-10] | 180 days (+ one 90-day extension) | Amendment ([NGF-AMND]) |
| Appeal window before slash execution | [NGF-SANC-12] | 30 days | Amendment ([NGF-AMND]) |
| Decision deadline (sanctions and disputes) | [NGF-SANC-13], [NGF-DISP-4] | 60 days | Amendment ([NGF-AMND]) |
| Registry challenge response deadline | [NGF-DISP-2] | 30 days | Amendment ([NGF-AMND]) |
| Bilateral negotiation period | [NGF-DISP-3] | 30 days | Amendment ([NGF-AMND]) |
| Emergency fast-path minimum voting window | [NGF-EVOL-4] | 48 hours | Amendment ([NGF-AMND]) |
| Retroactive ratification deadline | [NGF-EVOL-5] | 30 days | Amendment ([NGF-AMND]) |

## 16. Annex B — Schedule of Controlled Documents

*Normative as to the list.* Each Controlled Document of this framework is listed below with its owning body per [NGF-AMND-1]. The list is exhaustive: a document not listed here is not a Controlled Document of this framework until this annex is amended. Only documents the Council genuinely plans are listed.

| Controlled Document | Charter (one sentence) | Owner | Target |
| --- | --- | --- | --- |
| Validator operations documentation | The operational standards network validator nodes must conform to per [NGF-VAL-4] | Technical / Validator Committee | Before mainnet genesis |

## Version History

| Version | Date | Status | Summary |
| --- | --- | --- | --- |
| 0.1 | 2026-07-05 | Draft | First draft for co-authoring by Founding Members |
