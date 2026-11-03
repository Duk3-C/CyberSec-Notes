# CIA and Non-Repudiation
---
**The CIA Triad (Confidentiality, Integrity, and Availability)**
    Confidentiality - protects against unauthorized disclosure.
    Integrity - protects against uanuthorized or unexpected change.
    Availability - protects against loss of access or service

Non-Repudiation is the assurance that a party cannot later deny having performed an action; critical for contracts, financial approvals, and forensic accountability. This concepts is grouped with the Triad on SY0-701 even though it is not strictly part of the CIA.

## Scenario Classification:

- A contractor downloads customer records from a folder they should not access = Confidentiality because data was disclosed to an unauthorized party.
- A payment file hash does not match the known-good value = Integrity because evidence suggests unauthorized or accidental modification.
- A DDoS attack prevents customers from reaching a portal = Availability because the service cannot be used when needed.
- A manager disputes approving a high-risk firewall exception = Non-Repudiation because the business needs reliable proof of who approved the action.

An Audit log supports Non-Repudiation only if the identity and the log's integrity are trustworthy. A shared admin account with editable local logs is weak evidence; a named account with multi-factor authentication (MFA), centralized append-only logging, synchronized time, and ticketed approval is strong evidence.
