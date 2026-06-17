###Security Goals
    Defining security goals is a useful way of evaluating your environment. System security attempts to satisfy three primary goals: confidentiality, integrity, and availability. Security professionals refer to this collection of goals as the CIA Triad.
    **Hardening Servers**:
        The **principle of least privilege** guides many hardening techniques. The principle states that the users and services should be grantes as little access to resources as possible while still allowing them to function. In other words, if a user only needs read accsss to a file, do not grant them both read and write. If a service is misconfigured to allow access to a user who should not have it, the system is vulnerable to issues such as service disruptions and data breaches, particularly from insider threats.
        
        Hardening Steps:
            - **Integrate strong physical security**: Enforce restricted areas, require guest badges, ensure doors lock properly, and monitor physical access.
            - **Implement security scans**: Utilize vulnerability scanners and network tools such as Nmap to automate security auditing and ensure compliance.
            - **Comfigure system logging**: Configure the `rsyslog` and `logrotate` services to log significant system and application events. Log system access by the root account. Review the `/var/log` directory regularly. Use `journalctl` to review security events.
            - **Review and audit suspicious activity**: Log access by the root user account, and check for potential breaches in authentication logs.
            - **Set a strong default umask**: Configure an appropriate set of default permissions by using `umask` to enforce the principle of least privilege.
            - **Manage file access**: Carefully configure permissions ad access control lists (ACLs) according to the priciple of least privilege, and utilize SELinux.
            - **Configure the host firewall**: Configure the firewall to enforce the principle of least privilege on network connectivity.
            - **Configure secure SSH connectivity**: Configure the SSH servicee to deny root logins through network connections, display warning banners to remote users, disallow blank passwords, and require key-based authentication.
            - **Detect and avoid service misconfiguration**: Misconfigured services represent a severe threat to security. Use automated configuration management tools like Ansible to ensure settings remain correct anddo not change unexpectedly.
            - **Disable and remove insecure services**: Carefully audit for running services that become unnecesary as the server's roles changes throughout its life cycle. Remove unnecesary services with tools such as the DNF and APT package managers. Mask services with hte systemctl command.
            - **Secure Service Accounts**: Audit service account stored in `/etc/passwd` to ensure they do not have shell privileges that would permit privilege escalation. Block shell access by placing `/sbin/nologin` in the account's shell field of the `/etc/passwd` file.
            - **Enforce strong password requirements**: Enforce string password requirements by using the **chage** command.**Pluggable Authentication Modules (PAM)** also help enforce password settings.
            - **Remove unused software packages**: Remove unnecesary software with tools such as the DNF and APT package managers.
            - **Tune kernel parameters**: Tune kernel parameters to match the server's roles, installed services, network capabilitiesm performance requirements, and service levels.
            - **Automate updates**: Automate the application of patches and audit the results to ensure all systems receive the appropriate updates.
            - **Avoid unsecure access services**: Remove services like Telnet, **File Transfer Protocol (FTP)**, and **Trivial File Transfer Protocol (TFTP)** that do not encrypt name and password information during network communications.
            - **Backport patches for older applications**: Some older applications benefit from newer patches that add updated security options or enable new features. Carefully test and apply these patches to maintain security settings.
        
---

###Pluggable Authentication Modules (PAM)
    A *PAM* defines the underlying framework and centralized authentication method leveraged by authentication services like Kerberos and Lightweight Directory Access Protocol (LDAP). It provides a common mechanism for many different authentication services and applications.
    Using PAM to simplify authentication also helps administrators by making it easier to set up authentication rules for all applications and services on the system. This is better than having to create different rules in various formats for each service. Developers can also write their own PAM modules to support specific authentication and authorization functions within an app.
    
    ###PAM Configurations
        Linux stores PAM configuration files in the `/etc/pam.d/` directory. Each PAM-aware service or application as its own file containing directives, formatted in the following way: `{module interface} {control flag} {module name} {module arguments}`.
        Each directive component helps define an authentication response. 
            - **Module Interface**: Defines functions of the authentication/authorization process contained within a module
            - **Control Flags**: Indicate what should be done upon the success or failure of the module
            - **Module Names**: Define the module to which the directive applies.
            - **Module Arguments**: Additional options you can pass into the module.
        
        The four module interfaces are account, auth, password, and session.
            - **Account**: Checks to see whether a user is allowed access to something
            - **auth**: Verifies passwords and to set credentials (such as Kerberos tickets)
            - **password**: Changes passwords
            - **session**: Used when performing tasks in a user session that are required for access (such as mounting home directories).
        
        There are also four control flags.
            - When the *optional* flag is set, the module result is ignored.
            - The *required* flag mandates that the module result must be successful to continue theauthentication, and the user is notified when all tests in the module interfaces are finished. 
            - The *requisite* flag is the same as the required flag except for the requisite flag's directive to notify the user immediately upon failure.
            - The *sufficient* flag states that the module result is ignored upon failure.
