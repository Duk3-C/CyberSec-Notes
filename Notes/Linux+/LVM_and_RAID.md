## LVM Notes

## What is LVM and why use it?

LVM (Logical Volume Manager) is a storage abstraction layer. Instead of mounting a raw partition directly, you create flexible "virtual" volumes that can be resized on the fly, spanned across multiple disks, snapshotted, and migrated without unmounting or reinstalling.

LVM solves the classic problem: with plain partitions, growing a filesystem means repartitioning (risky, often requires downtime and moving data). With LVM, you just add more space to the pool and extend the logical volume.

## LVM architecture (the hierarchy, memorize this)

```
Physical Volume (PV)  →  Volume Group (VG)  →  Logical Volume (LV)  →  Filesystem
   /dev/sdb1              pool of space          /dev/vg1/lv1            /mount/point
```

Layer by layer:
- **Physical Volume (PV)**: a disk or partition marked as usable by LVM. Any raw disk or partition can become a PV, but a PV *must* have a partition type of `8e` (Linux LVM) to be seen correctly.
- **Volume Group (VG)**: a pool that combines one or more PVs. This is the "big bucket" of space. Can span multiple physical disks.
- **Logical Volume (LV)**: a virtual partition carved out of the VG. This is what you format and mount. Appears as `/dev/<vgname>/<lvname>` (or `/dev/mapper/<vgname>-<lvname>`).
- **Filesystem**: the LV gets a filesystem (ext4, XFS, swap, etc.) like any normal device.

The whole point: LVs are independent of the physical disk underneath, so they can be resized, moved, snapshotted, and combined across disks.

## Essential LVM commands

| Component | Create | Display/Inspect | Remove |
|---|---|---|---|
| PV | `pvcreate /dev/sdb1` | `pvs`, `pvdisplay`, `pvscan` | `pvremove /dev/sdb1` |
| VG | `vgcreate vg1 /dev/sdb1 /dev/sdc1` | `vgs`, `vgdisplay`, `vgscan` | `vgremove vg1` |
| LV | `lvcreate -L 10G -n lv1 vg1` | `lvs`, `lvdisplay`, `lvscan` | `lvremove /dev/vg1/lv1` |

Useful options for `lvcreate`:
- `-L 10G` → fixed size; `-l 100%FREE` → use percentage of remaining space (`-l` = extents, `-L` = size)
- `-n lv1` → name the LV
- `-s` → make a snapshot instead of a normal LV
- `-r` → resize the filesystem along with the LV (resize2fs/xfs_growfs automatically)
- `--type raid1` / `--type striped` → RAID/mirroring at the LVM level
- `-p r` → make the LV read-only

Other important commands:
- `vgchange -ay` → activate all VGs (needed after reboot in rescue situations)
- `vgextend vg1 /dev/sdd1` / `vgreduce vg1 /dev/sdd1` → add/remove PVs from a VG
- `pvmove /dev/sdb1` → migrate data off a PV (e.g. to remove a failing disk)
- `lvrename vg1 old new` → rename an LV
- `/etc/lvm/backup/` → LVM keeps configuration backups there; used for recovery
- `swap on LVM` → create an LV with `mkswap` and add it to `/etc/fstab` just like a partition

## Extending a logical volume (very common exam scenario)

**ext4 example (online resize, no downtime):**
1. `lvextend -L +5G /dev/vg1/lv1` (or `-l +100%FREE` to use all remaining VG space)
2. `resize2fs /dev/vg1/lv1` → grow the filesystem to fill the LV

Alternative one-shot: `lvresize -r -L +5G /dev/vg1/lv1` (`-r` resizes the filesystem too).

**XFS example:**
1. `lvextend -L +5G /dev/vg1/lv1`
2. `xfs_growfs /mount/point` (note: XFS grow commands take the **mount point**, not the device, and XFS can only grow, never shrink)

## Shrinking a logical volume (only ext4!)

XFS **cannot** be shrunk — this is a favorite exam trick. For ext4:
1. `umount /mount/point`
2. `e2fsck -f /dev/vg1/lv1` → check the filesystem first
3. `resize2fs /dev/vg1/lv1 8G` → shrink the filesystem *first* (smaller than the LV)
4. `lvreduce -L 8G /dev/vg1/lv1` → then shrink the LV

Rule of thumb: **grow filesystem after growing the LV; shrink filesystem before shrinking the LV.** And always shrink the filesystem before the volume.

## Snapshots

A snapshot is a point-in-time copy of an LV, useful for backups or before risky changes. It's cheap because it only stores changes (copy-on-write).

- `lvcreate -s -L 1G -n snap /dev/vg1/lv1` → create a snapshot named `snap`
- Mount it read-only to make a consistent backup: `mount -o ro /dev/vg1/snap /mnt/backup`
- Remove it when done: `lvremove /dev/vg1/snap`

If the snapshot fills up (its size is the max amount of *changes* it can hold), it becomes invalid.

## RAID at the LVM level

LVM can do RAID itself:
- `lvcreate --type raid1 -m 1 -L 10G -n mirr vg1` → mirrored LV
- `lvcreate --type striped -i 2 -L 10G -n str vg1` → striped LV across 2 PVs

This gives you LVM flexibility plus redundancy without a hardware RAID card or mdadm.

---

## RAID Notes

## What is RAID?

RAID (Redundant Array of Independent Disks) combines multiple physical disks into one logical storage unit to improve **performance** (parallel I/O) and/or **reliability** (redundancy against disk failure).

Two implementation types:
- **Hardware RAID**: dedicated RAID controller card. CPU-free, appears as a single disk to the OS, needs the controller's own management (often BIOS-level, `megacli`, `storcli`).
- **Software RAID**: implemented by the OS kernel with `mdadm`. Disks show up as `/dev/md0`, `/dev/md1`... and the config lives in `/etc/mdadm.conf`.

Exam tip: software RAID devices are always named `/dev/mdN`.

## RAID levels (memorize this table)

| Level | Min disks | How it works | Survives | Capacity | Use case |
|---|---|---|---|---|---|
| **RAID 0** | 2 | Striping (data split across all disks) | 0 failures | 100% (N disks) | Max speed, no redundancy — one disk dies, ALL data is lost |
| **RAID 1** | 2 | Mirroring (each disk holds a full copy) | 1 failure | 50% | Safety; reads are faster (can read both copies in parallel), writes are same speed |
| **RAID 5** | 3 | Striping + distributed parity (parity spread across all disks) | 1 failure | N−1 | Best balance of speed/space/safety |
| **RAID 6** | 4 | Striping + double parity | 2 failures | N−2 | Extra safety for large arrays; slower writes |
| **RAID 10 (1+0)** | 4 | Mirrored pairs, then the pairs are striped | 1 per mirror pair (up to 2 total) | 50% | Performance AND redundancy; the go-to for databases |

Key distinctions:
- RAID 0 = performance only. RAID 1/5/6 = redundancy. RAID 10 = both.
- Parity (RAID 5/6) lets the array rebuild the missing disk's data from the remaining disks — this is *not* a backup, it's fault tolerance.
- RAID 5 rebuild after one disk fails; if a second fails during rebuild, all data is lost (hence RAID 6 for big disks).
- RAID 10 is NOT the same as RAID 01: with RAID 01 (stripes then mirrors) you can lose one full stripe half.

## mdadm (software RAID) commands

| Action | Command |
|---|---|
| Create | `mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd` |
| Inspect | `mdadm --detail /dev/md0` or `mdadm --detail --scan` |
| Add a hot spare | `mdadm --add /dev/md0 /dev/sde` |
| Fail a disk | `mdadm --fail /dev/md0 /dev/sdb` |
| Remove a disk | `mdadm --remove /dev/md0 /dev/sdb` |
| Stop the array | `mdadm --stop /dev/md0` |
| Status | `cat /proc/mdstat` (quick status of all arrays) |

- A **hot spare** is a disk standing by in the array that automatically replaces a failed disk.
- `mdadm --detail --scan >> /etc/mdadm.conf` → persist the config so the array assembles on boot.
- Combine with LVM: make `/dev/md0` a PV, add it to a VG — LVM on top of RAID is a very common production setup.

## Common exam scenarios

- "No redundancy, just performance" → RAID 0
- "2 disks, one can fail" → RAID 1
- "3 disks, survive one failure, no wasted mirror" → RAID 5
- "Which survives 2 failures" → RAID 6 (also mirrored setups can in specific cases, but the classic answer is RAID 6)
- "Web server needs speed + redundancy with 4 disks" → RAID 10
- "XFS can't be shrunk" → shrinking an LVM volume with XFS fails; only ext4 can be shrunk
- After adding a disk to a VG: `pvs` / `vgscan` / `vgextend`, then `lvextend -l +100%FREE` + `resize2fs`/`xfs_growfs`
- Rescue boot with LVM root: run `vgchange -ay` (or `lvm vgchange -ay`) before mounting root, then `mount /dev/vg1/root /sysroot` and `chroot /sysroot`
