## Notes taken from some practice exams I took for the test

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

---

```bash
modload module param=value
```
```bash 
modprobe module param=value
```
Both insmod and modprobe accept module parameters in the form param=value. `modprobe` is preferred as it handles dependencies. Parameters can also be specified in /etc/modprobe.d/ files for persistent configuration.

*auditd* is the Linux audit daemon that records security-relevant envents to /var/log/audit/audit.log. Rules are added with auditctl and made persistent in /etc/audit/rules.d/. ausearch and aureport query and summarize the audit logs. 
*rsyslog and journald* handle general system messages, not the audit trail.

``crontab -l`` lists the current user's cron jobs. ``crontab -e`` edits them. /etc/crontab is the system cron file. User crontabs are restored in /var/spool/cron/ or /var/cron/tabs. 

*smartctl -a* displays comprehensive SMART information including health status, attributes, and error logs. SMART (Self-monitoring, Analysis, and Reporting Technology) predicts drive failutes. hdparm shos drive parameters but not SMART data.

``dhclient -r`` releases the current lease, and ``dhclient`` requests a new one. 
On systemd-networkd systems, use networkctl renew INTERFACE. Some distributions use dhcpcd instead of dhclient.

The noatime mount option disables the updating of access times (atime) on files when they are read. This reduces disk I/O and can significantly improve performance, expecially on systems with many file reads. This is commonly used on SSDs and database servers.

/var/log/dmesg contains kernel ring buffer messages. journalctl -k shows kernel messages from systemd journal. 
/var/log/boot.log may contain boot service messages but varies by distribution and configuration.

``nft list ruleset`` displays all nftables rules across all tables and chains. 
nft is the modern replacement for iptables. 
*nftables* uses a unified syntax for IPv4/IPv6 and has better performance than iptables.

---

**Git Commands**:
    ``git add .`` stages all changes in the current directory and subdirectories. 
    ``git commit -a`` commits all modified tracked files without explicit staging. 
    ``git push`` uploads commits to a remote repository.

---

``dpkg -l`` lists installed packages on Debian/Ubuntu. 
``apt`` show displays detailed information.
``rpm -qi`` shows information on RHEL/CentOS.
    the specific command depends on the distribution and package management system.

``sar`` without options and ``sar -u`` both display CPU utilization. -u explicitly specifies CPU activity. ``sar -P ALL`` shows per-CPU statistics.
**The sysstat package must be installed and enabled for sar to collect data.**

---

**Protocols**:
    *NTP* (Network Time Protocol) synchronizes system clocks over a network. The ntpd daemon or systemd-timesyncd service handles NTP pon Linux. Accurate time is critical for logging, authentication (Kerberos), and distributed systems. chrony is a newer alternative to ntpd.
        
---

**Docker**:
    RUN executes commands during the image build, creating new layers.
    CMD provides defaults for running containers. 
    ENTRYPOINT configures the container as an executable. 
    Multiple RUN commands can be combined with && to reduce layers.

---
