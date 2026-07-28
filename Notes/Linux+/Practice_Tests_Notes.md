## Notes taken from some practice exams I took for the test

**UIDs**:
    system UIDs range from 0 - 999.

AppArmor profiles are stored in /etc/apparmor.d/. Profile files define what resources an application can access. aa-enforce and aa-complain modes are similar to SELinux enforcing and permissive.

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

---

**Protocols**:
    *NTP* (Network Time Protocol) synchronizes system clocks over a network. The ntpd daemon or systemd-timesyncd service handles NTP pon Linux. Accurate time is critical for logging, authentication (Kerberos), and distributed systems. chrony is a newer alternative to ntpd.
