## Notes taken from some practice exams I took for the test

### Concepts
**UIDs**:
    system UIDs range from 0 - 999.

AppArmor profiles are stored in /etc/apparmor.d/. Profile files define what resources an application can access. aa-enforce and aa-complain modes are similar to SELinux enforcing and permissive.
AppArmor is the default MAC (Mandatory Access Control) system on Ubuntu and SUSE. It uses profiles to confine applications. SELinux is default on RHEL/CentOS/Fedora.
SMACK and TOMOYO are other Linux security modules.

``-r`` tests if a file exists and is readable.
``-e`` tests for existence only.
``-f`` tests if it is a regular file.
``-x`` tests for executability.
File test operators are essential for shell scripting logic.

If a certificate authority fails to uphold their responsibilities when issuing certificates, they will have an issue where their authority is withdrawn, and their existing certificates are placed in a revocation list.

Webhooks are event-driven and can notify an application or system when a specific event occurs, such as CPU usage exceeding a threshold. This notification can trigger an automated workflow to scale resources, making them ideal for dynamic environments.

**x86_64/AMD64** is the 64-bit extension of the x86 architecture and is the most widely used architecture for modern servers. It supports backward compatibility with 32-bit applications, which meets the requirement for legacy software support. x86_64 can address more than 4GB of memory and is universally supported by Linux distributions. 

**x86** is a legacy 32-bit system that is not longer suitable for  modern server environments.It has a memory addressing limit of 4GB and does not support 64-bit applicationsm which are now standard in most server deployments.

**RISC-V** is a modular and customizable architecture, but it is not widely adopted to production environments.

**Standard permissions** provide a way for system administrators to enforce access levels on users for files and directories. Issues occur when the user does not habe appropriate access to these files and directories.

The use of **Special Characters** is discouraged when naming files and directories due to known issues they can cause in Linux environments. 

**Agentless monitoring** approaches are generally less robust and provide less comprehensive data than agent-based solutions.
Agentless Monitoring Tools rely on existing system protocols like SNMP and SSH to gather data without requiring additional software installation.

**Log Aggregation tools** are useful for analyzing logs but do not provide real-time health checks or detailed performance data.

Systemd .timer files can replace schedulers, such as cron. Schedulers permit administrators and users to specify when an event should occur.

The **Filesystem Hierarchy Standard**(FHS) creates a naming convention that helps administrators, users, and applications consistently find the files they seek.

The *default.target* unit file points to the selected target - either command line interface (CLI) referencing *multi-user.target* or graphical user interface (GUI) referencing *graphical.target.*

**Configuration Management** is the process of making sure that systems are set to match security and performance requirements.
**Provisioning** refers to deployment tasks, while configuration relates to defining settings after the deployment process is complete.

**Service Mesh** is a dedicated infrastructure layer managed by code that provides service-to-service interaction in a container environment.

---

### Commands

```bash
modload module param=value
```
```bash 
modprobe module param=value
```

Both insmod and modprobe accept module parameters in the form param=value. `modprobe` is preferred as it handles dependencies. Parameters can also be specified in /etc/modprobe.d/ files for persistent configuration.

**auditd** is the Linux audit daemon that records security-relevant envents to /var/log/audit/audit.log. Rules are added with auditctl and made persistent in /etc/audit/rules.d/. ausearch and aureport query and summarize the audit logs. 
*rsyslog and journald* handle general system messages, not the audit trail.

``crontab -l`` lists the current user's cron jobs. ``crontab -e`` edits them. /etc/crontab is the system cron file. User crontabs are restored in /var/spool/cron/ or /var/cron/tabs. 

*smartctl -a* displays comprehensive SMART information including health status, attributes, and error logs. SMART (Self-monitoring, Analysis, and Reporting Technology) predicts drive failutes. hdparm shos drive parameters but not SMART data.

``dhclient -r`` releases the current lease, and ``dhclient`` requests a new one. 
On systemd-networkd systems, use networkctl renew INTERFACE. Some distributions use dhcpcd instead of dhclient.

The noatime mount option disables the updating of access times (atime) on files when they are read. This reduces disk I/O and can significantly improve performance, expecially on systems with many file reads. This is commonly used on SSDs and database servers.

``/var/log/dmesg`` contains kernel ring buffer messages. journalctl -k shows kernel messages from systemd journal. 
``/var/log/boot.log`` may contain boot service messages but varies by distribution and configuration.

``nft list ruleset`` displays all nftables rules across all tables and chains. 
nft is the modern replacement for iptables. 
*nftables* uses a unified syntax for IPv4/IPv6 and has better performance than iptables.

The `/usr/share/zoneinfo/` directory contains the regional time zone files that Linux systems use to configure the system's time zone. These files are organized by region and are not raw text files but special files used by the system.

``swapon`` is used to activate a specific swap space. The ``swapon -a`` command activates all swap spaces listed in the ``/etc/fstab`` file.

To redirect the output of the ``ip a`` command and have it overwrite any existing data, you would use the ``ip a > {file_name}`` command. Using the ``<`` instead would read from a file instead of outputting to a file. Using the ``>>`` redirector appends the output to the file instead of overwriting it.

The ``|`` (pipe) operator sends the output of one command to another command if that previous command was successful.

The ``lsscsi`` command displays information about each drive. Data for each device is displayed on a separate line and includes the device name, manufacturer, model, etc.

The ``lsblk`` command displays information on storage devices of which the system is aware. The information includes the device name, capacity, and mount point(if configured).

The ``blkid`` command displays known information on the partitions. One particularly useful piece of information is the Universally Unique ID (UUID) of the partition.

The ``fcstat`` command displays information about existing Fibre Channel adapters. The technician typically uses theses adapters and storage-area network (SAN) solutions in conjunction. It also contains subcommands that provide additional detail, such as link statistics.

The ``fg`` command component is associated with managing job functions and represents foreground. Using the ``fg`` component, the technician can bring jobs the system is working out of sight back into sight.

``jobs`` are a subset of processes and refer specifically to any process the current user has started. Users can display processes they are running by using the ``jobs`` command.

The ``bg`` command components manages job functions and represents background. Using ``bg``, the user transitions the job to be out of sight. WHen working with Ctrl+Z, the user sends the job to the background using bg %[1].

The ``pidstat`` command is specifically designed to monitor performance statistics for individual processes. The ``-u`` option focuses on CPU usage, and the command ``pidstat -u 1 5`` will display CPU usage for individual processes every second for five intervals. This makes it the ideal tool for identifying which process is consuming excessive CPU resources.

The ``mpstat`` command is used to monitor overall CPU performance, not individual processes. While it provides detailed statistics about CPU usage, it does not break down resource usage by process.

The ``ps aux`` command provides a snapshot of all running processes and their resource usage at a single point in time. However, it does not provide continuous monitoring or allow to track CPU usage over intervals. This makes it less effective for identifying a process causing performance issues over time.

---

### Repository Management

Git excels at tracking and integrating changes during development, especially in the context of large, distributed software-development projects where many programmers work on different aspects of the same application.

**Git Commands**:
    ``git add .`` stages all changes in the current directory and subdirectories. 
    ``git commit -a`` commits all modified tracked files without explicit staging. 
    ``git push`` uploads commits to a remote repository.

Corrupted or incomplete metadata is a common repository misconfiguration issue and can prevent the system from resolving dependencies or fetching package information, leading to errors during package installation or updates.

---

### Package Managers

``dpkg -l`` lists installed packages on Debian/Ubuntu. This command is useful for generating a complete inventory of installed software. 
``dpkg -s <package-name>`` is specifically designed to display detailed information about a single package on a Debian-based system. It provides details such as the package's version, installation status, and a brief description, which directly satisfies the requirements of the scenario.
``apt`` show displays detailed information.
``rpm -qi`` shows information on RHEL/CentOS.
    the specific command depends on the distribution and package management system.
The command ``yum provides zsh`` displays the contents of the zsh package. Zsh is short for Z shell, the default command-line interface (CLI) shell for macOS. 

``sar`` without options and ``sar -u`` both display CPU utilization. -u explicitly specifies CPU activity. ``sar -P ALL`` shows per-CPU statistics.
**The sysstat package must be installed and enabled for sar to collect data.**

``cpio -iv < knowledgebase.cpio``. To extract the contents of the knowledgebase.cpio archive, you would use this command. The `iv` option is used to copy files into the filesystem (restore files) from an archive. The < redirector reads the contents of the knowledgebase.cpio archive.

``cpio -ov < knowledgebase.cpio``. The `ov` option is used to create an archive, not extract the files.

``echo $?`` displays the exit code from the previously executed command. In this case, a value of 1 would be displayed because the command failed. A 0 indicates no errors.

``fio`` is designed to simulate I/O workloads and provide detailed metrics like latency, throughput, and IOPS. This enables direct comparison of storage performance under realistic conditions.

The ``dmesg`` command prints any messages sent to the kernel's message buffer during and after system boot.

FILE MANIPULATION:
    The ``cat`` command displays the contents of a file. If multiple files are added to the commandm, the contents of each file will be displayed in a **single text stream**.
    The ``cut`` command removes sections from each line of a file.
    ``pr`` formats a text file for printing.
    ``nl`` places a line number in from of each line in a text file and sends the result to standard output.

The ``cargo.toml`` file is the configuration file for a Rust Project, and the ``[dependencies]`` section is wherer you define the external crates (dependencies) your project requires.

The ``cargo install`` command is used to install standalone binaries (executables) from crates, not to add dependencies to a project. Using this command would not add a specific dependency, and it would not modify the cargo.toml file.

---

### Protocols

*NTP* (Network Time Protocol) synchronizes system clocks over a network. The ntpd daemon or systemd-timesyncd service handles NTP pon Linux. Accurate time is critical for logging, authentication (Kerberos), and distributed systems. chrony is a newer alternative to ntpd.

An Access Control List (ACL) is a list of permissions attached to an object. System administrators can use ACLs when the traditional file permission concept does not suffice and can lead to issues when users are not on the ACL.

Low Input/Output Operations per Second (IOPS) indicate a faulty drive or data bottlenecks when moving/retrieving the data.

The systemd management system includes a very robust journaling and logging component that can be useful for understanding system and application crashes. The systemd journal is a different and infependent service from rsyslog, which is the traditional Linxu log file service.
        
``NFS`` is specifically designed for environments where Linux clients access Linux servers. It is the preferred protocol in homogeneous Linux environments because it offers seamless integration and compatibility.

In mixed environments with both Windows and Linux systems, the ``SMB`` protocol is the better choice because it is compatible with both operating systems.

``PXE`` uses the **Trivial File Transfer Protocol (TFTP)** to transfer boot files from the server to the client.

The primary Linux task scheduler is ``cron``. This tool references a crontab file to determine whether tasks assigned to a specific minute exist. A system-wide crontab file is located at ``/etc/crontab``, and a per-user crontab is at ``/var/spool/cron/crontabs``.

*Chrony* is a modern implementation of NTP that supports secure communication using **Transport Layer Security (TLS)**. By omplementing Chrony with NTP over TLS, you ensure that time synchronization is both accurate and secure, resolving any issue of insecure protocols while maintaining consistency accross servers.

---

### Docker

RUN executes commands during the image build, creating new layers.
CMD provides defaults for running containers. 
ENTRYPOINT configures the container as an executable. 
Multiple RUN commands can be combined with && to reduce layers.

**Container registries** are a critical part of the DevOps infrastructure, enabling continuous integration and continuous deployment (CI/CD) by providing a standardized and accessible location where automation and orchestration tools pull images without human intervention.
Some organizations grow beyond the multicontainer environments provided by Docker, which builds multicontainer clusters using the Compose tool. Compose can be translated into something Kubernetes can understand, allowing for an easy transition into a larger, orchestrated container environment.

---

### Processes

``zip -e`` creates encrypted zip archives. ``gpg -c`` (symmetric) encrypts any file with a password. tar itself does not support encryption directly but can piped to gpg. For string encryption, prefer gpg over zip encryption.

**gzip**:
    To preserve the timestamp and original filename when compressing a file with gzip, you would use the ``-N`` option.
    the ``-n`` option in gzip omits the original file and timestamp.
    The ``-v`` option in gzip displays the name and percentage reduction of the compressed or decompressed file. An abreaviation of *verbose*.
    The ``-d`` option in gzip decompresses the file.

The ``sudo kill -9 <PID>`` command send the SIGKILL(Signal 9) to the process, which immediately and forcefully terminates it. This is the appropriate action when a process is unresponsive and consuming excessive resources, a it bypasses the process's ability to handle the termination gracefully.
The ``sudo kill -15 <PID>`` command sends the SIGTERM(Signal 15) to the process, which requests a graceful shutdown. While this is the preferred method for terminating processes, it may not work if the process is unresponsive.
The ``sudo renice -10 <PID>`` command adjusts the priority level of the process to make it more CPU-intensive(closer to -20). While this might improve the performance of a critical process. It does not terminate the process.

**Systemd** allows processes to start in parallel, which improves system startup efficiency. **Systemd** actually uses control groups (cgroups) to organize resources hierarchically. Systemd calls these collected sets of processes "control groups", so cgroups are an integral part of systemd, not something it eliminates.

The **systemd** command to manage startup options is **systemctl**. This command relies on the command subcommand argument syntax. One subcommand of systemctl is **mask**, which prevents a service from being started by any other service. Another subcommand of **systemctl** is **status**, which displays the current status of the service or daemon.
