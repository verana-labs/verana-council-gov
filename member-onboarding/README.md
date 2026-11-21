# Verana Council: Member Onboarding Sheet

> **Status:** informative summary, November 2026. Figures are Initial
> Parameters of the [Network Governance Framework](../network-gf/network-governance-framework.md)
> (DRAFT 0.4, written against version 5 of the Verifiable Public Registry
> specification) and become final when the Incorporation General Assembly
> ratifies the framework. Where this sheet and a governance document differ,
> the governance document prevails.

A one-page summary for an organization considering a Founding Member seat:
what the seat means, what it asks of the organization, how the network pays
for itself, and the steps to take it.

**[Download the one-page PDF](./member-onboarding-sheet.pdf)** (source:
[`member-onboarding-sheet.html`](./member-onboarding-sheet.html)).

References in brackets point to requirements of the Network Governance
Framework.

## At a glance

| | |
| --- | --- |
| One status | One seat, one vote, one validator node |
| Size | 25 seats maximum |
| Cost of membership | Free, no dues |
| Commitment starts | Mainnet, Q1 2027 |

## The role

- The Council is the only body that governs and secures the live Verana
  network. It is separate from the Verana Foundation, which holds the
  specifications, the open-source software and the token (section 3.1).
- Each member holds one seat and one vote and operates one validator node
  ([NGF-VAL-1], [NGF-VAL-2]). Seats span sectors and regions.
- Members decide by a two-thirds majority of seated members ([NGF-GOV-6]):
  the governance frameworks, network parameters and budgets, software
  upgrades, network-level sanctions and admissions ([NGF-POW-1], [NGF-POW-2]).
- The Council does not write standards, sell products, give grants, issue the
  token or govern other ecosystems ([NGF-POW-5] to [NGF-POW-9]).

## What your organization receives

- A vote on the rules of an open public trust infrastructure, with
  governments, standards bodies, enterprises and academia.
- Free membership: no dues, no capital contribution, and no liability for the
  association's debts (section 3.1; Art. 75a ZGB).
- After launch, a node budget sized to cover the cost of running the
  validator (see [Budget and distribution](#budget-and-distribution)).
- A complimentary Verana Foundation Associate Membership.

## What a seat does not carry

- No token allocation, no revenue share, no economic claim of any kind
  ([NGF-GOV-19]). Token holdings give no vote ([NGF-ECON-13]).
- No extra power for Board members: the Board holds no network authority
  ([NGF-GOV-5]).

## Obligations of a member

| When | Obligation | Reference |
| --- | --- | --- |
| Formation | Co-author the governance frameworks. Vote in 14-day asynchronous ballots. Run a testnet validator node (recommended) to be ready for genesis. | [NGF-TRAN-3], [NGF-VAL-3] |
| From mainnet | Operate one validator node. This is mandatory: votes are cast through it. A member not ready at launch keeps its seat and joins within 90 days. | [NGF-VAL-2], [NGF-VAL-3] |
| Operations | Availability of at least 95% over any 30 days (target 99.5%). Adopted upgrades applied within 14 days. Keys kept separate and in the member's own custody. | [NGF-VAL-5], [NGF-VAL-6], [NGF-VAL-8] |
| Reporting | Suspected key compromise within 24 hours. Material incident within 72 hours. Change of hosting or operator within 5 business days. Change of control within 14 days. | [NGF-VAL-7], [NGF-VAL-15], [NGF-GOV-13] |
| People | One voting representative. Two emergency governance contacts able to vote on an urgent security proposal, reachable at all times, tested quarterly. | [NGF-VAL-17] |
| Node | AGPL-3.0-or-later software; modified builds publish their source. Own data center, colocation or cloud, disclosed publicly. A contracted operator is allowed; the member stays fully accountable. | [NGF-VAL-9], [NGF-VAL-13] to [NGF-VAL-15] |
| Conduct | Statutes and Code of Conduct. Recusal on conflicts of interest. One seat per corporate group. Seatings, votes and departures are public. | [NGF-GOV-2], [NGF-GOV-7], [NGF-GOV-14] |
| Term and exit | 3-year terms with formal renewal. Orderly handover on departure. Breaches follow a graduated ladder, from warning to removal for cause, with due process and appeal. | [NGF-VAL-10], [NGF-VAL-11], [NGF-SANC-2] |

## Budget and distribution

Every fee paid on the network enters a single pool. Once a day the protocol
pays the pool out in a fixed order ([NGF-ECON-18]; Verifiable Public Registry
specification v5, [DIST-1]):

| # | Line | What it is |
| --- | --- | --- |
| 1 | Validator node budgets | The same amount for every active node, reduced when uptime is low |
| 2 | Council budget | Runs the association; accounts published every year ([NGF-ECON-12]) |
| 3 | Foundation budget | Paid to the Foundation's treasury |
| 4 | Yield on bonded tokens | Capped; not active at launch |
| 5 | Remainder | Burned, never redistributed |

- **What a member is paid.** The node budget is a cost target set in fiat
  currency and paid in the native token (VNA) at the oracle rate. It is paid
  in full when the node signs at least 99% of the day's blocks, pro-rated
  below that, and not paid under 90% (Annex A.1: `validator_node_budget`,
  `validator_target_uptime`, `validator_min_uptime`).
- **Who sets the amounts.** The budgets are set at genesis, then changed only
  by a two-thirds Council vote with a published justification
  ([NGF-ECON-10]), and reviewed in public every year ([NGF-ECON-11]). The
  amounts are not set yet.
- **No new tokens.** Supply is fixed at 1 billion VNA and only shrinks. While
  fees are below the budgets, nodes are paid first and the shortfall comes
  from the founding treasuries and vesting grants (section 7.6).

The payment thresholds above are separate from the availability duty of
[NGF-VAL-5]: a low-uptime day reduces that day's payment, while the 95% floor
over 30 days is what opens the sanctions ladder.

## Onboarding checklist

- [ ] 1. Name an internal sponsor and confirm who can represent the
  organization.
- [ ] 2. Submit the non-binding expression of interest on
  [veranacouncil.org](https://veranacouncil.org/join) (sector and region).
  Nothing is signed yet.
- [ ] 3. Vetting by the Membership & Seats Committee.
- [ ] 4. Admission ballot: two-thirds of seated members, 14 days
  ([NGF-TRAN-3]). The first three seats are designated by the steward
  ([NGF-TRAN-1]).
- [ ] 5. Legal review of the Council Membership Agreement, the single binding
  document, then authorized signature.
- [ ] 6. Designate the voting representative and the two emergency governance
  contacts.
- [ ] 7. Choose own hosting or an operator, then start a testnet validator
  node (4+ CPU cores, 32 GB RAM, 1 TB SSD, static IP).
- [ ] 8. Join the framework co-authoring and the Incorporation General
  Assembly, which ratifies all seatings ([NGF-TRAN-5]).

## Other track

Sovereigns and multilateral bodies that cannot join a Swiss association may
take part as Public-Sector Observers: voice, no vote, no validator.

## Maintaining this sheet

The PDF is printed from `member-onboarding-sheet.html` with a headless
Chromium (A4, no header or footer). This README and the HTML carry the same
content; change both together, and update them whenever an Initial Parameter
they quote changes in the Network Governance Framework.

## License

[CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
