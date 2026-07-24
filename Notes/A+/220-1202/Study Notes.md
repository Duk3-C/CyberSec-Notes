Passing score is 700 on a scale of 100-900. The exam consists of a maximum of 90 questions, although I can get less than that.

### Core Domains Breakdown
	. Operating Systems (27%): Installation and configuration of WIndows, macOS, Linux, iOS, and Androidm including command-line tools and virtualization.
	. Security (24%): Malware removal, threat detection, identity and access management, physical security, and data destruction.
	. Software Troubleshooting (26%): Resolving PC and mobile OS issues, application errors, and performance problems using systematic troubleshooting methodologies.
	. Operational Procedures (23%): Best practices for documentation, change management, disaster recovery, safety, and professional communication.

Certificate Manager Console (certmgr.msc) - console related to managing digital certificates for the current user and trusted root certification authority certificates.
Group Policy Editor (gpedit.msc) - Console related to configuring detailed user and system registry settings via policies.
Registry Editor (regedit.exe) - Tool for making direct edits to the registry database, such as adding or modifying keys or values.
Hives - File storing configuration data corresponding to a section of the Windows registry.
Microsoft Management Console (MMC) - Utility allowing Windows administrative tools to be added as snap-ins to a single interface.
System Information (msinfo32.exe) - Utility that provides a report of the PC's hardware and software configuration.
Event Viewer (eventvwr.msc) - Windows console related to viewing and exporting events in the Windows logging file format.
System File Checker - Command-line utility that checks the integrity of system and device driver files.
Update Limitations - Product life cycle and procurement consideration where a device or product no longer receives a full range of updates or support from its vendor.
File System - Structure for file data indexing and storage created by a process of formatting a partition that allows an OS to make use of a mass storage device, such as an HDD, SSD, or thumb drive.
Incremental Backups - Job type in which all selected files that have changed since the last full or incremental backup are backed up.
Preboot eXecution Environment (PXE) - Feature of a network adapter that allows the computer to boot by contacting a suitably configured server over the network.
Windows Recovery Environment (WinRE) - Windows troubleshooting feature that installs a command shell environment to a recovery partition to remediate boot issues.
Roll Back Driver - Windows troubleshooting feature that allows removal of an update or reversion to a previous driver version.
fixboot - command in Windows that allows for the repair (or attempted repair) of the boot manager and boot loader.
Drifting Out of Sync - Situation where hosts on a network are not closely synchronized to the same data/time source.
Standard Account - Non-privileged user account in Windows that typically has membership of the Users security group only.
Power Users - One of the default Windows group accounts. Its use is deprecated, but it is still included with Windows to support legacy applications.
Multifactor Authentication (MFA) - Authentication scheme that requires the user to present at least two different factors as credentials; for example, something you know, something you have, something you are, something you do, and somewhere you are. Specifying two factors is know as 2FA.
Soft Token - Either an additional code to use for 2-step verification, such as a one-time password, or authorization data that can be presented as evidence of authentication in an SSO system.
Hard Token - USB storage key or smart card with a cryptographic module that can hold authenticating encryption keys securely.
Kerberos - Single sign-on authentication and authorization service that is based on a time-sensitive, ticket-granting system.
Active Directory (AD) - Network directory service for Microsoft Windows domain networks that facilitates authentication and authorization of user and computer accounts.
Member Server - Any application server computer that has joined a domain but does not maintain a copy of the Active Directory database.
Security Groups - Access control feature that allows permissions to be allocated to multiple users more efficiently.
Organizational Unit (OU) - Structural feature of a network directory that can be used to group objects that should share a common configuration or organizing principle, such as accounts within the same business department.
Group Policy Objects (GPOs) - On a Windows domain, a way to deploy per-user and per-computer settings such as password policy, account restrictions, firewall status, and so on.
gpupdate - command-line tools to apply and analyze group policies.
Login Script - Code that performs a series of tasks automatically when a user account is authenticated.

JIT (Just-In-Time) access is a security practice in which users are granted access to resources only when needed and for only as long as it takes to complete the needed task.

Risk analysis is a systematic approach to identify possible risks associated with implementing the change. Each change being requested should undergo a risk analysis.

In a Windows environment, services often run under a specific user account rather than the local system account. If that account's credentials have expired or if the account has been locked due to multiple failed login attempts, the services it was running will stop.

After completing all malware removal steps, a technician's next action should be to educate the end user on how to prevent those types of issues.

Synthetic full backups  create a full backup by combining previous full backups and incremental backups without transferring all data again. This improves the backup time because the system does not have to process every single file from scratch every time the backup is made.

When a technician has exhausted their knowledge and cannot provide any further steps to a customer during troubleshooting, they must escalate the issue to a senior technician that can better handle the issue. That way the customer will know they're in hand of a more experienced professional.

Offboarding requires revoking a user's acces to both physical and digital resources to maintain security.

When dealing with zero-day vulnerabilities, a technician must implement an emergency change immediately, that way the fix will have priority.

Most issues that feature bad performance and slow applications, are mostly due to RAM usage. Either because the machine does not have the required amount of RAM to run those processes, or because the installed RAM is malfunctioning.

Rogue Wireless Networks:
    1. A rogue wireless access point is an unaithorized device set up to broadcast a wireless network, often using the same SSID as the legitimate network it is copying.
    2. Users may connect to this rogue network and have internet connection, but they will not have access to the original network's internal resources such as file shares because they are no longer connected to the proper segment.
    **This security issue concept is better covered in the CompTIA A+ Core 2 wireless security threats chapter**

MFA frequent  issues:
    MFA (Multifactor authentication) apps, often generate time-based one-time passwords (TOTP). These numeric codes rely on the smartphone's internal clock aligning precisely with the clock in the authentication servers.
    When someone travels internationally, the smartphone's internal clock may either automatically change itself or retain an incorrect offset because of network settings or manual changes. This discrepancy disrupts the code generation process on the authentication server's side, creating an invalid one-time password wuring login attempts.
    Before reinstalling an app or escalating these types of issues, a technician should always make sure to check on the device's internal clock and set a proper date and time.

A network-based remote installation tool allows IT teams to:
    - deploy images to multiple machines simultaneously over the network with minimal effort
    - handle different hardware classes through hardware-specific driver injection
    - apply custom images based on user groups through task sequences or deployment rules
    - maintian consistent configurations, reducing human error 

    Some of these tools are:
        - Windows Deployment Services 
        - SCCM (Microsoft System Center Configuration)
        - MDT (Microsoft Deployment Toolkit)


