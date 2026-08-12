# Linux+ (XK0-005) Study Plan — Exam Aug 28, 2026

**Start:** Aug 11 | **Exam:** Aug 28 | **Days:** 17 | **Time:** 2-4 hrs/day (~45-60 hrs)

## Exam Domains (weighted by % of exam — study in this order)
| Domain | Weight | Priority |
|---|---|---|
| System Management | 32% | HIGH |
| Troubleshooting | 28% | HIGH |
| Security | 21% | MEDIUM |
| Scripting, Containers & Automation | 19% | MEDIUM |

**Strategy:** Practice-test-driven (your style) + daily hands-on. Everything you miss on a practice test → add to `Practice_Tests_Notes.md` (your current workflow) AND look up the full topic — don't just memorize the one question.

**Rule:** Pause A+, CySA+, Security+ until after Aug 28. Linux+ first.

---

## Phase 1 — System Management (32%) — Days 1-6

- [ ] D1: Boot process: BIOS/UEFI → GRUB2 → initramfs → systemd. Boot params (`single`, `emergency`, `init=/bin/bash`). GRUB config: `/etc/default/grub`, `grub-mkconfig` / `grub2-mkconfig`
- [ ] D2: Kernel modules: `lsmod`, `modprobe`, `insmod`, `rmmod`, `modinfo`, `/etc/modules`, `/etc/modules-load.d/`, `/etc/modprobe.d/` (param=value)
- [ ] D3: systemd: `systemctl` (start/stop/enable/mask), units, targets vs runlevels, journald (`journalctl -b`, `-u`, `-p`, `-k`), `/var/log/`
- [ ] D4: Storage: `fdisk`/`gdisk`/`parted`, filesystems (ext4, xfs, btrfs), `mkfs`, `mount`/`fstab` + options (`noatime`, `ro`, `nofail`), swap, `/dev` naming
- [ ] D5: LVM (pv/vg/lv: `pvcreate`, `vgcreate`, `lvcreate`, `lvextend`, `resize2fs`), RAID levels, `df`/`du`/`blkid`/`lsblk`, `smartctl`, `fio`, `iostat`
- [ ] D6: Package mgmt: apt/dpkg + yum/dnf/rpm + zypper (install, query, provide, repo problems), `tar`/`cpio`/`zip`/`gpg`, `git` basics (add/commit/push/branch/merge)

**Practice test after D6** → log misses.

---

## Phase 2 — Troubleshooting (28%) + Security (21%) — Days 7-12

- [ ] D7: Troubleshooting methodology + boot recovery (rescue/emergency mode, repairing fs with `fsck`), kernel ring buffer (`dmesg`), `systemctl` failure diagnosis, stuck services
- [ ] D8: Network troubleshooting: `ping`, `tracepath`/`traceroute`, `ss`/`netstat`, `dig`/`host`, `ip`, `nmap`, `tcpdump`, DNS/DHCP/connectivity issues. **Review your existing `Monitor_Network_Traffic.md` + `Manage_Network_Settings.md`**
- [ ] D9: Storage/perf troubleshooting: full disk, inode exhaustion, slow I/O (IOPS), CPU/mem (`top`, `ps`, `free`, `vmstat`, `sar`, `ulimit`), process mgmt (`kill`, `nice`, `renice`, `ps` options)
- [ ] D10: Security — users/groups: `/etc/passwd`/`/etc/shadow`/`/etc/group`, UID ranges (0-999 system), `useradd`/`usermod`/`passwd`, sudo rules, PAM basics
- [ ] D11: Security — permissions: `chmod`/`chown`/`chgrp`, umask (022, 077, 002, 027), special bits (setuid/setgid/sticky), ACLs (`getfacl`/`setfacl`). **Review `Harden_a_Linux_System.md`**
- [ ] D12: Security — SELinux vs AppArmor (modes: enforcing/permissive/complaining; `getenforce`, `sestatus`, `aa-status`; profiles in `/etc/apparmor.d/`), firewalls: `ufw`, `firewalld`/`firewall-cmd`, `nftables` vs iptables, GPG/openssl encryption. **Review `Set_Up_Remote_Administrative_Access.md` (SSH hardening)**

**Practice test after D12** → log misses.

---

## Phase 3 — Scripting, Containers & Automation (19%) — Days 13-15

- [ ] D13: Bash scripting: shebang, variables, `$?`, `$#`, `$@`, conditionals, `[ -e/-f/-r/-w/-x ]` test operators, loops, functions
- [ ] D14: Automation: cron (`crontab -l/-e`, `/etc/crontab`, `/var/spool/cron`), at, systemd timers
- [ ] D15: Containers: images vs containers, Dockerfile (RUN/CMD/ENTRYPOINT), `docker` commands, orchestration basics, Podman. **Review `Managing_Containers_in_Linux/`** + fill gaps

---

## Phase 4 — Final Week — Days 16-17

- [ ] D16: **Full practice exam(s)** — simulate real exam, timed. Every miss → note + lookup
- [ ] D17 (Aug 27): Review all notes (especially `Practice_Tests_Notes.md` + `Common_Questions.md`). Flashcard weak spots. No new topics.

**Aug 28:** EXAM DAY — light review only, sleep, eat before.

---

## Daily Routine (2-4 hrs)
1. **10 min** — review yesterday's practice-test misses
2. **60-90 min** — topic study (per checklist above), take notes in your style
3. **30-60 min** — hands-on: create a VM or container and DO the commands. You can't answer what you haven't run. (Even 15 min of `systemctl`, `modprobe`, `lvextend`, `setfacl` beats passive reading)
4. **20-30 min** — practice questions on that topic; log all misses into `Practice_Tests_Notes.md`

## Biggest gap alerts (based on your current notes)
Your notes cover: hardening (partial), SSH, network settings/monitoring, containers, misc practice facts.
**Missing (highest exam value):**
- [ ] Boot process / GRUB / recovery — likely on every exam
- [ ] systemd & journald specifics
- [ ] LVM + filesystem commands
- [ ] SELinux/AppArmor details (you have a bit in practice notes)
- [ ] Firewall config commands (`ufw`, `firewall-cmd`, `nft`)
- [ ] Bash scripting syntax (test operators, `$?` you already have)
- [ ] Full user/permission management
