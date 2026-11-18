# Security+ Study Guide

This file contains practice questions and answers for the CompTIA Security+ exam.

## Questions

### Question 1: Securing LDAP Directory Service

**Question**: An educational institution's systems administrator is responsible for securing the LDAP directory service for the organization's computing resources. Which authentication method should the systems administrator implement to ensure secure access while minimizing opening extra ports on the firewall?

A. It requires no authentication method
B. Lightweight Directory Access Protocol Secure
C. Simple Authentication and Security Layer
D. Simple Bind authentication method

**Answer**: B

**Explanation**: LDAPS (Lightweight Directory Access Protocol Secure) wraps LDAP in SSL/TLS, encrypting directory traffic and protecting credentials. SASL is an authentication framework, Simple Bind can transmit credentials in cleartext, and no authentication provides no security. LDAPS is the standard method for securing LDAP directory access.

**Answer**: **B** - Lightweight Directory Access Protocol Secure

### Question 2: System Reliability Metrics

**Question**: A company is reviewing its system reliability metrics. It needs to know the average time the system operates without failure and the average time it takes to repair a system when it fails. Which of the following pairs of metrics should the company focus on to meet its needs?

A. Risk assessment and risk analysis
B. Mean Time Between Failures (MTBF) and Mean Time to Repair (MTTR)
C. Recovery Time Objective (RTO) and Recovery Point Objective (RPO)
D. Risk tolerance and risk appetite

**Answer**: B

**Explanation**: MTBF is the average time a system operates between failures, and MTTR is the average time required to repair it. RTO and RPO are business continuity metrics, while the remaining options are risk management concepts rather than reliability metrics.

**Answer**: **B** - Mean Time Between Failures (MTBF) and Mean Time to Repair (MTTR)

### Question 3: IT Framework Design for Digital Services

**Question**: A systems engineer is architecting a new IT framework for a business offering a widely utilized digital service. The business mandates uninterrupted and efficient communication for the service. Which elements should take priority in the engineer's design considerations? (Select the two best options.)

A. Generators
B. Replication
C. Load balancing
D. Clustering

**Answer**: C and D

**Explanation**: Load balancing distributes traffic across servers to prevent overload, and clustering provides high availability through failover. Generators address power continuity, and replication protects data copies but does not directly provide real-time traffic distribution or service failover.

**Answer**: **C and D** - Load balancing and Clustering

### Question 4: Risk Analysis Methodologies

**Question**: A cybersecurity consultant is analyzing risks for a new e-commerce website. The consultant identifies potential risks, evaluates their impact and likelihood, and considers the organization's ability to mitigate them. Which risk analysis or assessment methodology is the consultant MOST likely using?

A. Ad hoc risk assessments
B. Qualitative and quantitative risk analysis
C. Qualitative risk analysis
D. Quantitative risk analysis

**Answer**: B

**Explanation**: The consultant combines qualitative evaluation of impact and likelihood with quantitative cost-benefit analysis of mitigation options. Ad hoc assessments are unstructured, and neither qualitative nor quantitative analysis alone covers the full process described.

**Answer**: **B** - Qualitative and quantitative risk analysis

### Question 5: Security Control Device Failure Modes

**Question**: As a financial institution implementing a new security control device to protect its network infrastructure, it wants to ensure that in the event of a failure, the confidentiality and integrity of its financial data take precedence over system availability. What should the financial institution set as the failure mode configuration for this security control device?

A. The security control device should be configured to actively monitor the network.
B. The security control device should be configured to fail-closed.
C. The security control device should be configured to passively monitor the network.
D. The security control device should be configured to fail-open.

**Answer**: B

**Explanation**: Fail-closed (fail-secure) blocks traffic when the device fails, preserving confidentiality and integrity. Fail-open prioritizes availability and would expose the network. Active versus passive monitoring describes inspection behavior, not failure behavior.

**Answer**: **B** - The security control device should be configured to fail-closed

### Question 6: Processor Vulnerabilities

**Question**: A cyber consultant inspects a corporate desktop after receiving numerous complaints. What type of vulnerability can include instances where processors inside the computer allow malicious programs to steal data during processing?

A. Firmware
B. Virtualization
C. Legacy
D. End-of-life

**Answer**: A

**Explanation**: Firmware-level processor vulnerabilities such as Spectre and Meltdown exploit speculative execution to leak data during processing. Virtualization, legacy, and end-of-life describe other technologies or lifecycle categories, not this processor-level vulnerability class.

**Answer**: **A** - Firmware

### Question 7: Password Manager Advantages

**Question**: A system administrator at a medium-sized agency is working on improving the agency's password management practices to enhance security. The admin wants to provide employees with efficient and secure ways to manage their passwords. As part of the implementation plan, the admin examines different password managers available in the market, each with unique features and capabilities. Which of the following are the advantages of using password managers for password management? (Select the two best options.)

A. Password managers can securely store and organize passwords for various online accounts and services.
B. Password managers can generate strong and complex passwords automatically, reducing the risk of weak passwords.
C. Password managers automatically use the same strong password for all stored accounts to reduce the complexity for users.
D. Password managers automatically synchronize passwords across competitors' platforms to ensure seamless transition.

**Answer**: A and B

**Explanation**: Password managers provide an encrypted vault for storing and organizing credentials and can generate unique, strong passwords. Reusing one password across accounts is insecure, and synchronization applies to the user's own devices, not competitors' platforms.

**Answer**: **A and B** - Password managers can securely store and organize passwords for various online accounts and services, and Password managers can generate strong and complex passwords automatically, reducing the risk of weak passwords.

### Question 8: Cloud Service Contract Audit Clauses

**Question**: The IT department of a local governmental agency is in the process of finalizing a contract with a third-party vendor to provide cloud services. The agency is highly concerned about data security and wants to ensure it can assess the vendor's security practices. The IT team decides to include a right-to-audit clause in the contract to ensure periodic audits of the vendor's security measures. Additionally, the agency wants an independent assessment of the vendor's security controls to ensure unbiased evaluation. Which of the following accurately concludes the primary purpose of including a right-to-audit clause and seeking independent assessments in the contract with the cloud service vendor?

A. To ensure the company can periodically assess the vendor's security practices
B. To exempt the vendor from security compliance requirements
C. To provide the vendor with access to sensitive customer data
D. To grant the vendor the right to conduct audits on the company's internal systems

**Answer**: A

**Explanation**: A right-to-audit clause gives the agency the contractual right to review the vendor's security controls, and independent assessments provide unbiased verification. The clause does not exempt compliance, grant the vendor access to sensitive data, or give the vendor audit rights over the agency.

**Answer**: **A** - To ensure the company can periodically assess the vendor's security practices

### Question 9: Enterprise Port Security

**Question**: The network administrator in an organization is reinforcing the security measures of the company's enterprise infrastructure, with a key focus on port security. In an environment with dynamic port usage where different applications request ports on an ad-hoc basis, the administrator must consider the most secure method of assigning and managing these ports to mitigate security risks. To secure the enterprise infrastructure optimally, what key measure should the network administrator prioritize in terms of port security?

A. Keeping all ports open to ensure application functionality
B. Implementing a dynamic port allocation and management system
C. Assigning all applications a static port number
D. Blocking all incoming and outgoing connections on all ports

**Answer**: B

**Explanation**: Dynamic port allocation with management, logging, and oversight balances application flexibility with security. Keeping all ports open creates excessive exposure, static assignment is impractical for ad-hoc requests, and blocking all traffic breaks business operations.

**Answer**: **B** - Implementing a dynamic port allocation and management system

### Question 10: RADIUS Authentication Protocols

**Question**: The IT team of a medium-sized governmental agency took significant steps to bolster the security of their remote access services. Determined to fortify the authentication process for remote users, the team decided to implement Remote Authentication Dial-In User Service (RADIUS). However, relying solely on RADIUS may not be enough to achieve their rock-solid remote access solution goal. To ensure the utmost protection, the team evaluated different authentication protocols that can complement and work seamlessly with RADIUS. What authentication protocols should the team use to complement RADIUS for the company's remote access solution?

A. Protected Extensible Authentication Protocol (PEAP)
B. Password Authentication Protocol (PAP)
C. Address Resolution Protocol (ARP)
D. Wired Equivalent Privacy (WEP)

**Answer**: A

**Explanation**: PEAP creates a TLS tunnel that protects the authentication exchange with RADIUS. PAP transmits passwords in cleartext, ARP is not an authentication protocol, and WEP is an obsolete and insecure wireless protocol.

**Answer**: **A** - Protected Extensible Authentication Protocol (PEAP)

### Question 11: Software Agreement Compliance

**Question**: A cyber technician purchases new software to monitor employee computer usage after the company announces a new work-from-home program. Which risks could lead to noncompliance with software agreements? (Select the three best options.)

A. Unauthorized sharing or usage
B. Liability for damages caused by data loss
C. Modifying code or distributing software
D. Exceeding permitted installations

**Answer**: A, C, and D

**Explanation**: Unauthorized sharing, modifying or distributing code, and exceeding licensed installations all violate software agreements. Liability for data loss is a consequence of a risk event, not a software licensing compliance violation.

**Answer**: **A, C, and D** - Unauthorized sharing or usage, Modifying code or distributing software, and Exceeding permitted installations

### Question 12: Defense-in-Depth Technical Controls

**Question**: As part of enhancing its data protection strategy, a corporation's IT manager aims to ensure defense-in-depth by integrating a technical control alongside existing managerial and operational controls. Which measure BEST exemplifies a technical security control according to the classification scheme?

A. Conducting employee cybersecurity training
B. Implementing a risk identification tool
C. Installing a building access control system
D. Setting up a network intrusion detection system

**Answer**: D

**Explanation**: A network intrusion detection system is a technology-based logical control. Training and risk identification are managerial activities, and building access control is a physical control.

**Answer**: **D** - Setting up a network intrusion detection system

### Question 13: Compliance Monitoring

**Question**: After failing a regulatory exam on compliance, an organization looks for methods to systematically assess, evaluate, and report its adherence to laws, regulations, and industry standards. What is a true statement regarding compliance monitoring?

A. Compliance monitoring involves risk assessments, data collection, and analysis.
B. Compliance monitoring facilitates stakeholder communication and decision-making.
C. Compliance monitoring provides high-level summaries of an organization's compliance performance.
D. Compliance monitoring focuses on operational details and supports internal decision-making.

**Answer**: A

**Explanation**: Compliance monitoring is built on risk assessments, data collection, and analysis. Stakeholder communication, high-level summaries, and operational details are benefits or aspects of monitoring, not its core definition.

**Answer**: **A** - Compliance monitoring involves risk assessments, data collection, and analysis

### Question 14: Media Destruction Concepts

**Question**: When cleaning out the server closet, a company discovers a box of old disk drives. When considering which disposal method to use, what are the characteristics associated with the destruction concept? (Select the best two options.)

A. It refers to removing sensitive information from storage media to prevent unauthorized access or data breaches.
B. It involves the physical or electronic elimination of information stored on media, rendering it inaccessible and irrecoverable.
C. Its methods include shredding, crushing, or incinerating storage devices.
D. Its process uses specialized techniques, such as data wiping, degaussing, or encryption.

**Answer**: B and C

**Explanation**: Destruction permanently eliminates data and media through methods such as shredding, crushing, or incineration. Removing data or using wiping, degaussing, and encryption describes sanitization, not destruction.

**Answer**: **B and C** - It involves the physical or electronic elimination of information stored on media, rendering it inaccessible and irrecoverable. Its methods include shredding, crushing, or incinerating storage devices.

### Question 15: Network Segmentation for Containment

**Question**: Upon reviewing the results of an organizational assessment, the cyber team implements various remediation practices to safeguard the company's data. What remediation practices include the division of a network into separate pieces to contain an attack or attempted breach within one piece of the network?

A. Segmentation
B. Insurance
C. Patching
D. Compensating controls

**Answer**: A

**Explanation**: Segmentation divides the network into isolated segments, limiting lateral movement and containing a breach. Insurance transfers financial risk, patching fixes vulnerabilities, and compensating controls are alternative safeguards.

**Answer**: **A** - Segmentation

### Question 16: Cryptographic Techniques

**Question**: A tech company tasked a security analyst with improving the overall security posture of its systems to protect against various types of attacks. The analyst implemented a combination of cryptographic techniques, including key stretching, key exchange, and obfuscation. Given the scenario above, which of the following correctly describes why the security analyst would implement these techniques? (Select the three best options.)

A. Key exchange allows for the secure sharing of cryptographic keys over an insecure network.
B. Obfuscation encrypts individual files, making them unreadable without the correct key.
C. Obfuscation makes the system's operation harder to comprehend, making it more difficult for an attacker to exploit.
D. Key stretching increases the computational effort to crack a password through brute-force attacks.

**Answer**: A, C, and D

**Explanation**: Key exchange secures key distribution over untrusted networks, obfuscation makes code or system operation harder to understand, and key stretching slows brute-force attacks. Obfuscation does not encrypt files or use a decryption key.

**Answer**: **A, C, and D** - Key exchange allows for the secure sharing of cryptographic keys over an insecure network. Obfuscation makes the system's operation harder to comprehend, making it more difficult for an attacker to exploit. Key stretching increases the computational effort to crack a password through brute-force attacks.

### Question 17: Addressing Computational Demands

**Question**: The data processing department of a company is struggling to handle increasing computational demands due to business growth. What approach could they consider to address this issue effectively?

A. Implementing scalable architecture
B. Introducing microservices
C. Establishing a third-party vendor partnership
D. Adopting an air-gapped system

**Answer**: A

**Explanation**: Scalable architecture allows resources to grow horizontally or vertically as demand increases. Microservices are an application design pattern, vendor partnerships are indirect, and air-gapping is a security isolation measure that does not add capacity.

**Answer**: **A** - Implementing scalable architecture

### Question 18: Physical Attack Identification

**Question**: An organization observes several computer systems in a secured area showing signs of damage, having various cables disconnected, or hardware component tampering. Which type of attack is likely responsible for these issues?

A. Insider threats
B. Physical attacks
C. Malware attacks
D. Denial-of-service attacks

**Answer**: B

**Explanation**: Damaged hardware, disconnected cables, and tampered components are indicators of physical attacks. Insider threats are a broader category, malware operates logically, and denial-of-service attacks affect availability without physical damage.

**Answer**: **B** - Physical attacks

### Question 19: Unauthorized Device Connection to Network Ports

**Question**: Which of the following involves threat actors attaching unauthorized devices to a physical network port, allowing them to eavesdrop on network traffic, intercept and modify data, run spoofed services and applications, or execute exploit code against other hosts?

A. Lack of availability
B. Lack of authentication
C. Lack of confidentiality
D. Lack of integrity

**Answer**: B

**Explanation**: The root enabler is the lack of port authentication, such as missing 802.1X controls, which allows unauthorized devices to connect. Eavesdropping, data modification, spoofing, and code execution are consequences of that initial access.

**Answer**: **B** - Lack of authentication

### Question 20: Dynamic Security Testing and Static Source Code Analysis

**Question**: A security analyst evaluates a software application's codebase to detect potential security vulnerabilities. The analyst performs dynamic security testing and static source code analysis to understand potential threats comprehensively. When conducting dynamic security testing and static source code analysis, the analyst typically performs which activities? (Select the two best options.)

A. Analyzing run-time behavior of applications
B. Installing updates on network routers
C. Configuring firewall rules
D. Reviewing code for hard-coded credentials

**Answer**: A and D

**Explanation**: Dynamic testing analyzes application behavior during execution, while static analysis reviews source code without running it and can uncover hard-coded credentials. Router updates and firewall configuration are network administration tasks.

**Answer**: **A and D** - Analyzing run-time behavior of applications and Reviewing code for hard-coded credentials

### Question 21: Context-Aware Authentication

**Question**: A large multinational company wants to enhance the security of its computing resources. It considers applying common security techniques to protect sensitive data and prevent unauthorized access. Which security technique would be MOST suitable for securing computing resources?

A. Add geofencing to create a virtual boundary around the company's office premises
B. GPS tagging to add geographical identification metadata to a company's sensitive files
C. Indoor Positioning System to determine the physical position of employees' devices
D. Applying context-aware authentication to restrict resource access based on user location

**Answer**: D

**Explanation**: Context-aware authentication evaluates location and other contextual factors to make dynamic access decisions. Geofencing, GPS tagging, and indoor positioning provide location data but do not themselves control access to computing resources.

**Answer**: **D** - Applying context-aware authentication to restrict resource access based on user location

### Question 22: Cloud Service SLA Evaluation

**Question**: A large multinational company is in the process of selecting a new cloud service provider to meet its expanding data storage needs. The team has identified four potential vendors offering various features, pricing models, and service level agreements (SLAs). As part of their due diligence, the IT team has thoroughly reviewed the SLAs of each vendor to ensure they align with the company's requirements. The IT department wants to ensure they choose a vendor with the MOST appropriate SLA to maintain critical business operations. Which factors are essential for the IT department to consider when evaluating the SLAs of potential cloud service vendors? (Select the two best options.)

A. The vendor's data security measures and protocols
B. The uptime guarantees and penalties for downtime specified in the SLA
C. The pricing models offered by the vendors
D. The number of years the vendor has been in the industry

**Answer**: A and B

**Explanation**: An SLA should specify the vendor's security measures and its uptime guarantees with remedies for downtime. Pricing models and vendor longevity are business due-diligence considerations, not SLA performance terms.

**Answer**: **A and B** - The vendor's data security measures and protocols, and the uptime guarantees and penalties for downtime specified in the SLA

### Question 23: Wireless Network Site Survey

**Question**: The network administrator of an educational institution is upgrading an existing wireless network. The campus has various buildings, each having multiple floors, and the aim is to ensure consistent Wi-Fi coverage across the entire campus. To achieve this, a site survey and heat map creation will guide the placement and configuration of wireless access points (WAPs). Which of the following would MOST accurately represent the correct actions based on the survey results?

A. Place WAPs in areas marked strong in the heat map and carefully manage transmit power to avoid unnecessary overlap.
B. Ignore the heat map and place WAPs in every room regardless of signal strength to ensure maximum coverage.
C. Place WAPs in areas indicated weak in the heat map and increase transmit power to the highest in all devices, while avoiding unnecessary overlap.
D. Set all WAPs to use the same channel to ensure seamless transition for users moving between different WAP coverage areas.

**Answer**: A

**Explanation**: The heat map identifies where coverage is needed; placing WAPs accordingly and managing transmit power avoids unnecessary overlap and interference. Ignoring the map, maximizing power, or using a single channel would create co-channel interference and degrade performance.

**Answer**: **A** - Place WAPs in areas marked strong in the heat map and carefully manage transmit power to avoid unnecessary overlap.

### Question 24: Smishing

**Question**: A text message purporting to be from a user's bank requests the recipient to click on a link to verify a recent transaction and provide security details. What BEST describes the type of attack used?

A. SMiShing
B. Vishing
C. Phishing
D. Watering hole attack

**Answer**: A

**Explanation**: Smishing is phishing conducted through SMS text messages. Vishing uses voice calls, phishing typically uses email, and a watering hole attack compromises a website frequently visited by the target group.

**Answer**: **A** - SMiShing

### Question 25: False Negative

**Question**: An organization recently conducted a vulnerability scan of its network infrastructure. The security team followed up on the results, remediating all vulnerabilities flagged by the scanner. However, a month later, an external penetration tester was able to exploit a known vulnerability that the scanner had missed. What BEST describes the vulnerability scanner's failure to detect an actual vulnerability present in the system?

A. False negative
B. True positive
C. True negative
D. False positive

**Answer**: A

**Explanation**: A false negative occurs when a real vulnerability exists but the scanner fails to detect it. A true positive correctly identifies a real vulnerability, a true negative correctly finds none, and a false positive reports a vulnerability that does not exist.

**Answer**: **A** - False negative

### Question 26: False Positive

**Question**: A security analyst at a large corporation initiates a vulnerability scan on the company's web application. Upon completion, the results show several potential vulnerabilities. One of these vulnerabilities, identified as "Potential SQL Injection," is a concern. However, after further inspection, the analyst realizes this vulnerability does not exist in the application and the scanner has made an error. Given the scenario above, what term BEST describes the vulnerability scanner's identification of the "Potential SQL Injection" that does not exist in the application?

A. False positive
B. True positive
C. True negative
D. False negative

**Answer**: A

**Explanation**: A false positive is a reported vulnerability that does not actually exist in the system. A true positive is a real finding, a true negative is a correct absence of findings, and a false negative is a missed vulnerability.

**Answer**: **A** - False positive

### Question 27: Anomaly-Based Detection

**Question**: Which intrusion detection method involves the analysis engine trained to recognize baseline "normal" traffic and generates an incident when it detects deviations from this baseline?

A. Signature-based detection
B. Trend analysis
C. Network traffic analysis (NTA)
D. Behavioral- and anomaly-based detection

**Answer**: D

**Explanation**: Anomaly-based detection learns a baseline of normal behavior and alerts on deviations, which helps identify unknown threats. Signature-based detection matches known patterns, while trend analysis and NTA are broader analysis approaches.

**Answer**: **D** - Behavioral- and anomaly-based detection

### Question 28: CIS Benchmarks

**Question**: A small business wants to enhance the security of its IT infrastructure which includes various network devices, operating systems, and applications. The business is considering a standardized approach by changing default configurations, disabling unnecessary services, applying regular patches and updates, and enforcing strong password policies. To which resource should the company refer for secure configuration BEST practices?

A. Latest Cyber Threat Intelligence Reports
B. Center for Internet Security (CIS) Benchmarks
C. Network Performance Analysis Reports
D. Vendor-specific user manuals

**Answer**: B

**Explanation**: CIS Benchmarks provide consensus-based secure configuration guidance for operating systems, software, and network devices. Threat intelligence, performance reports, and vendor manuals do not provide standardized hardening baselines.

**Answer**: **B** - Center for Internet Security (CIS) Benchmarks

### Question 29: Bollards

**Question**: A security manager decides to enhance the physical security of a warehouse storing high-value tech equipment by installing a deterrent at the perimeter to prevent vehicle-based attacks. Which security measure would be the MOST suitable for this purpose?

A. Access badge
B. Fencing
C. Access control vestibule
D. Bollards

**Answer**: D

**Explanation**: Bollards are short, sturdy posts designed to stop vehicles from entering a protected perimeter. Access badges control personnel, fencing may not stop a vehicle, and an access control vestibule controls building entry.

**Answer**: **D** - Bollards

### Question 30: Healthcare Data Preservation

**Question**: A healthcare provider is digitalizing its patient data and needs a system that guarantees the preservation of its sensitive data in the event of a disaster while avoiding lock-in to a single technology vendor's platform. What is the MOST crucial practice the provider needs to implement?

A. Implementing an Uninterruptible Power Supply (UPS)
B. Incorporating additional power generators
C. Adopting platform diversity for their digital infrastructure
D. Maintaining regular data backups

**Answer**: D

**Explanation**: Regular data backups are the foundation of disaster recovery and preserve patient data so it can be restored after a disruptive event. UPS and generators address power continuity, while platform diversity addresses vendor lock-in.

**Answer**: **D** - Maintaining regular data backups

### Question 31: Data States

**Question**: An international corporation has tasked a systems engineer with implementing security controls for its data. The engineer needs to consider the various stages of data—whether it is at rest, in transit, or in use. The systems engineer is primarily dealing with which of the following concepts?

A. Data segmentation
B. Data states
C. Geographic restrictions
D. Data obfuscation

**Answer**: B

**Explanation**: Data at rest, data in transit, and data in use are the three data states. Segmentation, geographic restrictions, and obfuscation are separate data protection concepts.

**Answer**: **B** - Data states

### Question 32: Risk Tolerance

**Question**: A company is willing to accept certain risks associated with a new project as it believes the potential rewards outweigh the potential downsides. However, it will not accept risks that jeopardize its core business functions. What does this decision about the company's risk management approach primarily represent?

A. Risk appetite
B. Risk tolerance
C. Risk transference
D. Risk threshold

**Answer**: B

**Explanation**: Risk tolerance defines the boundaries of acceptable risk. Risk appetite is the broader willingness to pursue risk, risk transference shifts risk to another party, and a risk threshold is the point that triggers a response.

**Answer**: **B** - Risk tolerance

### Question 33: Cloud Architecture Model

**Question**: A multinational organization is planning to expand its services to various locations across the globe. The organization requires a flexible IT infrastructure that can easily adapt to rapid business growth but also maintain data security and meet different legal and regulatory requirements. Which of the following architecture models would be MOST suitable for this organization?

A. Cloud model
B. Standalone model
C. Peer-to-Peer model
D. Client-server model

**Answer**: A

**Explanation**: The cloud model provides rapid elasticity, global reach, and access to provider compliance certifications. Standalone, peer-to-peer, and traditional client-server models lack the same flexibility, scalability, and global deployment capabilities.

**Answer**: **A** - Cloud model

### Question 34: IPS/IDS Inline Placement

**Question**: A large organization is redesigning its network infrastructure to increase security and reduce the potential attack surface. The organization considers implementing an Intrusion Prevention System (IPS) and an Intrusion Detection System (IDS) into its security zones. The IT manager wants to secure connectivity and considers different network appliances and port security measures. Which of the following options BEST describes the benefits and disadvantages of placing the IPS/IDS devices inline with the network traffic?

A. Inline placement reduces connectivity but allows for passive detection.
B. Inline placement improves port security but increases network latency.
C. Inline placement increases the attack surface but provides comprehensive traffic visibility.
D. Inline placement allows for active prevention measures but can become a single point of failure.

**Answer**: D

**Explanation**: Inline placement lets the IPS actively block malicious traffic, but all traffic depends on the device, so a failure can disrupt the network. Passive detection is characteristic of out-of-band IDS deployment.

**Answer**: **D** - Inline placement allows for active prevention measures but can become a single point of failure.

### Question 35: BYOD Removable Media

**Question**: A financial firm is transitioning to a Bring Your Own Device (BYOD) policy, significantly increasing the utilization of removable media among employees. What is the MOST vital practice to emphasize to minimize potential cybersecurity threats?

A. Implementing a strict policy on removable media encryption and management
B. Regular auditing of the physical security of devices
C. Adopting a robust password management policy
D. Increasing focus on anomalous behavior recognition

**Answer**: A

**Explanation**: Encryption and management policies directly protect data on removable media if it is lost or stolen. Physical audits, password management, and behavior monitoring are important but less directly targeted at removable-media risks.

**Answer**: **A** - Implementing a strict policy on removable media encryption and management

### Question 36: Acceptable Use Policy Classification

**Question**: An acceptable use policy requires the system to encrypt confidential information while in transit. All employees must use secure email when exchanging proprietary information with external vendors. Which of the following describes this type of acceptable use policy?

A. Technical
B. Preventive
C. Operational
D. Managerial

**Answer**: A

**Explanation**: The policy mandates specific technical safeguards—encryption in transit and secure email. Preventive describes a goal, operational policies cover procedures, and managerial policies cover governance and oversight.

**Answer**: **A** - Technical

### Question 37: Unified Incident Response

**Question**: A company mandated personnel training within each business unit on their own unit's role in the incident response plan. However, during an incident response, it became apparent that the business units were not working well together, resulting in a delayed resolution. How can the company build a more unified response to an incident? (Select the two best options.)

A. More department training
B. Leaders only training
C. Team building exercises
D. Cross-team training

**Answer**: C and D

**Explanation**: Team building improves collaboration and trust across units, and cross-team training ensures personnel understand one another's roles. Additional siloed training or leader-only training would not address the coordination gap.

**Answer**: **C and D** - Team building exercises and Cross-team training

### Question 38: Security Keys

**Question**: The cybersecurity expert at a technology firm recommends adding another layer of protection to employee accounts. The expert suggests a physical device that users can insert or tap on compatible systems to verify their identity alongside a password. The proposed solution should use something other than biometric data, produce time-sensitive codes, or be an app or software on personal devices. Which authentication method is the cybersecurity expert recommending for the employees?

A. Security keys
B. Biometric authentication
C. Soft authentication tokens
D. Hard authentication tokens

**Answer**: A

**Explanation**: Security keys are physical FIDO2/WebAuthn devices that authenticate cryptographically without time-based codes. Biometrics are excluded, soft tokens are apps, and traditional hard tokens often generate time-sensitive one-time codes.

**Answer**: **A** - Security keys

### Question 39: Memory Dumps

**Question**: In cybersecurity investigations, what is the significance of using a memory dump to extract valuable data from a computer system?

A. Memory dumps are solely beneficial for creating encrypted backups and their usage.
B. Memory dumps provide information about active processes, registry data, and more.
C. Memory dumps provide a permanent record of system usage for long-term trend analysis.
D. Memory dumps recover lost files and volatile memory from mass storage devices.

**Answer**: B

**Explanation**: A memory dump captures volatile RAM contents such as active processes, network connections, loaded drivers, and registry data. It is not a backup, a permanent long-term record, or a mass-storage recovery tool.

**Answer**: **B** - Memory dumps provide information about active processes, registry data, and more.

### Question 40: Nation-State Warfare Motivation

**Question**: A recent cyberattack led to massive disruptions in a country's power grid, causing widespread blackouts and significant economic and social damage. The country's cyber team traced the attack to a hostile nation-state's cyber warfare division. In this case, what is the primary motivation of the perpetrators?

A. Financial gain
B. Levels of sophistication/capability
C. War
D. Ethical concerns

**Answer**: C

**Explanation**: An attack by a nation-state cyber warfare division against critical infrastructure is consistent with military or wartime objectives. Financial gain, capability level, and ethical concerns do not fit the described state-sponsored attack.

**Answer**: **C** - War

### Question 41: SSL/TLS Certificate Roles

**Question**: A small online printing company needs to secure its internal web server with Secure Sockets Layer/Transport Layer Security (SSL/TLS) encryption. The IT administrator explores the certificate options and their implications. In the context of SSL/TLS certificate generation, which statement correctly explains the roles of Certificate Signing Request, self-signed, and third-party certificates?

A. The server generates a Certificate Signing Request to create a self-signed certificate, while a Certificate Authority issues third-party certificates after validating the server's identity.
B. The server generates a Certificate Signing Request (CSR) and submits it to a third-party Certificate Authority (CA) for validation but generates self-signed certificates without involving a third party.
C. The server generates a self-signed certificate to create a Certificate Signing Request, while a Certificate Authority issues third-party certificates after validating the server's identity.
D. The server generates a self-signed certificate and submits it to a third-party Certificate Authority for validation but generates a Certificate Signing Request without involving a third party.

**Answer**: B

**Explanation**: A CSR is generated and submitted to a CA for a third-party certificate; a self-signed certificate is generated locally without third-party validation. The other options reverse or confuse these two processes.

**Answer**: **B** - The server generates a Certificate Signing Request (CSR) and submits it to a third-party Certificate Authority (CA) for validation but generates self-signed certificates without involving a third party.

### Question 42: Digital Evidence Admissibility

**Question**: In cybersecurity investigations, why is it crucial to ensure the admissibility of digital evidence collected from computer systems?

A. Due process and the fair application of laws require proper handling of digital evidence.
B. The location and identity of threat actors are easily identifiable through digital evidence.
C. Threat actors can tamper with digital evidence without affecting its integrity.
D. Digital evidence is often visible to the naked eye, ensuring its authenticity.

**Answer**: A

**Explanation**: Proper chain of custody, write-blocking, and hash verification preserve evidence integrity so it can be used in legal proceedings. Digital evidence is not always easily attributable or visible, and tampering is precisely why rigorous handling is required.

**Answer**: **A** - Due process and the fair application of laws require proper handling of digital evidence.

### Question 43: Incident Response Policy

**Question**: Which policy outlines the processes to follow after a security breach or cyberattack occurs and includes procedures for identifying, investigating, controlling, and mitigating the impact of incidents?

A. Disaster recovery policy
B. Change management policy
C. Incident response policy
D. Acceptable use policy (AUP)

**Answer**: C

**Explanation**: The incident response policy defines how to detect, investigate, contain, eradicate, recover from, and learn from security incidents. Disaster recovery focuses on restoring IT after a major disruption, change management controls changes, and an AUP defines acceptable employee use.

**Answer**: **C** - Incident response policy

### Question 44: Recovery Point Objective

**Question**: A technology company implements a backup strategy to mitigate data loss in case of a system crash. The strategy focuses on defining the maximum age of data to retrieve from the backup storage to ensure business continuity after a system crash. Which principle should the company apply to meet their needs?

A. Single loss expectancy (SLE)
B. Recovery point objective (RPO)
C. Annualized loss expectancy (ALE)
D. Recovery time objective (RTO)

**Answer**: B

**Explanation**: RPO defines the maximum acceptable amount of data loss measured in time. RTO defines acceptable downtime, while SLE and ALE are quantitative risk analysis metrics.

**Answer**: **B** - Recovery point objective (RPO)

### Question 45: Firewall and IDS/IPS Enhancement

**Question**: An eCommerce company utilizes an advanced firewall for network protection. However, due to an increasing variety of threats, their existing setup is not enough. The company considers enhancing its firewall with intrusion detection and prevention systems (IDS/IPS). What should be their primary approach in this scenario?

A. Abandon the firewall and adopt host-based IDS/IPS
B. Discard firewall rules and rely solely on network-based IDS/IPS
C. Add network-based IDS/IPS and maintain the firewall rules
D. Keep the firewall and ignore IDS/IPS adoption

**Answer**: C

**Explanation**: Defense in depth layers network-based IDS/IPS with the existing firewall. Abandoning the firewall or discarding its rules removes a critical control, while ignoring IDS/IPS leaves the organization without the added detection and prevention capability.

**Answer**: **C** - Add network-based IDS/IPS and maintain the firewall rules

### Question 46: Load Balancer Security

**Question**: An organization plans to implement a load balancer as part of its network infrastructure to manage the increased web traffic to its services. The organization tasks a network administrator with ensuring that the load balancer configures in line with best security practices to reduce the attack surface and secure the enterprise infrastructure. The network administrator's responsibilities include evaluating the network appliances, securing connectivity, and considering device placement. What is the MOST effective security measure in this scenario?

A. Configure the load balancer to operate in a fail-open mode.
B. Use a proxy server in combination with the load balancer.
C. Implement a Web Application Firewall (WAF) alongside the load balancer.
D. Place the load balancer in the screened subnet.

**Answer**: D

**Explanation**: Placing the load balancer in a screened subnet (DMZ) exposes only the load balancer to the internet while protecting internal servers. Fail-open weakens security, and proxy or WAF controls are complementary rather than the primary placement decision.

**Answer**: **D** - Place the load balancer in the screened subnet.

### Question 47: Regulatory Sanctions Impact

**Question**: A board of directors receives a memorandum that two departments in the organization violate federal regulations. What could the organization receive that would monetarily impact them if sanctioned?

A. Fines
B. Reputational damage
C. Loss of license
D. Indemnification

**Answer**: A

**Explanation**: Regulatory sanctions can include monetary fines. Reputational damage is non-monetary, loss of license is a regulatory action, and indemnification generally refers to compensation paid rather than received.

**Answer**: **A** - Fines

### Question 48: Change Implementation Timing

**Question**: A large international organization is planning to implement changes to its infrastructure. When is the BEST time to implement changes to minimize disruption and ensure business continuity? (Select the two best options.)

A. Peak times
B. Maintenance windows
C. Off-peak times
D. After the workday

**Answer**: B and C

**Explanation**: Maintenance windows and off-peak times minimize user impact and business disruption. Peak times maximize disruption, and "after the workday" is less comprehensive for a global organization with multiple time zones.

**Answer**: **B and C** - Maintenance windows and Off-peak times

### Question 49: Legacy System Mitigation

**Question**: A system administrator is upgrading a company's network security infrastructure and notices several legacy machines running end-of-life operating systems (OS). These machines are no longer upgradeable as the developer has stopped issuing security patches and updates. However, the machines are still necessary for certain critical tasks. What is the system administrator's MOST effective course of action to reduce potential security vulnerabilities caused by these legacy machines running end-of-life operating systems?

A. Disable all network connections on the legacy machines.
B. Upgrade the software to make it compatible with a modern OS.
C. Isolate the legacy machines on a separate network segment.
D. Replace the legacy machines with modern machines.

**Answer**: C

**Explanation**: Isolating the unpatched systems on a separate network segment limits their exposure and prevents lateral movement while preserving their critical function. Disabling connectivity breaks functionality, upgrading is not possible in the scenario, and replacement may not be immediately feasible.

**Answer**: **C** - Isolate the legacy machines on a separate network segment

### Question 50: SIEM Alert Tuning

**Question**: A cybersecurity analyst notices that a certain rule in the Security Information and Event Management (SIEM) system is generating a high volume of dashboard notifications, making it difficult for the team to manage. Which action would be MOST effective in dealing with this issue?

A. Increase the sensitivity of the alerting system to counter the increased alert volume
B. Ignore all alerts generated by this particular rule until the team finds the time to resolve the problem
C. Remove the problematic rule entirely from the SIEM system
D. Adjust the parameters of the rule or lower the alert level

**Answer**: D

**Explanation**: Tuning the rule's parameters or lowering its severity reduces alert noise while preserving detection. Increasing sensitivity worsens the volume, ignoring alerts risks missing threats, and removing the rule eliminates detection entirely.

**Answer**: **D** - Adjust the parameters of the rule or lower the alert level

### Question 51: Certificate Signing Request

**Question**: A small development company just set up a web server and must ensure a secure customer connection. Regarding digital certificates, what is a file containing the information that the subject wants to use in the certificate, including its public key?

A. CSR
B. PKI
C. CRL
D. CA

**Answer**: A

**Explanation**: A Certificate Signing Request contains the subject's information and public key for submission to a Certificate Authority. PKI is the overall framework, a CRL lists revoked certificates, and a CA issues and signs certificates.

**Answer**: **A** - CSR (Certificate Signing Request)

### Question 52: Proprietary Data Classification

**Question**: A software company designs a new feature for its product involving the creation and storage of new algorithms and methods that give the product a competitive advantage. The company wants to appropriately classify this information within its data management system. What would be the MOST fitting classification for this data?

A. Critical
B. Confidential
C. Proprietary
D. Public

**Answer**: C

**Explanation**: Proprietary data is owned by the organization and derives value from competitive advantage, such as trade secrets and unique algorithms. Public data is openly shareable, while critical and confidential describe other risk or sensitivity categories.

**Answer**: **C** - Proprietary

### Question 53: SOPs in Change Management

**Question**: An organization has an established change management program that includes standard operating procedures (SOPs). It wants to implement changes consistently and effectively. What role do SOPs play in the change management process?

A. Standard operating procedures (SOPs) help track and communicate the status and outcome of approved changes.
B. Standard operating procedures (SOPs) provide guidelines for developing backout plans for changes.
C. Standard operating procedures (SOPs) outline the steps for employees to follow when conducting an impact analysis.
D. Standard operating procedures (SOPs) define routine operations or changes and provide detailed instructions for their implementation.

**Answer**: D

**Explanation**: SOPs are documented, repeatable instructions for performing routine operations and changes consistently. Tracking, backout planning, and impact analysis are separate change management activities.

**Answer**: **D** - Standard operating procedures (SOPs) define routine operations or changes and provide detailed instructions for their implementation.

### Question 54: Nation-State Political Motivation

**Question**: A multinational corporation recently fell victim to a series of cyberattacks, disrupting services and leading to significant financial losses. After an investigation, the corporation found that these attacks were part of a systematic campaign to undermine the corporation's market position. The highly sophisticated attacks suggest the involvement of a governmental entity with specific strategic objectives. Which of the following motivations BEST describes this scenario?

A. Revenge
B. Political
C. Chaotic
D. Financial

**Answer**: B

**Explanation**: A governmental entity conducting a systematic campaign for strategic objectives is politically motivated. Revenge is personal, chaotic is not a deliberate motivation, and financial gain does not fit a state-sponsored campaign to undermine a market position.

**Answer**: **B** - Political

### Question 55: Provisioning Automation

**Question**: Given the importance of automation and orchestration related to secure operations, a newly hired IT employee creates, modifies, and deletes user accounts and access rights across the company's IT systems. Due to the significant number of users and the heightened need for security, this task proves to be time-consuming and error-prone. Which automation capability can not only improve the efficiency and consistency of this task but also ensure secure operations?

A. Provisioning
B. Service management
C. Ticketing
D. Guardrails and security groups

**Answer**: A

**Explanation**: Provisioning automates the creation, modification, and deletion of user accounts and access rights. Service management and ticketing are workflow tools, while guardrails and security groups are controls rather than account lifecycle automation.

**Answer**: **A** - Provisioning

### Question 56: Collision Attack

**Question**: An incident response team detected a threat actor attempting to find two different inputs that produce the same hash value in the company's secure communication system. Which of the following BEST describes this type of attack?

A. Birthday attack
B. Side-channel attack
C. Brute-force attack
D. Collision attack

**Answer**: D

**Explanation**: A collision attack seeks two different inputs that produce the same hash output. A birthday attack is a method for finding collisions, side-channel attacks exploit implementation leakage, and brute-force attacks exhaustively search a space.

**Answer**: **D** - Collision attack

### Question 57: Single Loss Expectancy

**Question**: A newly established software firm plans to roll out a proprietary messaging platform. One of their main concerns is estimating the platform's monetary impact per incident of downtime. What measure should the firm employ to address this concern?

A. Annualized Rate of Occurrence (ARO)
B. Annualized Loss Expectancy (ALE)
C. Risk Identification
D. Single Loss Expectancy (SLE)

**Answer**: D

**Explanation**: SLE estimates the monetary loss from a single incident. ARO is how often an incident occurs per year, ALE is SLE multiplied by ARO, and risk identification is the process of finding and documenting risks.

**Answer**: **D** - Single Loss Expectancy (SLE)

### Question 58: Serverless Platforms and SDN

**Question**: A company is deploying a software service to monitor traffic and enforce security policies in its cloud environment. Considering the need for responsiveness, which technology should the company consider using?

A. Infrastructure as code (IaC)
B. Microservices
C. Virtual private cloud (VPC)
D. Serverless platforms and software-defined networking (SDN)

**Answer**: D

**Explanation**: SDN enables programmable, dynamic network control and policy enforcement, while serverless platforms provide scalable, event-driven execution. IaC, microservices, and VPCs are related but do not directly provide responsive traffic monitoring and enforcement.

**Answer**: **D** - Serverless platforms and software-defined networking (SDN)

### Question 59: Compensating Controls

**Question**: After finding some of the company's confidential data on the internet, a software team is drafting a policy on vulnerability response and remediation. What remediation practice refers to measures put in place to mitigate the risk of a vulnerability when the team cannot directly eliminate it?

A. Insurance
B. Compensating controls
C. Segmentation
D. Patching

**Answer**: B

**Explanation**: Compensating controls are alternative safeguards used when a vulnerability cannot be directly fixed. Insurance transfers financial risk, segmentation limits exposure, and patching directly remediates software flaws.

**Answer**: **B** - Compensating controls

### Question 60: Cybercrime

**Question**: A large multinational software company experienced a ransomware attack. After running a forensic audit and recovering data from backups, the company found that it was an organized, illicit, nonpolitical group that attempted to extort it. What describes the attack that occurred to the company?

A. Hacktivism
B. Insider threat
C. Cybercrime
D. Service disruption

**Answer**: C

**Explanation**: An organized, illicit, nonpolitical group using ransomware for extortion is engaged in cybercrime. Hacktivism is ideologically motivated, insider threats originate internally, and service disruption is an outcome rather than the threat category.

**Answer**: **C** - Cybercrime

### Question 61: Multicloud Disaster Recovery

**Question**: An online retailer seeks ways to bolster its disaster recovery strategy for its online sales platforms, aiming to minimize the risk of any interruptions during unexpected catastrophic events. Which approach MOST effectively maintains the availability of their online services during such events?

A. Transitioning to multicloud systems
B. Developing a company-owned, local data center
C. Implementing Uninterruptible Power Supply (UPS) systems for local servers
D. Reinforcing physical server locations to withstand natural disasters

**Answer**: A

**Explanation**: Multicloud distributes workloads across providers and regions, providing redundancy and failover. A single local data center, UPS systems, or a hardened physical site still represents a single point of failure.

**Answer**: **A** - Transitioning to multicloud systems

### Question 62: Risk Register

**Question**: A technology firm is adopting a structured approach to managing risk. It catalogs potential risks and assigns them to responsible parties within the team. This catalog also includes the strategies to mitigate these risks and their potential impacts. What document must the firm develop as it adopts this approach?

A. Risk assessment
B. Risk analysis
C. Risk register
D. Business impact analysis

**Answer**: C

**Explanation**: A risk register documents identified risks, owners, potential impacts, mitigation strategies, and current status. Risk assessment and risk analysis are processes, and a business impact analysis focuses on continuity impacts.

**Answer**: **C** - Risk register

### Question 63: Secure Enclave

**Question**: A cybersecurity analyst implements security measures for a financial institution's infrastructure. The analyst explores different technologies to enhance security and must select the appropriate technology to strengthen security within the organization's infrastructure. Which technology should the cybersecurity analyst choose to enhance security for executing sensitive operations and protecting critical data in the financial institution's infrastructure?

A. Firewall
B. Secure enclave
C. Intrusion detection system
D. Key management system

**Answer**: B

**Explanation**: A secure enclave is a hardware-isolated environment for sensitive operations and critical data. Firewalls filter traffic, IDS detects threats, and a key management system protects cryptographic keys but does not by itself secure the execution environment.

**Answer**: **B** - Secure enclave

### Question 64: Sideloading

**Question**: An IT administrator observes that a significant number of mobile devices within the organization have applications installed from outside official app stores. Concerned about the security implications, the administrator decides to assess the vulnerabilities introduced by this practice. Which of the following BEST describes the process that allows users to install applications on their devices from sources other than official app stores, potentially exposing the device to malware or unauthorized data access?

A. Keylogging
B. Sideload
C. Jailbreaking
D. Rooting

**Answer**: B

**Explanation**: Sideloading installs applications from unofficial sources, bypassing the security controls of official app stores. Keylogging captures keystrokes, while jailbreaking and rooting remove operating system restrictions.

**Answer**: **B** - Sideload

### Question 65: System Owner Responsibilities

**Question**: The newly appointed IT manager of a growing e-commerce company has initiated a security review to ensure compliance with industry standards. This process includes defining clear roles and responsibilities for data and system owners to optimize the organization's security posture. According to the IT manager's new plan, which of the following would be the primary responsibility of a system owner in the context of cybersecurity?

A. Conducting network penetration tests
B. Establishing the security controls for systems
C. Implementing a disaster recovery plan
D. Prosecuting individuals who perpetrate cyberattacks

**Answer**: B

**Explanation**: A system owner is responsible for defining and implementing appropriate security controls for the systems they own. Penetration testing, disaster recovery planning, and prosecution are separate organizational functions.

**Answer**: **B** - Establishing the security controls for systems

### Question 66: Vishing

**Question**: A representative at a company reports receiving numerous unsolicited phone calls seeking banking information for a credit report. Which social engineering variant is the finance director experiencing?

A. Vishing
B. Spear phishing
C. Whaling
D. Smishing

**Answer**: A

**Explanation**: Vishing is voice phishing conducted over the phone. Spear phishing and whaling use targeted email, and smishing uses SMS text messages.

**Answer**: **A** - Vishing

### Question 67: Resilience and Recovery Strategies

**Question**: A large technology company has recently experienced a significant system failure due to a cyberattack. The chief information security officer (CISO) is conducting a post-incident review to identify ways to improve the organization's resilience and recovery capabilities. The CISO wants to focus on strategies that could have prevented the system downtime or minimized its duration and impact. From a resilience and recovery standpoint in security architecture and continuity of operations planning (COOP), which of the following strategies would the CISO MOST likely recommend implementing to enhance the organization's ability to prevent or quickly recover from similar incidents in the future? (Select the two best options.)

A. Expanding the IT team with more developers
B. Investing in a stronger firewall system
C. Implementing a detailed incident response plan
D. Establishing a redundant data center

**Answer**: C and D

**Explanation**: An incident response plan improves coordination, containment, and recovery, while a redundant data center provides failover continuity. Adding developers or strengthening the firewall does not directly improve resilience and recovery after an incident.

**Answer**: **C and D** - Implementing a detailed incident response plan and Establishing a redundant data center

### Question 68: IDS/IPS Alert Optimization

**Question**: A multinational corporation has recently implemented an intrusion detection system (IDS) and intrusion prevention system (IPS) to protect its network infrastructure. The security team receives many alerts and struggles to manage false positives. The team must optimize the IDS and IPS to identify and prioritize actual threats while minimizing irrelevant alerts. Which primary strategy should the team adopt to achieve this objective?

A. Integrate SELinux policies for a layered security approach, ensuring system-level restrictions to applications and processes.
B. Implement trend analysis to identify patterns and anomalies, tune the IDS/IPS over time, and prioritize genuine threats.
C. Apply signature-based detection rules only to filter out false positives.
D. Ignore all alerts from the IDS/IPS to focus on manual monitoring of network traffic.

**Answer**: B

**Explanation**: Trend analysis and iterative tuning improve detection accuracy and help prioritize genuine threats. SELinux is unrelated to IDS/IPS alert tuning, signature-only rules do not eliminate false positives, and ignoring alerts is unsafe.

**Answer**: **B** - Implement trend analysis to identify patterns and anomalies, tune the IDS/IPS over time, and prioritize genuine threats.

### Question 69: DDoS Service Disruption

**Question**: A major online retailer experiences a sudden halt in its services during the peak holiday shopping season. It traces the cause back to an orchestrated distributed denial of service (DDoS) attack, which overwhelmed the retailer's servers with traffic, making it impossible for legitimate users to access the site. This attack BEST aligns with which type of threat motivation?

A. Espionage
B. Financial
C. Service disruption
D. Disinformation

**Answer**: C

**Explanation**: The attack's primary effect is denying service to legitimate users, which aligns with service disruption. Espionage steals information, financial motivation involves monetary gain, and disinformation spreads false information.

**Answer**: **C** - Service disruption

### Question 70: LEAP Alternatives

**Question**: A company using Wi-Fi Protected Access (WPA) wireless security on their wireless access points (WAPs) uses Lightweight Extensible Authentication Protocol (LEAP) to authenticate users to the network. LEAP is vulnerable to password cracking. What other options does the company have to mitigate this vulnerability? (Select the two best options.)

A. Protected Extensible Authentication Protocol (PEAP)
B. EAP-MD5
C. RADIUS federation
D. Flexible Authentication via Secure Tunneling (EAP-FAST)

**Answer**: A and D

**Explanation**: PEAP and EAP-FAST create protected TLS tunnels for authentication, mitigating LEAP's password-cracking weakness. EAP-MD5 is also weak, and RADIUS federation is an inter-domain authentication framework rather than a LEAP replacement.

**Answer**: **A and D** - Protected Extensible Authentication Protocol (PEAP) and Flexible Authentication via Secure Tunneling (EAP-FAST)

### Question 71: Risk Transference

**Question**: A technology company experiences several security vulnerabilities with its online application, leading to customer complaints and legal threats. In response, the board of directors decides to outsource the maintenance and associated liabilities of the application to a third party. Which risk management strategy is the company primarily implementing?

A. Risk transference
B. Risk acceptance
C. Risk avoidance
D. Risk mitigation

**Answer**: A

**Explanation**: Outsourcing maintenance and associated liabilities shifts risk to a third party, which is risk transference. Risk acceptance retains the risk, avoidance eliminates the activity, and mitigation reduces the risk.

**Answer**: **A** - Risk transference

### Question 72: Access Control List Objective

**Question**: A medium-sized company has entrusted its IT administrator with the crucial responsibility of improving network security. The company's network contains sensitive financial data, proprietary software, and employee records. Since the IT administrator's task is implementing access control lists (ACLs), what is the primary objective for using them in computer systems and networks?

A. To enforce mandatory access controls (MAC) on Linux systems
B. To regulate and manage permissions for resource access and actions
C. To provide centralized management and configuration of operating systems in Active Directory
D. To establish standardized configuration baselines for devices

**Answer**: B

**Explanation**: ACLs regulate who can access resources and what actions they can perform. MAC is a separate access control model, Active Directory provides centralized management, and configuration baselines are hardening guides.

**Answer**: **B** - To regulate and manage permissions for resource access and actions

### Question 73: On-Path Attack

**Question**: A network administrator suspects that an attacker is intercepting and potentially modifying communications between their organization's server and the client systems. The attacker is not detected by either party during this process. Which type of attack is the network administrator likely observing in this instance?

A. On-path attack
B. Domain Name System (DNS) attack
C. Distributed denial-of-service (DDoS) attack
D. Replay attack

**Answer**: A

**Explanation**: An on-path (man-in-the-middle) attack intercepts and can modify communications without the endpoints detecting it. DNS attacks target name resolution, DDoS affects availability, and replay attacks retransmit captured data.

**Answer**: **A** - On-path attack

### Question 74: Bluetooth Network Vector

**Question**: A threat actor exploits the vulnerabilities or misconfigurations in a device's wireless networking protocol to transmit a malicious file to a user's device. This scenario is an example of what type of networking vector?

A. Direct Access
B. Cloud Access
C. Wired Network
D. Bluetooth Network

**Answer**: D

**Explanation**: Bluetooth is a wireless networking protocol commonly exploited to transmit malicious files. Direct Access and cloud access are remote connectivity technologies, and a wired network contradicts the wireless scenario.

**Answer**: **D** - Bluetooth Network

### Question 75: Incident Response Final Phase

**Question**: The leader of the cybersecurity team for a major e-commerce company recently encountered a major data breach that led to the exposure of customer payment details. The team has now contained the breach and is moving toward the final phase of the incident response cycle. After completing all previous steps, what is the team's primary objective in the final phase?

A. Restoring the affected system to a secure state to reintegrate it
B. Identifying stakeholders and reporting it to relevant parties
C. Analyzing the incident to improve procedures or systems
D. Determining the root cause of the incident to eradicate it

**Answer**: C

**Explanation**: The final phase is lessons learned, where the team analyzes the incident to improve procedures, controls, and future response. Restoration is part of recovery, reporting occurs earlier, and root-cause eradication precedes recovery.

**Answer**: **C** - Analyzing the incident to improve procedures or systems

### Question 76: Location-Based Authentication

**Question**: An employee traveling in Europe for vacation submitted a ticket as they could not access their work email. Which policy does the company use?

A. Password age
B. Multifactor authentication
C. Password management
D. Location-based authentication

**Answer**: D

**Explanation**: Location-based authentication restricts or challenges access based on geographic location, which explains why access failed while the employee was traveling. Password age, password management, and MFA do not specifically account for the employee's location.

**Answer**: **D** - Location-based authentication

### Question 77: Least-Privilege Inter-Zone Policies

**Question**: A network administrator is configuring firewall policies between several internal security zones. Which principle should guide the inter-zone rules to minimize the attack surface?

A. Allow only the traffic required for business functions, following least privilege.
B. Allow all traffic between internal zones to simplify administration.
C. Deny all traffic, including required business services.
D. Merge the zones into a single flat network.

**Answer**: A

**Explanation**: Least privilege means permitting only the traffic necessary for business functions between zones. Allowing all traffic removes the benefit of segmentation, denying everything breaks required services, and flattening the network increases exposure.

**Answer**: **A** - Allow only the traffic required for business functions, following least privilege.

### Question 78: Attestation

**Question**: Which term describes a formal declaration or statement, often provided by management or a third party, that an organization's security controls meet specified requirements?

A. Attestation
B. Acknowledgment
C. Authorization
D. Authentication

**Answer**: A

**Explanation**: Attestation is a formal declaration that controls meet specified requirements. Acknowledgment is acceptance or awareness, authorization grants access, and authentication verifies identity.

**Answer**: **A** - Attestation

### Question 79: SIEM Threshold Alerting

**Question**: A SIEM is configured to generate an alert when a user account experiences multiple failed login attempts within a short time window. Which type of alerting does this describe?

A. Anomaly-based alerting
B. Threshold-based alerting
C. Signature-based alerting
D. Heuristic alerting

**Answer**: B

**Explanation**: Threshold-based alerting triggers when a defined count is exceeded within a time window, such as multiple failed logins. Anomaly-based alerting compares behavior to a baseline, and signature-based alerting matches known patterns.

**Answer**: **B** - Threshold-based alerting

### Question 80: Post-Remediation Testing

**Question**: After remediating vulnerabilities identified during a security assessment, which actions should the security team perform to confirm the fixes were effective? (Select the three best options.)

A. Rescan the affected systems to verify the vulnerabilities are no longer detected.
B. Confirm that the required patches or configuration changes were applied.
C. Perform regression testing to ensure the fixes did not break functionality.
D. Disable logging and monitoring to reduce noise during testing.

**Answer**: A, B, and C

**Explanation**: Post-remediation validation includes rescanning, verifying that patches or configuration changes were applied, and regression testing to confirm functionality. Disabling logging and monitoring would reduce visibility and is not a valid testing step.

**Answer**: **A, B, and C** - Rescan the affected systems, Confirm the patches or configuration changes were applied, and Perform regression testing

### Question 81: Remote-Work Continuity

**Question**: A company wants to ensure employees can continue working remotely during a disaster that prevents access to the office. Which solution BEST supports this continuity requirement?

A. A VPN with remote desktop or virtual desktop infrastructure (VDI)
B. Keeping all employee desktops powered on at the office
C. Relying solely on local backups stored at the office
D. Installing uninterruptible power supplies on office workstations

**Answer**: A

**Explanation**: A VPN with remote desktop or VDI lets employees securely access applications and data from outside the office. Office desktops, local backups, and UPS devices depend on access to the affected facility.

**Answer**: **A** - A VPN with remote desktop or virtual desktop infrastructure (VDI)

### Question 82: MSP and Supply-Chain Risk

**Question**: A company decides to outsource its IT operations to a managed service provider (MSP) instead of maintaining the function in-house. Which risk does this decision primarily introduce?

A. Reduced access to specialized expertise
B. Increased control over internal systems
C. Elimination of third-party dependencies
D. Supply-chain risk from the provider's access and dependencies

**Answer**: D

**Explanation**: Using an MSP introduces supply-chain risk because the provider has access to the company's systems and may itself depend on other vendors. Outsourcing typically increases access to specialized expertise and reduces direct control; it does not eliminate third-party dependencies.

**Answer**: **D** - Supply-chain risk from the provider's access and dependencies

### Question 83: Data Breach Penalties

**Question**: A major retail store suffered a data breach that exposed customer payment card data. A class-action lawsuit resulted in a $3.5 million settlement for affected consumers, and a regulatory agency levied an additional $2.5 million penalty against the store. Which of the following BEST describes the monetary penalties imposed on the organization?

A. Reputational damage
B. Fines
C. Loss of license
D. Indemnification

**Answer**: B

**Explanation**: The consumer settlement and the regulatory penalty are monetary fines imposed on the organization. Reputational damage is non-monetary, loss of license is a regulatory action that may disrupt business, and indemnification generally refers to compensation paid rather than received.

**Answer**: **B** - Fines
