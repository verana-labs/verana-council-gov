# Template CGF

> **Status:** `DRAFT 0.1` — first draft for co-authoring by Founding Members.

📄 **[Read the Template CGF](./template-cgf.md)**

The document at the root of this directory is always the current working
draft; previous drafts will be archived in versioned subdirectories.

A **scaffold, not a gate.** Every organization that acts on the Verana
network does so through a Corporation entry on the VPR, and Create New
Corporation requires the URL and digest of a version-1 **Corporation
Governance Framework (CGF)** at creation. Anyone can register a Corporation
with no Council approval, and using this template implies no Council
endorsement. The Template CGF is a working scaffold the Council maintains to
make authoring that document cheap, consistent, and conformant with the
[Network GF](../network-gf/) **by construction**.

A CGF is not an EGF. The [Template EGF](../template-egf/) governs an
*ecosystem* (schemas, roles, onboarding, sanctions). A CGF governs the
*organization behind a Corporation entry*: who it is, how it decides, who may
sign for it, how it protects its keys and deposits, and what happens when it
changes or disappears. Most corporations on Verana (issuers, verifiers,
grantors in ecosystems run by others) need only the **short form** described
in section 1.1.

The authoring guidance is integrated into the template itself (the
three-mode convention: suggested text, ⟨fill-in fields⟩, and *Instruction*
blocks to delete before publication) — there is no separate authoring guide.

## What it provides

- **Identity and accountability** — the registered organization, one legal
  entity per Corporation entry, DID lifecycle and rotation.
- **Decision-making mirror** — the Corporation's `x/group` members (by
  function), weights, and decision policy, with the off-chain authorization
  that governs votes and the acts reserved to the group.
- **Operator and delegation policy** — operator and VS operator
  authorizations as the authoritative list, scoped message types,
  expiration, spend limits, fee grants, revocation deadlines.
- **Keys, incidents, deposits, wind-down** — compromise procedures, slash
  repay-or-contest decisions, continuity and document retention.
- **Publication instructions** — the exact VPR message sequence: Create New
  Corporation with the version-1 CGF, operator grants, later versions
  through the Governance Framework module.

The Council's own Corporation entry anchors the Network GF itself as its
version-1 CGF document ([NGF-TRAN-6]).

## Version history

| Version | Date | Status | Summary |
| --- | --- | --- | --- |
| DRAFT 0.1 | 2026-10-14 | Draft | First draft for co-authoring by Founding Members, written against VPR specification v5 (draft). |

## License

[CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
