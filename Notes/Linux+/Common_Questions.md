## Common Questions on the test

- A system cannot boot because the root filesystem is corrupt. Which boot parameter can help recover?
    Normally you get `emergency`, `init=/bin/bash`, and `single` as possible answers. All of these can help recover. Add these to the kernel command line in the bootloader. Emergency mode mounts root read-only.

- Which file can be used to specify kernel modules that should be loaded at boot time?
    Both /etc/modules (on Debian/Ubuntu) and /etc/modules-load.d/*.conf files are used to specify modules to load at boot. 

- What is the purpose of the rpm command in Red Hat-based distributions?
    The rpm command is the low-level package manager for RPM-based distributions. It installs, queries, and manages individual .rpm packages but does not resolve dependencies automatically (use yum or dnf for that).

- Which umask value results in new files having permissions 644 and new directories having 755?
    umask 022 subtracts from 666 for files (666-022=644) and 777 for directories (777-022=755).
    Other umasks:
        umask 002 allows group write.
        umask 077 removes all permissions for group and others (results in 600/700).
        umask 027 removes group write and all others permissions,

- Which command updates all installed packages to their latest versions on a Debian/Ubuntu system?
    **apt upgrade** updates all installed packages to their latest available versions. 

- Which command loads a kernel module along with its dependencies?
    **modprobe** is the recommended command for loading kernel modules as it automatically handles module dependencies.


