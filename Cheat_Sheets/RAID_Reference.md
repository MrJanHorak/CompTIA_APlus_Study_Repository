# Cheat Sheet: RAID Reference

> Quick reference for RAID levels tested on CompTIA A+ Core 1 (220-1201).

---

## RAID Levels Summary

| RAID Level  | Common Name                 | Minimum Disks   | Fault Tolerance    | Usable Capacity | Read      | Write               |
| ----------- | --------------------------- | --------------- | ------------------ | --------------- | --------- | ------------------- |
| **RAID 0**  | Striping                    | 2               | **None** (0 disks) | 100% (n × disk) | Excellent | Excellent           |
| **RAID 1**  | Mirroring                   | 2               | **1 disk**         | 50%             | Good      | Same as single disk |
| **RAID 5**  | Striping with Parity        | 3               | **1 disk**         | (n−1) × disk    | Good      | Moderate            |
| **RAID 6**  | Striping with Double Parity | 4               | **2 disks**        | (n−2) × disk    | Good      | Slow                |
| **RAID 10** | Mirrored Stripe (RAID 1+0)  | 4 (even number) | **1–2 disks**      | 50%             | Excellent | Excellent           |

---

## Detailed Breakdown

### RAID 0 — Striping

```
Disk 1: [Block A1] [Block A3] [Block A5]
Disk 2: [Block A2] [Block A4] [Block A6]
```

- Data is split (striped) across all drives simultaneously
- **Pro:** Maximum read and write performance
- **Con:** Zero fault tolerance — losing **any single drive** loses ALL data
- **Use case:** Scratch disks, video editing cache, situations where performance > data safety

### RAID 1 — Mirroring

```
Disk 1: [Full copy of all data]
Disk 2: [Exact duplicate of Disk 1]
```

- Every write is duplicated to both drives
- **Pro:** Simple; fast read; can survive failure of one drive
- **Con:** 50% of total capacity is unusable; writes go to both drives simultaneously
- **Use case:** OS drives, small servers, applications where uptime is critical

### RAID 5 — Striping with Parity

```
Disk 1: [A1] [A2] [Ap] (Ap = parity for stripe A)
Disk 2: [A3] [Bp] [B1]
Disk 3: [Bp] [B2] [B3]
```

- Data and parity information are striped across all drives
- Parity allows reconstruction of data if one drive fails
- **Pro:** Good balance of performance, space, and fault tolerance
- **Con:** Write performance penalty (parity calculation); only tolerates 1 failure
- **Use case:** Most popular RAID level in small-to-medium servers and NAS devices

### RAID 6 — Striping with Double Parity

- Same as RAID 5 but with two independent parity blocks per stripe
- **Pro:** Survives simultaneous failure of 2 drives; important for large arrays where URE (Unrecoverable Read Error) risk is high
- **Con:** Slower writes than RAID 5; 2 drives' worth of capacity overhead
- **Use case:** Large-capacity arrays (8+ drives) where rebuild time is long enough that a second failure is statistically likely

### RAID 10 (1+0) — Mirrored Sets in a Striped Set

```
Mirror Set 1:  Disk 1 ↔ Disk 2 (mirrored pair)
Mirror Set 2:  Disk 3 ↔ Disk 4 (mirrored pair)
           ↕               ↕
            [Striped across both mirror sets]
```

- First, create RAID 1 mirror pairs; then stripe those pairs together
- **Pro:** Highest performance + redundancy; fast rebuild (only the mirror pair rebuilds)
- **Con:** Requires minimum 4 drives; only 50% capacity utilization
- **Use case:** High-performance databases, virtual machine datastores, enterprise storage

---

## Fault Tolerance: How Many Disks Can Fail?

| RAID Level | Drives That Can Fail Before Data Loss                                          |
| ---------- | ------------------------------------------------------------------------------ |
| RAID 0     | **0** — any failure = total data loss                                          |
| RAID 1     | **1** (unless the surviving disk also fails during rebuild)                    |
| RAID 5     | **1**                                                                          |
| RAID 6     | **2**                                                                          |
| RAID 10    | **1–2** (1 per mirror pair maximum; can lose 2 if they are in different pairs) |

---

## Capacity Calculations

| RAID Level | Formula                       | Example (4 × 2 TB drives) |
| ---------- | ----------------------------- | ------------------------- |
| RAID 0     | n × disk size                 | 4 × 2 TB = **8 TB**       |
| RAID 1     | disk size (only 1 drive used) | 2 TB usable               |
| RAID 5     | (n−1) × disk size             | 3 × 2 TB = **6 TB**       |
| RAID 6     | (n−2) × disk size             | 2 × 2 TB = **4 TB**       |
| RAID 10    | (n/2) × disk size             | 2 × 2 TB = **4 TB**       |

---

## Hardware RAID vs Software RAID

| Feature                   | Hardware RAID                         | Software RAID                                          |
| ------------------------- | ------------------------------------- | ------------------------------------------------------ |
| **Controller**            | Dedicated RAID controller card        | OS manages array (Windows Storage Spaces, Linux mdadm) |
| **Performance**           | Higher — offloads processing from CPU | Slightly lower — uses CPU resources                    |
| **Cost**                  | Higher                                | Low / free                                             |
| **Battery Backup (BBWC)** | Available on enterprise controllers   | Not available                                          |
| **OS independence**       | Array survives OS reinstall           | Array tied to OS configuration                         |

---

## Important Exam Context

> **RAID ≠ Backup.** RAID provides **availability** (protection against hardware failure) but does NOT protect against:
>
> - Accidental file deletion
> - Ransomware encrypting all files (RAID mirrors the encrypted version too)
> - Fire, flood, or theft of the entire system
> - File corruption that propagates to all disks
>
> Always implement RAID **in addition to**, not instead of, a proper backup strategy (see the 3-2-1 rule).

---

_See also: [Core_1/1.3_Hardware.md](../Core_1/1.3_Hardware.md) for full storage and hardware notes._
