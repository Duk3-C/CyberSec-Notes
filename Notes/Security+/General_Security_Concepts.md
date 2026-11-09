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


# AAA and IAM Concepts
---
AAA stands for **Authentication, Authorization, and Accounting**, and most Security+ identity items test whether you can keep the three apart.

**Identity and Access Management (IAM)** governs an account from creation to deletion. Examiners frame this as **JML**: Joiner, Mover, Leaver. A leaked credential is an authentication failure; access that lingers after a job change is a lifecycle failure.

**Authorization Models:**
    RBAC (Role-Based):
        Permissions come from job roles or groups
    ABAC (Attribute-Based):
        A policy engine evaluates multiple attributes
    MAC (Mandatory): 
        A central authority enforces labels and clearances
    DAC (Discretionary):
        The resource owner grants access
    Rule-Based:
        Access follows explicit, predefined rules

# Cryptography, Hashes, Signatures, PKI, and Cetificate Decision Rules 
---
A **Hash** is a one-way digest; you cannot decrypt it back to the original. Good hashes resist collisions (two inputs, same digests), which is why **MD5** and **SHA-1** are deprecated and **SHA-256** is preferred. For passwords, a plain fast hash is still wrong because attackers precompute rainbow tables.

**Public Key Infrastructure (PKI)** binds public keys to identities through signed certificates and a chain of trust.

## Scenario Walkthrough
A team publishes an installer and wants customers to confirm it is unaltered and genuinely theirs. A bare hash detects accidental change, but an attacker can post a new hash beside a tempered file. A **digital signature** is strongerl the team signs with its private key and customers verify with the public key via a trusted certificate, delivering integrity, authentication, and Non-Repudiation at once.

# Social Engineering Types and Clues 
---
- Phishing - Deceptive message sent broadly - Genereic email to many recipients
- Spear phishing - Phishing tailored to a person/team - Message references your roles or project
- Whaling - Spear phishing aimed at executives - Targets the CEO, CFO, or their assistant 
- Smishing - Lure delivered by SMS/text - urgent text with a link 
- Vishing - Voice-based deception - Phone call impersonating IT or a bank
- Pretexting - Fabricated backstory to build trust - Fake auditor, vendor, or help-desk story
- Baiting - Tempting object or offer - Free gift cards, a USB drive left in the lobby
- Tailgating / pigybacking - Following someone through a secure door - Person slips in behind a badge-holder
- Shoulder surfing - Observing secrets in person - Watching a PIN or password entry
- Dumpster diving - Searching trash for information - Printed records discarded uncut
- Watering hole - Compromising a site the target trusts - Industry portal servers malware to visitors
- Pharming / typosquatting - Redirect or look-alike domain - DNS poisoning or misspeled URL
- Impersonation / brand Impersonation - Posing as a trusted person or brand - Logo and tone mimic a known company

# Supply Chain and Insider Threat Scenarios
---
Supply Chain risk comes from relationships an organization already trusts. Rather than attacking a hardened target directly, an actor compromises a vendor, managed service provider (MSP), software dependency, build system, update channel, contractor, or hardware source because that path is softer and the malicious payload arrives wrapped in trust.

A **software bill of materials (SBOM)** is the ***SYO-701*** answer when a question asks how to know exactly which components and versions ship inside a product, which is essential for responding fast to a dependency disclosure.

## The Three Insider Types 
- Malicious Insider - Intentionally misuses access | Example: Copies source code before resigning
- Negligent Insider - Creates risk through carelessness | Example: Uploads restricted date to personal cloud
- Compromised Insider - Account controlled by an attacker | Example: Valid VPN login from an impossible-travel location
- Privileged Insider - Elevated access, broad blast radius | Example: Admin disables logs before exfiltrating data 

The deciding clue is **trusted access**, not motive. A negligent insider intends no harm yet can cause a breach, while a compromised insider is technically an outsider operating through a legitimate account.

# Threats, Vulnerabilities, and Mitigations - Attacks 
---

## Malware Behaviors and Indicators

**Fileless Malware** is a high-yield topic: it lives in memory and abuses trusted signed binaries (a technique called living-off-the-land) so traditional signature antivirus sees little. PowerShell with an encoded `-enc` command line, `wmic`, `mshta`, and `rundll32` are classic indicators. The behavior, not the file, is the giveaway.

**Observed Behavior and What it Suggests**
- Mass file encryption with extension renames - Ransomware or destructive wiper
- Credential access from LSASS memory or browser stores - Infostealer or post-exploitation tool
- New scheduled task or Run-key registry value - Persistence mechanism
- PowerShell downloading and decoding content - Fileless / Staged payload
- DNS queries to a random-looking domain every 60 seconds - Commands-and-control beaconing
- Lateral movement using admin shares (C, ADMIN) - Compromised privileged credentials

## Persistence and Stealth Mechanisms

Beyond the initial infection, exam scenarios test how malware stays. Persistence keeps the malware running accross reboots and logoffs, while stealth hides it from defenders. Recognizing these mechanisms in a description lets you classify the threat and choose eradication and actually removes it rather than just killing a single process.

A **Potentially Unwanted Program (PUP)** is a softer category - adware or bundled toolbars that are not overtly malicious but degrade the system and may track users. The exam contrasts PUPs with true malware to test whether you over-escalate a low-severity finding.

## Distinguishing Authentication Attacks Patterns

Attack  |   Pattern     |   Best Clue 
Brute Force |   Many guesses against one account or service |   High failed-attempt count for a single username
Password spraying   |   One or a few common passwords accross many users    |   Low failures per user, many usernames affected
Credential stuffing |   Reused breached username/password pairs |   Successful logins from residential proxies or odd geos
Dictionary Attack   |   Wordlist plus mutations |   Common words and leetspeak variants
Rainbow table   |   Precomputed unsalted-hash lookup    |   Stolen unsalted hashes cracked instantly

