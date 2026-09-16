# CompTIA Linux+ XK0-005 Full Practice Exam

**Questions:** 40  
**Coverage:** System Management, Security, Scripting/Containers/Automation, and Troubleshooting  
**Status:** Graded on 2026-09-15

## Instructions

- Mark your choice by changing `[ ]` to `[X]`.
- Single-answer questions require exactly one selection.
- Multiple-response questions state exactly how many answers to select.
- Each review section now records the result, rationale, and relevant XK0-005 objective.
- This practice exam uses an approximate XK0-005 domain weighting: 13 System Management, 8 Security, 8 Scripting/Containers/Automation, and 11 Troubleshooting questions.

---

## System Management

### Question 1 of 40 - Single answer

Which directory is intended to contain variable data such as system logs, mail spools, and package caches?

- [ ] **A.** `/etc`
- [ ] **B.** `/var`
- [X] **C.** `/usr`
- [ ] **D.** `/boot`

#### Grading and Explanation

**Result:** Incorrect. You selected **C**; the correct answer is **B**.

**Why B is correct:** `/var` contains variable data that changes during normal system operation, including logs, spool files, and package caches.

**Why the other options are not:** **A** `/etc` stores host configuration files. **C** `/usr` contains mostly shareable, static programs, libraries, and documentation. **D** `/boot` contains bootloader files, kernels, and initramfs images.

**Objective:** 1.1 - Summarize Linux fundamentals (Filesystem Hierarchy Standard).

---

### Question 2 of 40 - Single answer

A Linux server must boot into a local maintenance environment with a root shell and only essential services. Which kernel parameter can be added to the GRUB boot entry to boot into the systemd rescue target?

- [X] **A.** `systemd.unit=rescue.target`
- [ ] **B.** `systemd.unit=graphical.target`
- [ ] **C.** `quiet`
- [ ] **D.** `rd.break`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `systemd.unit=rescue.target` tells systemd to boot the rescue target, which provides a local maintenance environment with essential services and a root shell.

**Why the other options are not:** **B** boots the graphical target. **C** only reduces boot-message output. **D** interrupts boot in the initramfs before the normal root filesystem and systemd rescue target are started.

**Objective:** 1.1 - Summarize Linux fundamentals (basic boot process and recovery).

---

### Question 3 of 40 - Single answer

An administrator must copy `/srv/inventory/` to `backup.example.com` each night. The transfer must preserve permissions and timestamps, transfer only changed files, and remove destination files that no longer exist at the source. Which command is best?

- [ ] **A.** `scp -r /srv/inventory backup@backup.example.com:/archives/inventory`
- [X] **B.** `rsync -a --delete -e ssh /srv/inventory/ backup@backup.example.com:/archives/inventory/`
- [ ] **C.** `cp -a /srv/inventory/ backup@backup.example.com:/archives/inventory/`
- [ ] **D.** `tar -cf inventory.tar /srv/inventory/`

#### Grading and Explanation

**Result:** Correct. You selected **B**.

**Why B is correct:** `rsync -a` preserves directory metadata, `--delete` removes obsolete destination files, and rsync transfers only changed data. `-e ssh` provides the remote transport; the trailing slash copies the contents of the source directory.

**Why the other options are not:** **A** copies recursively but lacks rsync's delta transfer, archive behavior, and deletion synchronization. **C** is a local-copy command and cannot use an SSH destination. **D** creates a local archive but does not perform the required remote synchronization.

**Objective:** 1.2 - Given a scenario, manage files and directories (copying files between systems).

---

### Question 4 of 40 - Single answer

An archive named `logs.cpio` was created with `cpio`. Which command extracts its contents into the current directory while creating needed directories?

- [ ] **A.** `cpio -idv < logs.cpio`
- [X] **B.** `cpio -ov > logs.cpio`
- [ ] **C.** `tar -xzf logs.cpio`
- [ ] **D.** `gzip -d logs.cpio`

#### Grading and Explanation

**Result:** Incorrect. You selected **B**; the correct answer is **A**.

**Why A is correct:** `cpio -i` selects copy-in mode to extract an archive, and `-d` creates required directories. `-v` only enables verbose output.

**Why the other options are not:** **B** uses `-o` for copy-out mode, which creates an archive rather than extracts one. **C** expects a tar archive, not a cpio archive. **D** only decompresses gzip data and does not extract a cpio archive.

**Objective:** 1.2 - Given a scenario, manage files and directories (archiving and backup).

---

### Question 5 of 40 - Select 2 answers

A blank disk, `/dev/sdb`, must be added to the existing LVM volume group `vg_data`. Using the explicit two-step LVM physical-volume workflow, which two actions should the administrator perform? No filesystem or partition is required on the disk.

- [X] **A.** Run `pvcreate /dev/sdb`.
- [X] **B.** Run `vgextend vg_data /dev/sdb`.
- [ ] **C.** Run `vgcreate vg_data /dev/sdb`.
- [ ] **D.** Run `mkfs.xfs /dev/sdb`.
- [ ] **E.** Run `lvcreate -L 20G /dev/sdb`.

#### Grading and Explanation

**Result:** Correct. You selected **A, B**.

**Why A and B are correct:** The explicit LVM workflow first initializes `/dev/sdb` as a physical volume with `pvcreate`, then adds it to the existing volume group with `vgextend vg_data /dev/sdb`.

**Why the other options are not:** **C** creates a new volume group rather than extending `vg_data`. **D** creates a filesystem, which is not part of preparing an LVM physical volume. **E** creates an LV and requires a volume group name, not a raw disk path.

**Objective:** 1.3 - Given a scenario, configure and manage storage (LVM physical volumes and volume groups).

---

### Question 6 of 40 - Single answer

A database server has four 1 TB disks. It needs strong random I/O performance and must survive one disk failure. Which RAID level provides the best fit, and how much usable capacity will it provide?

- [ ] **A.** RAID 0 with 4 TB usable
- [ ] **B.** RAID 1 with 1 TB usable
- [ ] **C.** RAID 5 with 3 TB usable
- [X] **D.** RAID 10 with 2 TB usable

#### Grading and Explanation

**Result:** Correct. You selected **D**.

**Why D is correct:** RAID 10 stripes mirrored pairs, providing strong random I/O performance and redundancy. Four 1 TB disks yield 2 TB usable capacity and can survive a single disk failure.

**Why the other options are not:** **A** RAID 0 provides 4 TB but no fault tolerance. **B** a four-way RAID 1 mirror provides 1 TB and lacks RAID 10's striping performance. **C** RAID 5 provides 3 TB and single-drive fault tolerance but incurs parity-write overhead, making it a weaker fit for random-write databases.

**Objective:** 1.3 - Given a scenario, configure and manage storage (RAID levels).

---

### Question 7 of 40 - Single answer

An administrator needs to add a temporary default route through `192.0.2.1` on interface `enp0s3`, without editing persistent network configuration. Which command is correct?

- [X] **A.** `ip route add default via 192.0.2.1 dev enp0s3`
- [ ] **B.** `ip addr add default via 192.0.2.1 dev enp0s3`
- [ ] **C.** `route -n 192.0.2.1 enp0s3`
- [ ] **D.** `nmcli device show enp0s3 default 192.0.2.1`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `ip route add default via 192.0.2.1 dev enp0s3` adds a runtime default route. It is not persistent unless configuration is also changed.

**Why the other options are not:** **B** attempts to configure an IP address, not a route. **C** uses a display-oriented legacy command with invalid syntax for this task. **D** displays NetworkManager device information and does not add a route.

**Objective:** 1.4 - Given a scenario, configure and use the appropriate networking tools or settings (routing).

---

### Question 8 of 40 - Single answer

Which local file provides static hostname-to-IP-address mappings that can be used before a DNS query, depending on the Name Service Switch configuration?

- [ ] **A.** `/etc/hosts`
- [ ] **B.** `/etc/resolv.conf`
- [ ] **C.** `/etc/hostname`
- [X] **D.** `/etc/nsswitch.conf`

#### Grading and Explanation

**Result:** Incorrect. You selected **D**; the correct answer is **A**.

**Why A is correct:** `/etc/hosts` stores local static mappings from hostnames to IP addresses. Whether it is checked before DNS depends on the `hosts:` entry in the Name Service Switch configuration.

**Why the other options are not:** **B** configures DNS resolver servers. **C** stores the local system's hostname. **D** controls the lookup order, but does not contain hostname-to-IP mappings itself.

**Objective:** 1.4 - Given a scenario, configure and use the appropriate networking tools or settings (name resolution).

---

### Question 9 of 40 - Single answer

The `nginx.service` unit must be stopped immediately and prevented from starting manually or through dependencies until an administrator intentionally restores it. Which sequence is correct?

- [X] **A.** `systemctl stop nginx.service && systemctl mask nginx.service`
- [ ] **B.** `systemctl disable nginx.service`
- [ ] **C.** `systemctl reset-failed nginx.service`
- [ ] **D.** `systemctl isolate rescue.target`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `systemctl stop` stops the running service; `systemctl mask` prevents any manual or dependency-based activation until the unit is unmasked.

**Why the other options are not:** **B** prevents normal startup at boot but still permits manual or dependency activation. **C** only clears a failed state. **D** changes the current system target unnecessarily and does not specifically mask NGINX.

**Objective:** 1.5 - Given a scenario, configure and manage system services (systemd service management).

---

### Question 10 of 40 - Single answer

An administrator needs `/usr/local/sbin/rotate-reports` to run once at 22:30. Which command schedules the one-time task?

- [ ] **A.** `echo "/usr/local/sbin/rotate-reports" | at 22:30`
- [X] **B.** `crontab -e` followed by `30 22 * * * /usr/local/sbin/rotate-reports`
- [ ] **C.** `systemctl enable rotate-reports.service`
- [ ] **D.** `sleep 22:30 && /usr/local/sbin/rotate-reports`

#### Grading and Explanation

**Result:** Incorrect. You selected **B**; the correct answer is **A**.

**Why A is correct:** `at` queues a command for one execution at the specified time.

**Why the other options are not:** **B** creates a cron job that runs daily at 22:30, not once. **C** merely enables a service at boot. **D** is not a valid way to express a clock time to `sleep` and depends on a running shell session.

**Objective:** 1.5 - Given a scenario, configure and manage system services (task scheduling).

---

### Question 11 of 40 - Single answer

A source package uses the traditional GNU Autotools build process and does not have a distribution package available. Which command sequence configures, compiles, and installs it?

- [X] **A.** `./configure && make && sudo make install`
- [ ] **B.** `make install && ./configure && make`
- [ ] **C.** `dnf install source-package.tar.gz`
- [ ] **D.** `gcc source-package.tar.gz -o application`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** Traditional GNU Autotools projects are normally configured with `./configure`, compiled with `make`, and installed with `make install` using administrative privilege when needed.

**Why the other options are not:** **B** attempts installation before configuration and compilation. **C** asks DNF to install a source archive as a package. **D** cannot compile a compressed source archive directly and bypasses the project's build configuration.

**Objective:** 1.6 - Given a scenario, build and install software.

---

### Question 12 of 40 - Single answer

On a RHEL-family system, an administrator must install the local RPM `acme-1.0.rpm` while resolving dependencies from configured repositories. Which command should be used?

- [X] **A.** `rpm -i acme-1.0.rpm`
- [ ] **B.** `dnf install ./acme-1.0.rpm`
- [ ] **C.** `apt install ./acme-1.0.rpm`
- [ ] **D.** `dpkg -i acme-1.0.rpm`

#### Grading and Explanation

**Result:** Incorrect. You selected **A**; the correct answer is **B**.

**Why B is correct:** `dnf install ./acme-1.0.rpm` installs the local RPM and uses enabled repositories to resolve and install dependencies.

**Why the other options are not:** **A** installs an RPM directly but does not resolve missing dependencies. **C** and **D** are Debian-family package tools and use `.deb` packages rather than RPMs.

**Objective:** 1.7 - Given a scenario, manage software configurations (package management).

---

### Question 13 of 40 - Select 2 answers

A Linux host will act as an IPv4 router. Which two actions enable IPv4 forwarding immediately and make the setting persistent across reboots?

- [X] **A.** Run `sysctl -w net.ipv4.ip_forward=1`.
- [ ] **B.** Add `net.ipv4.ip_forward=1` to `/etc/sysctl.d/99-router.conf`.
- [ ] **C.** Add `ip_forward=1` to `/etc/modprobe.d/router.conf`.
- [X] **D.** Run `ip route add default via 192.0.2.1`.
- [ ] **E.** Change the permissions of `/proc/sys/net/ipv4/ip_forward`.

#### Grading and Explanation

**Result:** Partial. You selected **A, D**; the required selections are **A, B**.

**Why A and B are correct:** `sysctl -w net.ipv4.ip_forward=1` changes the running kernel parameter immediately. A setting in `/etc/sysctl.d/99-router.conf` is loaded during boot, making the configuration persistent.

**Why the other options are not:** **C** configures kernel module behavior, not sysctl parameters. **D** adds a route but does not enable packet forwarding. **E** changes file permissions without setting the kernel parameter's value.

**Objective:** 1.7 - Given a scenario, manage software configurations (kernel runtime configuration).

---

## Security

### Question 14 of 40 - Single answer

Which condition is essential for a client to validate a TLS certificate presented for `https://portal.example.com`?

- [X] **A.** The certificate chains to a CA trusted by the client, and a Subject Alternative Name matches `portal.example.com`.
- [ ] **B.** The server's private key is copied into the client's trust store.
- [ ] **C.** The certificate has `localhost` as its Common Name.
- [ ] **D.** The certificate is not expired, regardless of its issuer or hostname.

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** A TLS client must be able to build a trust chain to a trusted certificate authority and verify that the requested hostname appears in the certificate's Subject Alternative Name.

**Why the other options are not:** **B** violates private-key security; a server private key must never be copied to clients. **C** does not match `portal.example.com`. **D** certificate expiration is only one validation requirement; issuer trust and hostname matching are also necessary.

**Objective:** 2.1 - Summarize the purpose and use of security best practices in a Linux environment (PKI and certificates).

---

### Question 15 of 40 - Select 2 answers

The `/tmp` directory is on its own writable filesystem. Which two `/etc/fstab` mount options directly reduce the risk from untrusted executable files and setuid/setgid binaries stored there?

- [X] **A.** `noexec`
- [X] **B.** `nosuid`
- [ ] **C.** `noatime`
- [ ] **D.** `rw`
- [ ] **E.** `exec`

#### Grading and Explanation

**Result:** Correct. You selected **A, B**.

**Why A and B are correct:** `noexec` blocks direct execution of files on the mounted filesystem. `nosuid` ignores setuid and setgid bits there, preventing those files from granting elevated privileges.

**Why the other options are not:** **C** `noatime` reduces access-time writes but does not provide this execution hardening. **D** `rw` allows writes and is unrelated to either protection. **E** explicitly permits execution, the opposite of `noexec`.

**Objective:** 2.1 - Summarize the purpose and use of security best practices in a Linux environment (filesystem hardening).

---

### Question 16 of 40 - Single answer

User `alice` must be added to the existing `developers` supplementary group without losing any of her current supplementary group memberships. Which command is correct?

- [ ] **A.** `usermod -G developers alice`
- [X] **B.** `usermod -aG developers alice`
- [ ] **C.** `groupadd -a developers alice`
- [ ] **D.** `passwd -a developers alice`

#### Grading and Explanation

**Result:** Correct. You selected **B**.

**Why B is correct:** `usermod -aG developers alice` appends `developers` to Alice's existing supplementary-group list. The `-a` flag is essential when used with `-G`.

**Why the other options are not:** **A** replaces all existing supplementary groups with `developers`. **C** is not valid `groupadd` syntax. **D** does not manage group membership.

**Objective:** 2.2 - Given a scenario, implement identity management (group membership).

---

### Question 17 of 40 - Single answer

A RHEL-family system uses `pam_faillock`. User `alice` is locked out after repeated failed password attempts, but her account is otherwise valid. Which command resets her failed-login tally?

- [ ] **A.** `faillock --user alice --reset`
- [ ] **B.** `passwd -u alice`
- [ ] **C.** `usermod -L alice`
- [X] **D.** `chage -E -1 alice`

#### Grading and Explanation

**Result:** Incorrect. You selected **D**; the correct answer is **A**.

**Why A is correct:** `faillock --user alice --reset` clears the failed-authentication tally maintained by `pam_faillock`, allowing the account to authenticate again.

**Why the other options are not:** **B** unlocks a password field that was administratively locked but does not clear a PAM failure tally. **C** locks the account. **D** removes an account-expiration date but does not reset failed-login tracking.

**Objective:** 2.2 - Given a scenario, implement identity management (PAM account lockout).

---

### Question 18 of 40 - Select 2 answers

`firewalld` is running. HTTPS must be allowed permanently in the `internal` zone, and the change must take effect immediately. Which two commands are required?

- [X] **A.** `firewall-cmd --permanent --zone=internal --add-service=https`
- [ ] **B.** `firewall-cmd --reload`
- [ ] **C.** `firewall-cmd --zone=internal --remove-service=https`
- [ ] **D.** `systemctl mask firewalld`
- [ ] **E.** `iptables -F`

#### Grading and Explanation

**Result:** Partial. You selected **A**; the required selections are **A, B**.

**Why A and B are correct:** **A** writes the HTTPS service rule to firewalld's permanent configuration for the `internal` zone. **B** reloads firewalld so that permanent configuration becomes active immediately.

**Why the other options are not:** **C** removes HTTPS instead of allowing it. **D** prevents firewalld from running. **E** flushes legacy iptables rules and neither updates firewalld's permanent configuration nor safely achieves the requirement.

**Objective:** 2.3 - Given a scenario, implement and configure firewalls (firewalld zones and permanent rules).

---

### Question 19 of 40 - Single answer

An SSH hardening policy requires password logins to be disabled while administrators authenticate using authorized public keys. Which `sshd_config` directive implements the password-authentication portion of this policy?

- [X] **A.** `PasswordAuthentication no`
- [ ] **B.** `PermitRootLogin no`
- [ ] **C.** `UsePAM yes`
- [ ] **D.** `AuthorizedKeysFile none`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `PasswordAuthentication no` disables SSH password authentication while allowing public-key authentication to remain available through authorized key files.

**Why the other options are not:** **B** only controls whether root can log in and does not disable passwords for other users. **C** enables PAM integration but does not itself disable password logins. **D** disables the authorized-key file location, preventing public-key authentication.

**Objective:** 2.4 - Given a scenario, configure and execute remote connectivity for system management (SSH hardening).

---

### Question 20 of 40 - Single answer

An auditor named `auditor` needs read and traverse access to the existing `/srv/reports` directory without changing its owner, group, or permissions for all other users. Assume the directory has no existing extended ACL and its group-mode bits already permit `rx`. Which command is best?

- [X] **A.** `setfacl -m u:auditor:rx /srv/reports`
- [ ] **B.** `chmod 755 /srv/reports`
- [ ] **C.** `chown auditor /srv/reports`
- [ ] **D.** `usermod -aG auditor root`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `setfacl -m u:auditor:rx /srv/reports` grants the named user read and traverse permissions through an access control list without changing standard ownership or broadening access for everyone.

**Why the other options are not:** **B** grants broad read and traverse access to all users. **C** transfers directory ownership to the auditor. **D** adds `root` to a group named `auditor`; it does not grant the user `auditor` access.

**Objective:** 2.5 - Given a scenario, apply the appropriate access controls (ACLs).

---

### Question 21 of 40 - Single answer

SELinux is enforcing. Apache must serve static content from `/srv/site`, but files there have the `default_t` context and normal UNIX permissions are already correct. Which sequence applies the appropriate persistent SELinux context?

- [ ] **A.** `chcon -R -t httpd_sys_content_t /srv/site`
- [ ] **B.** `semanage fcontext -a -t httpd_sys_content_t "/srv/site(/.*)?" && restorecon -Rv /srv/site`
- [X] **C.** `setenforce 0`
- [ ] **D.** `chmod -R 777 /srv/site`

#### Grading and Explanation

**Result:** Incorrect. You selected **C**; the correct answer is **B**.

**Why B is correct:** `semanage fcontext` creates a persistent SELinux file-context rule, and `restorecon` applies that rule to the existing directory tree. `httpd_sys_content_t` permits Apache to read static web content.

**Why the other options are not:** **A** changes the current context but can be undone by relabeling because it does not define a persistent policy rule. **C** disables SELinux enforcement rather than fixing the access control. **D** changes discretionary permissions only and does not resolve the SELinux context denial.

**Objective:** 2.5 - Given a scenario, apply the appropriate access controls (SELinux).

---

## Scripting, Containers, and Automation

### Question 22 of 40 - Single answer

A Bash script must exit with status 1 when `/var/lib/app/state` is not an existing regular file. Which block is correct?

- [X] **A.** `if [ ! -f "/var/lib/app/state" ]; then exit 1; fi`
- [ ] **B.** `if [ -d "/var/lib/app/state" ]; then exit 1; fi`
- [ ] **C.** `if [ ! -e "/var/lib/app/state" ]; then exit 1; fi`
- [ ] **D.** `if ! /var/lib/app/state; then exit 1; fi`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `-f` tests whether a path is an existing regular file. The leading `!` makes the script exit with status 1 when the path is absent or is not a regular file.

**Why the other options are not:** **B** tests whether the path is a directory and uses the wrong condition. **C** only tests whether a path exists, so a directory or another nonregular type would incorrectly pass. **D** attempts to execute the path as a command.

**Objective:** 3.1 - Given a scenario, create simple shell scripts (file test operators and exit codes).

---

### Question 23 of 40 - Single answer

A Bash script must loop over every filename passed to it, including filenames that contain spaces. Which loop handles the positional parameters correctly?

- [X] **A.** `for file in $@; do process "$file"; done`
- [ ] **B.** `for file in "$@"; do process "$file"; done`
- [ ] **C.** `for file in "$*"; do process "$file"; done`
- [ ] **D.** `for file in $(args); do process "$file"; done`

#### Grading and Explanation

**Result:** Incorrect. You selected **A**; the correct answer is **B**.

**Why B is correct:** `"$@"` expands to one separately quoted word for each positional parameter, preserving filenames that contain spaces or wildcard characters.

**Why the other options are not:** **A** leaves `$@` unquoted, causing word splitting and pathname expansion. **C** expands all arguments as one string. **D** invokes an unrelated `args` command and then performs unsafe command-substitution splitting.

**Objective:** 3.1 - Given a scenario, create simple shell scripts (positional parameters and quoting).

---

### Question 24 of 40 - Single answer

Which command starts an NGINX container in the background, names it `web`, and maps host TCP port 8080 to container TCP port 80?

- [ ] **A.** `podman run -d --name web -p 8080:80 nginx`
- [X] **B.** `podman exec -d --name web -p 8080:80 nginx`
- [ ] **C.** `podman run --name web -p 80:8080 nginx`
- [ ] **D.** `podman build -d --name web -p 8080:80 nginx`

#### Grading and Explanation

**Result:** Incorrect. You selected **B**; the correct answer is **A**.

**Why A is correct:** `podman run` creates and starts a container. `-d` detaches it, `--name web` assigns its name, and `-p 8080:80` maps the host port to the container port.

**Why the other options are not:** **B** runs a command in an existing container and cannot create one with these options. **C** reverses the required port mapping. **D** builds an image rather than starting a container.

**Objective:** 3.2 - Given a scenario, perform basic container operations (container networking and lifecycle).

---

### Question 25 of 40 - Single answer

An image is already tagged `registry.example.com/payments:1.2`. Which command publishes the image to that container registry?

- [ ] **A.** `podman pull registry.example.com/payments:1.2`
- [ ] **B.** `podman run registry.example.com/payments:1.2`
- [X] **C.** `podman push registry.example.com/payments:1.2`
- [ ] **D.** `podman build registry.example.com/payments:1.2`

#### Grading and Explanation

**Result:** Correct. You selected **C**.

**Why C is correct:** `podman push` uploads a tagged local image to the specified container registry, assuming the user has authenticated as needed.

**Why the other options are not:** **A** downloads an image from a registry. **B** creates a container from the local image. **D** builds an image from a build context and does not publish it.

**Objective:** 3.2 - Given a scenario, perform basic container operations (container image operations and registries).

---

### Question 26 of 40 - Single answer

An administrator made unstaged changes to `config.yml` and `README.md` in a Git repository, and no paths are currently staged. The administrator needs to commit only `config.yml` with message `Update configuration`. Which command sequence is correct?

- [X] **A.** `git add config.yml && git commit -m "Update configuration"`
- [ ] **B.** `git commit -a -m "Update configuration"`
- [ ] **C.** `git push config.yml "Update configuration"`
- [ ] **D.** `git clone config.yml && git commit -m "Update configuration"`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `git add config.yml` stages only that file, and `git commit -m` commits the staged change with the required message.

**Why the other options are not:** **B** stages every modified tracked file, including `README.md`. **C** pushes existing commits but does not stage or create one. **D** clones a repository and is not a way to stage a file.

**Objective:** 3.3 - Given a scenario, perform basic version control using Git (staging and commits).

---

### Question 27 of 40 - Select 2 answers

The generated file `build/output.log` was accidentally committed to a Git repository. It must remain on the administrator's local system but never be included in future commits. Which two actions are required?

- [X] **A.** Add `build/output.log` to `.gitignore`.
- [ ] **B.** Run `git rm --cached build/output.log`.
- [ ] **C.** Run `git clean -fd`.
- [X] **D.** Run `git reset --hard`.
- [ ] **E.** Run `git tag ignore`.

#### Grading and Explanation

**Result:** Partial. You selected **A, D**; the required selections are **A, B**.

**Why A and B are correct:** The `.gitignore` entry prevents new untracked copies from being added later. `git rm --cached build/output.log` removes the already tracked file from Git's index while retaining the local working-tree file; that removal must then be committed.

**Why the other options are not:** **C** deletes untracked files and does not remove a tracked path from the index. **D** discards committed and uncommitted work, potentially deleting the local file, and does not establish the ignore rule. **E** creates a tag and has no effect on ignored paths.

**Objective:** 3.3 - Given a scenario, perform basic version control using Git (`.gitignore` and the index).

---

### Question 28 of 40 - Single answer

An organization needs a declarative tool to provision cloud networks and virtual machines, track infrastructure state, and calculate changes before applying them. Which tool best fits this need?

- [X] **A.** Terraform
- [ ] **B.** Ansible
- [ ] **C.** rsync
- [ ] **D.** cron

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** Terraform declaratively provisions infrastructure, tracks state, and generates an execution plan that shows intended changes before they are applied.

**Why the other options are not:** **B** Ansible is primarily a configuration-management and automation tool. **C** synchronizes files. **D** schedules recurring commands.

**Objective:** 3.4 - Summarize common infrastructure-as-code technologies.

---

### Question 29 of 40 - Single answer

An organization runs many containerized microservices across multiple hosts. It needs automated placement, scaling, and recovery of container workloads. Which technology is designed for this use case?

- [X] **A.** Kubernetes
- [ ] **B.** Docker Compose
- [ ] **C.** cron
- [ ] **D.** rsync

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** Kubernetes is a container orchestration platform that automates workload placement, scaling, health recovery, and multi-host management.

**Why the other options are not:** **B** Docker Compose is intended primarily for defining multi-container applications, commonly on one host. **C** schedules commands but does not orchestrate containers. **D** copies files and does not manage workloads.

**Objective:** 3.5 - Summarize container, cloud, and orchestration concepts.

---

## Troubleshooting

### Question 30 of 40 - Single answer

`df -h /` reports that the root filesystem is 100% full, but `du -x /` accounts for far less data. An application was recently rotated or deleted. What is the most likely cause, and which command confirms it?

- [X] **A.** A deleted file is still open by a process; use `lsof +L1`.
- [ ] **B.** The filesystem has no inodes; use `df -i`.
- [ ] **C.** The root filesystem is not mounted; use `mount -a`.
- [ ] **D.** The superblock is corrupt; use `fsck` while mounted.

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** A process can keep a deleted file open, so its blocks remain allocated and count in `df` but the deleted path is not counted by `du`. `lsof +L1` finds open files whose link count is less than one.

**Why the other options are not:** **B** is diagnosed with `df -i` and normally leaves data-block capacity visible in `df -h`. **C** is impossible in this scenario because `/` is clearly mounted for `df` to report on it. **D** is not indicated by the symptoms, and filesystem checking must not be performed on a mounted read-write filesystem.

**Objective:** 4.1 - Given a scenario, analyze and troubleshoot storage issues (capacity usage).

---

### Question 31 of 40 - Single answer

`df -i /var` reports `IUse%` at 100%, while `df -h /var` still reports plenty of free disk space. What is the most likely cause?

- [ ] **A.** The filesystem has exhausted its inodes because it contains too many files.
- [X] **B.** The system's swap space is exhausted.
- [ ] **C.** The volume group has no free extents.
- [ ] **D.** The filesystem is mounted read-only.

#### Grading and Explanation

**Result:** Incorrect. You selected **B**; the correct answer is **A**.

**Why A is correct:** `df -i` reports inode usage. At 100%, the filesystem has no remaining inode entries, usually because it contains too many small files, even when data blocks remain available.

**Why the other options are not:** **B** swap is memory backing and is unrelated to filesystem inodes. **C** volume-group free extents affect LVM allocation, not inode availability in an existing filesystem. **D** a read-only mount would not cause inode usage to reach 100%.

**Objective:** 4.1 - Given a scenario, analyze and troubleshoot storage issues (inode exhaustion).

---

### Question 32 of 40 - Select 2 answers

Which two sources directly report the current synchronization and member state of software RAID array `/dev/md0`?

- [X] **A.** `mdadm --detail /dev/md0`
- [ ] **B.** `cat /proc/mdstat`
- [ ] **C.** `mdadm --create /dev/md0 --level=1 --raid-devices=2 ...`
- [X] **D.** `fsck /dev/md0`
- [ ] **E.** `smartctl -H /dev/sda`

#### Grading and Explanation

**Result:** Partial. You selected **A, D**; the required selections are **A, B**.

**Why A and B are correct:** `mdadm --detail /dev/md0` reports detailed array and member state. `/proc/mdstat` is the kernel's live summary of MD array synchronization and member status.

**Why the other options are not:** **C** creates an array and is destructive rather than diagnostic. **D** checks a filesystem but does not report MD RAID synchronization or member roles. **E** reports an individual disk's SMART health, not the current state of the MD array.

**Objective:** 4.1 - Given a scenario, analyze and troubleshoot storage issues (software RAID).

---

### Question 33 of 40 - Single answer

An ext4 filesystem on `/dev/vdb1` is unmounted and reports metadata errors. Which command is appropriate to force a check and attempt repair?

- [X] **A.** `e2fsck -f /dev/vdb1`
- [ ] **B.** `xfs_repair /dev/vdb1`
- [ ] **C.** `resize2fs /dev/vdb1`
- [ ] **D.** `mount -o remount,rw /dev/vdb1`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `e2fsck -f` is the ext-family filesystem checker. With the filesystem unmounted, it can force a consistency check and attempt repairs safely.

**Why the other options are not:** **B** applies to XFS, not ext4. **C** resizes an ext filesystem; it does not repair metadata corruption. **D** remounts a filesystem and does not check or repair it.

**Objective:** 4.1 - Given a scenario, analyze and troubleshoot storage issues (filesystem repair).

---

### Question 34 of 40 - Single answer

A server becomes slow several times per hour. The administrator needs to identify which processes consume CPU every second for five intervals. Which command is most appropriate?

- [X] **A.** `pidstat -u 1 5`
- [ ] **B.** `mpstat 1 5`
- [ ] **C.** `ps aux`
- [ ] **D.** `free -h`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `pidstat -u 1 5` reports per-process CPU utilization at one-second intervals for five reports, making intermittent CPU consumers visible.

**Why the other options are not:** **B** reports CPU statistics by processor, not process. **C** is a one-time process snapshot. **D** reports memory and swap statistics rather than CPU use by process.

**Objective:** 4.2 - Given a scenario, analyze and troubleshoot resource issues (CPU utilization).

---

### Question 35 of 40 - Single answer

Which command continuously reports runnable processes, memory, swap, and CPU statistics and is useful when diagnosing system-wide memory pressure?

- [X] **A.** `vmstat 1`
- [ ] **B.** `free -h`
- [ ] **C.** `df -h`
- [ ] **D.** `lspci`

#### Grading and Explanation

**Result:** Correct. You selected **A**.

**Why A is correct:** `vmstat 1` repeatedly reports run-queue, virtual-memory, swap, paging, and CPU statistics at one-second intervals, which helps identify system-wide memory pressure.

**Why the other options are not:** **B** provides a point-in-time memory summary. **C** reports filesystem space. **D** inventories PCI hardware.

**Objective:** 4.2 - Given a scenario, analyze and troubleshoot resource issues (memory and swap pressure).

---

### Question 36 of 40 - Single answer

On a traditionally configured Linux host, which file normally contains the `nameserver` entries used by the DNS resolver?

- [ ] **A.** `/etc/resolv.conf`
- [X] **B.** `/etc/hosts`
- [ ] **C.** `/etc/hostname`
- [ ] **D.** `/etc/services`

#### Grading and Explanation

**Result:** Incorrect. You selected **B**; the correct answer is **A**.

**Why A is correct:** `/etc/resolv.conf` normally lists resolver configuration, including one or more `nameserver` IP addresses. It may be managed by NetworkManager or systemd-resolved on modern distributions.

**Why the other options are not:** **B** contains static host mappings, not DNS server addresses. **C** defines the local hostname. **D** maps service names to port numbers.

**Objective:** 4.3 - Given a scenario, analyze and troubleshoot network resource issues (DNS resolution).

---

### Question 37 of 40 - Single answer

An interface receives the address `169.254.89.12/16` after boot. What does this most likely indicate?

- [ ] **A.** The host could not obtain an address from DHCP and assigned itself a link-local address.
- [ ] **B.** The default gateway is responding normally.
- [ ] **C.** DNS resolution is configured correctly.
- [X] **D.** The interface has received a valid private address from a DHCP server.

#### Grading and Explanation

**Result:** Incorrect. You selected **D**; the correct answer is **A**.

**Why A is correct:** The `169.254.0.0/16` range is IPv4 link-local addressing. A host commonly assigns such an address when DHCP cannot supply a lease.

**Why the other options are not:** **B** concerns routing and is not proven by the address. **C** concerns name resolution and is unrelated. **D** is false because link-local addressing is not a normal DHCP-assigned private address for network connectivity.

**Objective:** 4.3 - Given a scenario, analyze and troubleshoot network resource issues (DHCP addressing).

---

### Question 38 of 40 - Single answer

Which command shows listening TCP sockets and associated process information, allowing an administrator to verify whether a process is listening on port 443?

- [ ] **A.** `ss -ltnp`
- [ ] **B.** `ip route show`
- [ ] **C.** `ping -c 4 localhost`
- [X] **D.** `netstat -r`

#### Grading and Explanation

**Result:** Incorrect. You selected **D**; the correct answer is **A**.

**Why A is correct:** `ss -ltnp` shows listening (`-l`) TCP (`-t`) sockets using numeric addresses (`-n`) and associated process details (`-p`). Run it with sufficient privilege to see all process names and PIDs.

**Why the other options are not:** **B** shows routing information. **C** tests ICMP reachability. **D** displays the routing table rather than listening sockets.

**Objective:** 4.3 - Given a scenario, analyze and troubleshoot network resource issues (ports and services).

---

### Question 39 of 40 - Single answer

User `dev1` was just added to group `developers`. The directory `/srv/app` is owned by `root:developers` and has permissions `drwxrws---`. `dev1` still cannot create a file in it during the current login session. Assume SELinux and ACLs are not involved. What is the most likely corrective action?

- [ ] **A.** Start a new login session or use `newgrp developers`.
- [ ] **B.** Run `chmod 777 /srv/app`.
- [ ] **C.** Run `chown dev1 /srv/app`.
- [X] **D.** Run `usermod -L dev1`.

#### Grading and Explanation

**Result:** Incorrect. You selected **D**; the correct answer is **A**.

**Why A is correct:** Supplementary group membership is established when a session starts. A new login session, or `newgrp developers`, refreshes `dev1`'s active group list so the directory's group permissions apply.

**Why the other options are not:** **B** grants excessive access to every user. **C** unnecessarily changes ownership of a shared directory. **D** locks the user account and makes the problem worse.

**Objective:** 4.4 - Given a scenario, analyze and troubleshoot user access and file permissions.

---

### Question 40 of 40 - Select 2 answers

After a change to `api.service`, the service fails during the current boot. Which two commands should be used first to inspect the unit's status and its logs from this boot?

- [X] **A.** `systemctl status api.service`
- [X] **B.** `journalctl -u api.service -b`
- [ ] **C.** `systemctl daemon-reload`
- [ ] **D.** `journalctl -k`
- [ ] **E.** `dmesg`

#### Grading and Explanation

**Result:** Correct. You selected **A, B**.

**Why A and B are correct:** `systemctl status api.service` shows the unit's current state, recent failure details, and process status. `journalctl -u api.service -b` filters journal entries for that unit from the current boot.

**Why the other options are not:** **C** reloads changed unit definitions but does not inspect a failure. **D** and **E** focus on kernel messages and do not target the service's journal entries.

**Objective:** 4.5 - Given a scenario, use systemd to diagnose and resolve common problems with a Linux system.

---

## Grading Summary

**Status:** Graded on 2026-09-15

**Scoring method:** Correct = 1 point, Partial = 0.5 point, Incorrect = 0 points. Partial credit was applied only to multiple-response questions where you selected at least one correct answer but did not select the complete correct set.

| Metric | Result |
| --- | --- |
| Correct | 22 |
| Partial | 4 |
| Incorrect | 14 |
| Practice score with partial credit | 24.0 / 40 (60%) |
| Strict all-or-nothing score | 22 / 40 (55%) |

### Performance by Domain

| Domain | Correct | Partial | Incorrect | Practice score |
| --- | --- | --- | --- | --- |
| System Management (Questions 1-13) | 7 | 1 | 5 | 7.5 / 13 (57.7%) |
| Security (Questions 14-21) | 5 | 1 | 2 | 5.5 / 8 (68.8%) |
| Scripting, Containers, and Automation (Questions 22-29) | 5 | 1 | 2 | 5.5 / 8 (68.8%) |
| Troubleshooting (Questions 30-40) | 5 | 1 | 5 | 5.5 / 11 (50.0%) |

### Objective Review Priorities

1. **4.1-4.4 Troubleshooting:** Review inode exhaustion, MD RAID state checks, resolver configuration, DHCP link-local addressing, listening-socket inspection, and new group memberships in active sessions.
2. **1.1-1.7 System Management:** Review the FHS, `cpio` extraction, static hosts versus NSS, one-time scheduling with `at`, DNF versus RPM, and persistent `sysctl` settings.
3. **2.2-2.5 Security:** Review `pam_faillock`, activating permanent firewalld changes, and persistent SELinux labels with `semanage fcontext` plus `restorecon`.
4. **3.1-3.3 Scripting and Containers:** Review `"$@"` argument handling, `podman run` versus `podman exec`, and removing an already tracked file from the Git index.
