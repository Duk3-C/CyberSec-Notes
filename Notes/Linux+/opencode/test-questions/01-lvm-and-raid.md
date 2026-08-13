# Linux+ Practice Quiz — LVM and RAID

**Date:** 2026-08-13
**Questions:** 10 (7 single-answer, 3 select-all)
**Objective domain:** 2.0 Filesystems, Storage, and Networking — 2.2 Given a scenario, configure and manage storage

## Score

| Result | Count |
|--------|-------|
| Correct | 5 |
| Partial | 1 |
| Incorrect | 4 |

---

## Question 1 — Single answer — CORRECT

A system administrator needs to add a new physical disk to an existing LVM volume group called `vg_data` so that additional logical volumes can be created. The new disk is visible as `/dev/sdb`. Which sequence of commands accomplishes this?

- **A.** `pvcreate /dev/sdb && vgcreate vg_data /dev/sdb`
- **B.** `pvcreate /dev/sdb && vgextend vg_data /dev/sdb` ✅ (given: B)
- **C.** `vgextend vg_data /dev/sdb && lvextend /dev/sdb`
- **D.** `pvcreate /dev/sdb && lvextend vg_data /dev/sdb`

**Explanation:** `pvcreate` initializes the disk as a physical volume (PV); `vgextend` adds it to the existing volume group. `vgcreate` would create a brand-new VG, and `lvextend` extends logical volumes, not VGs or disks.

**Objective:** 2.2 — LVM administration (`pvcreate`, `vgextend`)

---

## Question 2 — Single answer — CORRECT

Which command shows the current allocation and configuration of logical volumes, including their path, size, and the volume group they belong to?

- **A.** `lvs` ✅ (given: A)
- **B.** `pvs`
- **C.** `vgs`
- **D.** `lsblk --lvm`

**Explanation:** `lvs` lists logical volumes (name, VG, size, path such as `/dev/vg_data/lv_home`). `pvs` shows physical volumes, `vgs` volume groups; `lsblk --lvm` is a block-device view, not the standard LV listing.

**Objective:** 2.2 — LVM command set (`pvs`/`vgs`/`lvs`)

---

## Question 3 — Select all (3 correct) — PARTIAL (given A, B, C)

A server has a RAID array that recently lost a disk. An administrator needs to identify the degraded state and verify which disk failed. Which of the following are valid ways to check the RAID status? (Select **3**.)

- **A.** `mdadm --detail /dev/md0` ✅
- **B.** `cat /proc/mdstat` ✅
- **C.** `mdadm --examine /dev/md0` ❌ given — `--examine` reads the superblock of a *member disk/partition* (e.g., `/dev/sdb1`), not the array device
- **D.** `lsblk -S /dev/sda` ❌ — shows SCSI transport details, not RAID state
- **E.** `smartctl -H /dev/sda` ✅ — SMART health check to confirm the failed disk

**Expected answer: A, B, E**

**Explanation:** `mdadm --detail` shows full array status including device roles and degraded state; `/proc/mdstat` is the kernel's live view (e.g., `[UU_U]` indicates a failed member); `smartctl -H` verifies physical disk health. `lsblk -S` shows transport, not array state; `--examine` targets member devices, not `/dev/md0`.

**Objective:** 2.2 — Software RAID status with mdadm

---

## Question 4 — Single answer — INCORRECT (given B)

An administrator creates a new logical volume with 20 GB of allocated space, but the application on it later needs more space. The volume group has 15 GB of free extents. Without unmounting the filesystem, which command string extends both the LV **and** its filesystem in one step?

- **A.** `lvextend -L +15G /dev/vg_data/lv_app && xfs_growfs /dev/vg_data/lv_app`
- **B.** `lvextend -l +100%FREE /dev/vg_data/lv_app && resize2fs /dev/vg_data/lv_app` ❌ given
- **C.** `lvextend -L +15G --resizefs /dev/vg_data/lv_app` ✅ expected
- **D.** `lvextend -L +15G /dev/vg_data/lv_app && mount -o remount,resize /dev/vg_data/lv_app`

**Explanation:** `lvextend -L +15G -r/--resizefs` extends the LV and resizes the FS in a single command, automatically choosing `resize2fs` (ext4) or `xfs_growfs` (XFS). B is wrong because `-l +100%FREE` consumes *all* free extents instead of the needed 15 GB, and `resize2fs` cannot resize XFS. A is a valid two-step approach but fails "in one step", and `xfs_growfs` takes a mount point, not a device path. D is not a legitimate resize mechanism.

**Objective:** 2.2 — Extending logical volumes, `--resizefs`

---

## Question 5 — Single answer — INCORRECT (given D)

A server contains three 1 TB disks. The administrator must configure them so that a single disk failure causes **no data loss**, while maximizing usable capacity. No hot spares are available. Which RAID level should be used?

- **A.** RAID 0
- **B.** RAID 1
- **C.** RAID 5 ✅ expected
- **D.** RAID 6 ❌ given

**Explanation:** RAID 5 stripes with distributed parity: 3 × 1 TB → 2 TB usable, survives one disk failure. RAID 6 requires a minimum of 4 disks (double parity); RAID 1 with 3 disks yields only 1 TB usable; RAID 0 has zero fault tolerance.

**Objective:** 2.2 — RAID levels and fault tolerance

---

## Question 6 — Single answer — CORRECT

An administrator runs `lvmdiskscan` on a server and notices a disk is listed as a "whole disk". The administrator then checks the LVM metadata with `pvs` and the disk does **not** appear. Which command initializes the disk so it can be added to a volume group?

- **A.** `vgcreate /dev/sdc`
- **B.** `fdisk /dev/sdc`
- **C.** `pvcreate /dev/sdc` ✅ (given: C)
- **D.** `lvcreate -p /dev/sdc`

**Explanation:** `pvcreate` writes the LVM metadata/PV label so the disk appears in `pvs`. `vgcreate` needs an existing PV; `fdisk` only partitions; `lvcreate -p` creates an LV (the flag sets permissions). A disk absent from `pvs` is missing its PV label.

**Objective:** 2.2 — Physical volumes, `pvcreate`

---

## Question 7 — Select all (2 correct) — INCORRECT (given C, D)

An administrator must remove the disk `/dev/sdb` from RAID array `/dev/md0` so it can be replaced. Which two steps correctly prepare and remove the device? (Select **2**.)

- **A.** `mdadm /dev/md0 --fail /dev/sdb1` ✅
- **B.** `mdadm /dev/md0 --remove /dev/sdb1` ✅
- **C.** `mdadm --stop /dev/md0` ❌ given — stops the entire array, unnecessary
- **D.** `mdadm --zero-superblock /dev/sdb1` before removing it ❌ given — wrong order; zeroing happens **after** removal as cleanup
- **E.** `mdadm --create ...` ❌ — recreates a new array, unrelated

**Expected answer: A, B**

**Explanation:** Correct removal workflow: `--fail` the member, then `--remove` it. `--stop` tears down the whole array, and the superblock is zeroed only after the device has been removed from the array.

**Objective:** 2.2 — mdadm device failure/removal workflow

---

## Question 8 — Single answer — CORRECT

Which statement correctly describes how LVM snapshots work?

- **A.** A snapshot is a full copy of the logical volume's data at the time of creation.
- **B.** A snapshot records changes made to the source volume *after* snapshot creation; the source volume must stay active for the snapshot to remain valid. ✅ (given: B)
- **C.** A snapshot is a temporary block device that a volume can be cloned to, and the source volume cannot be used while the snapshot exists.
- **D.** Snapshots require a hot spare in the volume group before they can be created.

**Explanation:** LVM snapshots use copy-on-write: original blocks are recorded before modification, giving a consistent point-in-time view. The source must remain active or the snapshot is lost. COW stores only changed blocks (not a full copy); the source stays usable; only free extents are needed.

**Objective:** 2.2 — LVM snapshots, copy-on-write

---

## Question 9 — Select all (3 correct) — CORRECT (with caveat — given A, B, C)

A server's root filesystem is running low on space. The administrator plans to move part of the data to a new disk mounted under `/data`. Which three considerations are required for **LVM to be the correct tool** for this task, or are **true about LVM**? (Select **3**.)

- **A.** The new disk must be at least as large as the data being moved. ✅ given (true, but generic capacity planning)
- **B.** A volume group can span multiple physical disks, allowing logical volumes to grow across them. ✅ given
- **C.** Logical volumes can be extended while mounted, without unmounting. ✅ given
- **D.** The administrator must first back up and reformat the filesystem when adding a new physical volume. ❌ false
- **E.** Physical extents are the allocation units of a volume group, typically 4 MiB by default. ✅ also true

**Expected answer: B, C, E** (cleanest trio of LVM-defining properties)

**Caveat:** The question contained 4 factually true statements (A, B, C, E), violating strict "select 3" rules. Given answers are all true; flagged for question quality.

**Objective:** 2.2 — LVM concepts: VG spanning across disks, online extension, physical extents (default 4 MiB)

---

## Question 10 — Single answer — INCORRECT (given B)

An administrator replaces a failed disk in a RAID 1 array of `/dev/sda` and `/dev/sdb`, installs the new `/dev/sdb`, and **recreates the partition table** on it. Which mdadm operation adds the new disk back into `/dev/md0` so the array can rebuild?

- **A.** `mdadm /dev/md0 --add /dev/sdb1` ✅ expected
- **B.** `mdadm --assemble /dev/md0 /dev/sdb1` ❌ given — reassembles a *stopped* array, does not add a disk to a running one
- **C.** `mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1` ❌ destroys existing config and rebuilds from scratch
- **D.** `mdadm --add /dev/md0 /dev/sdb` ❌ wrong device — array is built on the partition `/dev/sdb1`, not the whole disk

**Explanation:** `--add` (or `-a`) registers the replacement member with the running array and triggers the rebuild automatically.

**Objective:** 2.2 — mdadm rebuild/replacement workflow

---

## Key takeaways

1. LVM chain: `pvcreate` → `vgextend` → `lvextend -r/--resizefs` (single-step FS resize).
2. `--resizefs` picks `resize2fs` (ext) or `xfs_growfs` (XFS, mount point arg) automatically; `resize2fs` never works on XFS.
3. mdadm lifecycle: fail → remove → (zero-superblock after removal) → add (triggers rebuild). `--assemble` is for stopped arrays only.
4. RAID 5 = minimum 3 disks, survives 1 failure; RAID 6 = minimum 4 disks, survives 2; RAID 1 mirrors (1 TB usable with 3 disks).
5. Snapshot = copy-on-write point-in-time view; source must stay active.
6. Check arrays with `mdadm --detail` + `/proc/mdstat`; verify physical health with `smartctl -H`.