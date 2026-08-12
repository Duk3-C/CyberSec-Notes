##Boot Processes

There are 2 Firmware options: BIOS or UEFI

BIOS is pretty much unused nowadays (changed by UEFI)
The main differences between BIOS and UEFI are the disk layouts and booting process. BIOS uses MBR as its layout and only stores up to 4 partitions. GPT is the table layout used by UEFI and can store more than 100 logical partitions. 
UEFI includes secure boot, which checks Operating Systems licenses and decides whether to boot into that partition or not.

On Linux+, GRUB2 is the bootloader you need to know, although there are a bunch of options as systemdboot, limine, etc.

Boot parameters (tends to appear a lot in the exam):
    To enter a parameter, you press e in the GRUB menu and enter it in the Linux Line; after that, press Ctrl+X to boot.
    Examples:
        single or 1 - single-user recovery
        emergency - emergency mode, mounts root as read-only
        init=/bin/bash - drops straight to the command Line, skips init entirely
        rd.break - useful if you need to fix fstab mounted disks. Breaks into a shell in the initramfs (before root is mounted).
        systemd.unit=rescue.target / systemd.unit=emergency.target - same as above but explicitly.
        nomodeset, quiet, s (SUSE single-user)

Common exam scenario - "system won't boot":
    1. No output at all/beeps -> hardware/firmware problem (POST fail)
    2. GRUB error (grub rescue> prompt) -> bootloader broken -> reinstall GRUB or boot from live media.
    3. Kernel panic - bad kernel/modules/params. Change menu entry, or edit entry to remove a bad parameter.
    4. Fails mounting root / drops to emergency mode - check /etc/fstab (bad UID=, wrong root=), journalctl -b -p err, run ``fsck`` on the root device.
    5. Boots to black screen - ``nomodeset`` (Graphics Drivers failure)
    6. Login loop / root can't log in - boot single or emergency, remount rw, fix config or reset password.

Relevant commands:
    systemctl list-units --type=target -> Show targets and default
    systemctl get-default / set-default -> Read/change default target
    journalctl -b -> all logs since last boot 
    journalctl -k -> kernel ring buffer (like dmesg)
    dmesg -> Kernel messages since boot
    lsblk, findmnt -> see mounted disks
    grub2-mkconfig / update-grub -> generate grub configuration directories
    systemd-analyze -> boot time analysis.
    systemctl list-jobs, list-units --failed -> diagnose failed boot steps
    mount -o remount,rw / -> remount root writable in rescue mode
    fsck /dev/sda1 -> repair filesystem (umount first)
    chroot /sysroot -> In rescue environments, chroot into the mounted root to fix it.





