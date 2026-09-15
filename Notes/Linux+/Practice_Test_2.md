# Notes
---
***This is a separate set of notes for the final practice test which includes more questions than the others and shows better the kind of questions you would get on the actual exam.***

---

A Tipical Multifactor Process:
    The user types in a password on their Linux Workstation and the System Security Services Daemon (sssd) connects the local system to remote authentication services, in this case, Microsoft's Active Directory services using Lightweight Directory Access Protocol (LDAP). The system then prompts the user for a one-time password (OTP), which is a password that either expires after the first use, within a short time period or both. 

Verifying and correcting the syntax of the repository configuration file, ensuring the URLs point to trusted and up-to-date repositories, is the best course of action because misconfigured repository files often lead to software installation failures or dependency issues. By verifying and correcting the syntax of the repository configuration file, you ensure the package manager can access the correct and trusted repositories to resolve dependencies and install the required software. This approach directly addresses the root cause of the problem.

Manually downloading packages is time-consuming, error-prone, and does not resolve the underlying issue with the repository configuration. Additionally, it increases the risk of installing untrusted or incompatible software.

Accurate date and time settings are critical for system logs, scheduled tasks, and time-sensitive operations. Setting the date and time does not directly affect Internet connectivity.

---

**Problem 1**:
    You are a system administrator tasked with setting up a Linux server for a group of interns who will be testing applications in a controlled environment.
    To ensure Security, you want to restrict their access to only a limited set of commands and prevent them from making unauthorized changes to the system.
    Answer would be to configure the interns' accounts to use the /bin/rbash shell and create a directory with symbolic links to allowed commands. The /bin/rbash shell (restricted Bash) limits the interns' ability to execute unauthorized commands or access system-critical files. By creating symbolic links in a new directory with only the allowed commands and setting the PATH variable to this directory, you can ensure that the interns operate in a controlled environment.

---

The commands ``w`` and ``who`` display all current users in a machine. This is commonly used by server administrators when they need to know who is connected in case they need to get noticed of an update or restart.

Low throughput occurs when the bandwidth of the storage device is lower than expectations, which directly impedes the movement of data to and from the storage drive. 
Low input/output operations per second (IOPS) indicate a faulty drive or data bottlenecks when moving/retrieving the data.

---

**Problem 2**:
    What command should you use to make nstevens the owner of all of the files and directories within the /docs directory?
    *Answer*:
        ``chown -R nstevens /docs``. The -R option tells ``chown`` to act recursively on all files and directories in the specified location.

---

To make FTP accessible to external users on a server through the perimeter network, a security engineer needs to open the appropriate port (21) in the firewall's configuration for the designated zone (``dmz``). This allows FTP traffic to pass through the firewall to servers in the DMZ, enabling file transfers without exposing other internal network resources.

Normally, the ``touch`` command is used for creating new files, but it can also be used for modifying the last accessed times to the current time of executing the command.

The ``/etc/ssh/ssh_config`` file defines Secure Shell (SSH) client settings and usually is not customized. This file has many configuration options (most of which are security-oriented). Common SSH server configuration with the ``/etc/ssh/ssh_config`` include changing ports, preventing the root user from connecting over the network via SSH, and requiring key-based authentication.

---

**Problem 3**:
    A system administrator notices that a user ``jdoe``, is unable to log in to a Linux server. Upon investigation, the administrator finds multiple failed login attempts for the account in the system logs.
    The administrator confirms that the account exists in the /etc/passwd file and that a hashed password exists in the /etc/shadow file.
    What should the administrator do next to resolve the issue?
        *Explanation*:
            The scenario mentions multiple failed login attempts, which could trigger a lockout policy enforced by Pluggable Authentication Modules (PAM). The administrator should check the PAM configuration to confirm whether the account is locked due to too many failed login attempts. This step aligns with troubleshooting best practices by addressing the root cause of the issue before taking further action.

---

XFS is more commonly used than ext4 or any other file system when it comes to storing data, since it is able to read a maximum of 8 exbibytes (~9 trillion GB).

**Log Aggregation**:
    Log Aggregation involves collecting and centralizing log files from multiple systems into a single location. This simplifies analysis, storage, and compliance with regulatory requirements, as administrators can access all logs in on place.
    Log Aggregation does not inherently compress log files. While compression may be part of log management, aggregation focuses on centralizing logs, not reducing their size. This tool does not replace monitoring tools. Instead, it compliments them by centralizing log data, which monitoring tools can then analyze for performance, security, or troubleshooting purposes.
    Log Aggregation does not handle the deletion of old log files. Tools like logrotate are responsible for managing log file rotation and deletion, whereas log aggregation focuses on centralizing logs for analysis and storage.

The ``awk`` command performs pattern matching on files. Its basis is on the AWK programming language. The awk keyword follows the pattern, the action to be performed, and the file name.

---

**Problem 4**:
    A system administrator is troubleshooting a service that fails to start during boot. Upon reviewing the ``.service`` unit file, they notice the following configuration: ``[Unit] Requires=network.target After=network.target`` The administator suspects the issue lies in the dependency configuration.
    Based on this Configuratio, what is the MOST likel cause of the service failing to start?
    Answer:
        The ``Requires=network.target`` directive ensures the service will fail if the network is unavailable.
    Explanation:
        The ``Requires=`` directive creates a hard dependency, meaning the service will fail to start if the ``network.taget`` is not available. This is the most likely cause of the issue, as the service dependent on the network being available, and any failure in the network target will prevent the service from starting. 
        The ``After=`` directive ensures that the service starts only after the ``network.target`` is available. Removing this directive could cause the service to attempt to start before the network is ready, which would likely lead to additional issues.

---

``/usr/lib/`` is a read-only directory that stores small programs and files accessible to all users. This includes object libraries and internal binaries that executable programs need.
``/sys`` is a virtual file system (VFS), and it primarily stores information about devices. For example, ``/sys/block/`` includes links to devices stored in various subdirectories under the ``/sys/devices`` location, which presents a hierarchy of devices in the kernel.
``/proc`` is another VFS that represents continually updated kernel information to the user in a typical file format.

---

**Problem 5**:
    You are managing a Linux environment where 50 employees need access to a shared directory located on a remote NFS server.
    The shared directory is rarely accessed, and you want to minimize the load on the remote server by ensuring that connections are only established when users access the directory.
    You decide to configure AutoFS to handle this.
    After installing and enabling the AutoFS service, you create the following entry in the ``/etc/auto.master`` file:``/mnt/shared /etc/auto.shared``
    You then create the /etc/auto.shared file with the following content:``shared -fstype=nfs 192.168.1.100:/shared``
    After restarting the AutoFS service, you notice that the shared directory is not accessible when users attempt to navigate to ``/mnt/shared``.
    What is the issue?
    *Answer* - The ``/mnt/shared`` directory does not exist on the local system.
    *Explanation* - AutoFS requires the mount point directory to exist on the local system. If the directory is missing, AutoFS cannot mount the remote NFS share when users attempt to access it. Creating the repository will resolve the issue.

---

**Kerberos** generates keys during the authentication process. These keys are used to securely access network services, ensuring secure communication and single sign-on capabilities. Kerberos only provides authentication, not authorization. Authorization, which determines what resources a user can access, is managed by other security mechanisms like Linux permissions or access control lists (ACLs). 
Kerberos does not replace LDAP or other directory services. Instead, it can work alongside LDAP to provide authentication while LDAP handles directory services and user information.

