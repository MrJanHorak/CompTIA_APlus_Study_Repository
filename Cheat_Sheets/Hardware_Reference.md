# Cheat Sheet: Hardware Reference

> Quick reference for RAM, connectors, storage, and hardware specifications tested on CompTIA A+ Core 1.

---

## RAM Reference

### Desktop RAM (DIMM)

| Generation | Pin Count | Voltage                | Notch Position            | Key Feature                                      |
| ---------- | --------- | ---------------------- | ------------------------- | ------------------------------------------------ |
| DDR (DDR1) | 184       | 2.5V                   | —                         | Original double data rate                        |
| DDR2       | 240       | 1.8V                   | Different from DDR3       | Faster clock, lower voltage than DDR             |
| DDR3       | 240       | 1.5V (1.35V low-power) | Different from DDR2       | Lower power than DDR2                            |
| **DDR4**   | **288**   | 1.2V                   | —                         | Used by DDR4 desktop platforms                      |
| **DDR5**   | **288**   | 1.1V                   | Different notch from DDR4 | Faster, higher density, on-DIMM power management |

> Both DDR3 and DDR4 differ in pin count (240 vs 288). DDR4 and DDR5 have the same pin count (288) but different notch positions — they are **not** interchangeable.

### Laptop RAM (SODIMM)

| Generation        | Pin Count | Notes                         |
| ----------------- | --------- | ----------------------------- |
| DDR / DDR2 SODIMM | 200       | Legacy laptops                |
| DDR3 SODIMM       | 204       | Many mid-generation laptops   |
| **DDR4 SODIMM**   | **260**   | Used by DDR4 laptop platforms       |
| DDR5 SODIMM       | 262       | Used by DDR5 laptop platforms |

### RAM Types by Characteristic

| Type                         | Description                                                    | Use Case                             |
| ---------------------------- | -------------------------------------------------------------- | ------------------------------------ |
| **SDRAM**                    | Synchronized with system bus (legacy)                          | Very old systems                     |
| **SO-DIMM**                  | Small Outline DIMM — laptop/SFF form factor                    | Laptops, small form factor PCs       |
| **ECC**                      | Error-Correcting Code — detects and corrects single-bit errors | Servers, workstations                |
| **Registered (RDIMM)**       | Includes register to buffer signals; reduces electrical load   | High-capacity server RAM             |
| **Unbuffered (UDIMM)**       | Standard desktop/laptop RAM                                    | Most consumer systems                |
| **XMP (Intel) / EXPO (AMD)** | Overclocking profiles burned into the SPD chip                 | Enthusiast builds to run rated speed |

---

## Storage Form Factors

### 2.5" and 3.5" Drives

| Size     | Interface  | Type       | Common Use               |
| -------- | ---------- | ---------- | ------------------------ |
| 3.5 inch | SATA / SAS | HDD        | Desktop storage towers   |
| 2.5 inch | SATA       | HDD or SSD | Laptops; desktop upgrade |
| 2.5 inch | SAS        | HDD        | Enterprise servers       |

### M.2 Form Factors

| Size Code | Dimensions     | Common In                              |
| --------- | -------------- | -------------------------------------- |
| 2242      | 22 × 42 mm     | Slim laptops                           |
| 2260      | 22 × 60 mm     | Less common                            |
| **2280**  | **22 × 80 mm** | **Most common — desktops and laptops** |
| 22110     | 22 × 110 mm    | Enterprise / workstation boards        |

> The first two digits = width in mm; remaining digits = length in mm.

### M.2 Key Types

| Key         | Protocol Supported      | Notes                                         |
| ----------- | ----------------------- | --------------------------------------------- |
| **M key**   | NVMe (PCIe) and/or SATA | Can support both; check motherboard spec      |
| **B key** | SATA or PCIe up to x2 | Depends on the drive and host implementation |
| **B+M key** | SATA or PCIe up to x2, depending on the drive | Fits compatible B/M sockets; protocol support must match |

---

> Keying establishes mechanical fit, not universal compatibility. Match the SSD's SATA/PCIe protocol, lane count and physical length to the motherboard manual. Source: [Kingston M.2 FAQ](https://www.kingston.com/en/ssd/ssd-faq).

---

## Interfaces and Connectors

### Storage Interfaces

| Interface              | Max Speed            | Notes                                  |
| ---------------------- | -------------------- | -------------------------------------- |
| **SATA I**             | 1.5 Gbps (~150 MB/s) | Legacy                                 |
| **SATA II**            | 3 Gbps (~300 MB/s)   | Legacy                                 |
| **SATA III**           | 6 Gbps (~600 MB/s)   | Current standard; backward compatible  |
| **NVMe (PCIe 3.0 x4)** | ~3,500 MB/s          | Typical consumer NVMe SSD speed        |
| **NVMe (PCIe 4.0 x4)** | ~7,000 MB/s          | High-performance Gen 4 NVMe            |
| **SAS**                | 12 Gbps (SAS-3)      | Enterprise; higher endurance than SATA |

### Display / Video Connectors

| Connector                    | Signal                  | Audio | Common Use                                                         |
| ---------------------------- | ----------------------- | ----- | ------------------------------------------------------------------ |
| **VGA (DB-15)**              | Analog                  | No    | Legacy monitors and projectors                                     |
| **DVI-A**                    | Analog only             | No    | Legacy                                                             |
| **DVI-D (Single/Dual Link)** | Digital only            | No    | LCD monitors; single = up to 1920×1200, dual = 2560×1600           |
| **DVI-I**                    | Analog + Digital        | No    | Flexible; can use DVI-to-VGA adapter                               |
| **HDMI**                     | Digital                 | Yes   | TVs, monitors, projectors — most common consumer standard          |
| **DisplayPort**              | Digital                 | Yes   | PC monitors; daisy-chaining; higher bandwidth than HDMI for gaming |
| **Mini-DisplayPort**         | Digital                 | Yes   | MacBooks, Surface devices; same signal as DP                       |
| **USB-C / Thunderbolt**      | Digital (with Alt Mode) | Yes   | Modern thin laptops                                                |

### USB Standards

| Standard                        | Max Speed | Connector              | Notes                                          |
| ------------------------------- | --------- | ---------------------- | ---------------------------------------------- |
| USB 1.1                         | 12 Mbps   | Type-A/B               | Legacy (Full Speed)                            |
| USB 2.0                         | 480 Mbps  | Type-A/B/Mini/Micro    | Hi-Speed; still common for keyboards/mice      |
| USB 3.0 / 3.1 Gen 1 / 3.2 Gen 1 | 5 Gbps    | Type-A (blue) / Type-C | SuperSpeed                                     |
| USB 3.1 Gen 2 / 3.2 Gen 2       | 10 Gbps   | Type-A / Type-C        | SuperSpeed+                                    |
| USB 3.2 Gen 2×2                 | 20 Gbps   | Type-C only            | —                                              |
| USB4 (20/40 Gbps implementations) | Up to 40 Gbps | Type-C | Capabilities depend on implementation; Thunderbolt 3 hardware is not required |
| USB4 Version 2.0 | Up to 80 Gbps | Type-C | Check host, device and cable capabilities |
| Thunderbolt 3                   | 40 Gbps   | USB-C                  | Daisy-chain up to 6 devices; video output      |
| Thunderbolt 4                   | 40 Gbps   | USB-C                  | Enhanced Thunderbolt 3 with mandatory features |

> **Color coding:** Some USB 3.x ports use blue inserts, but manufacturers vary. Check the port label and device specifications rather than inferring speed from color alone.

> Source: [USB-IF USB4 overview](https://www.usb.org/usb4). USB-C describes connector shape; verify supported speed, video mode and power delivery on both devices and the cable.

---

### Audio Connectors (3.5mm TRS Color Code)

| Color              | Function                                  |
| ------------------ | ----------------------------------------- |
| **Green**          | Analog audio output (headphones/speakers) |
| **Pink**           | Microphone input                          |
| **Blue**           | Line in (from external audio source)      |
| **Orange / Black** | Surround sound rear / side channels       |

---

## Power Supply Connectors

| Connector      | Pin Count            | Powers                                                  |
| -------------- | -------------------- | ------------------------------------------------------- |
| **Main ATX**   | 24-pin               | Motherboard (20+4 pin; backward compatible with 20-pin) |
| **CPU / EPS**  | 8-pin (4+4)          | CPU VRM                                                 |
| **PCIe power** | 6-pin or 8-pin (6+2) | GPU                                                     |
| **SATA power** | 15-pin               | SATA drives, case fans                                  |
| **Molex**      | 4-pin                | Legacy drives, some fans, pump controllers              |
| **Floppy**     | 4-pin (small)        | Legacy floppy drives (rarely seen in field)             |

---

## Motherboard Expansion Slots

| Slot         | Version        | Bandwidth  | Primary Use                      |
| ------------ | -------------- | ---------- | -------------------------------- |
| **PCIe x1**  | 3.0            | ~1 GB/s    | NICs, sound cards, USB expansion |
| **PCIe x4**  | 3.0            | ~4 GB/s    | M.2 adapters, RAID controllers   |
| **PCIe x8**  | 3.0            | ~8 GB/s    | Some GPUs, high-bandwidth cards  |
| **PCIe x16** | 3.0            | ~16 GB/s   | Primary GPU slot                 |
| **PCIe x16** | 4.0            | ~32 GB/s   | Current high-end GPUs            |
| **M.2**      | PCIe 3.0 / 4.0 | 3.5–7 GB/s | NVMe SSD                         |

> Smaller cards (x1, x4) can physically fit into larger slots (x16) and will work at the smaller card's speed.

---

## Front Panel Header Pin Layout (Common Reference)

| Function         | Pins | Notes                      |
| ---------------- | ---- | -------------------------- |
| Power Switch     | 2    | Momentary contact          |
| Reset Switch     | 2    | Momentary contact          |
| Power LED        | 2    | + and − (polarity matters) |
| HDD Activity LED | 2    | Polarity matters           |
| Speaker (beep)   | 4    | Used for POST beep codes   |

> Refer to the motherboard manual for the exact header layout — it varies by manufacturer.

---

## Wireless Card Standards Quick Reference

| Standard            | Band            | Max Speed | Key Feature            |
| ------------------- | --------------- | --------- | ---------------------- |
| 802.11a             | 5 GHz           | 54 Mbps   | First 5 GHz standard   |
| 802.11b             | 2.4 GHz         | 11 Mbps   | First popular standard |
| 802.11g             | 2.4 GHz         | 54 Mbps   |                        |
| 802.11n (Wi-Fi 4)   | 2.4/5 GHz       | 600 Mbps  | Introduced MIMO        |
| 802.11ac (Wi-Fi 5)  | 5 GHz           | 6.9 Gbps  | MU-MIMO, beamforming   |
| 802.11ax (Wi-Fi 6)  | 2.4/5 GHz       | 9.6 Gbps  | OFDMA                  |
| 802.11ax (Wi-Fi 6E) | 2.4/5/**6 GHz** | 9.6 Gbps  | Added 6 GHz band       |
| 802.11be (Wi-Fi 7)  | 2.4/5/6 GHz     | 46 Gbps   | Wi-Fi 7      |

---

> Wireless figures are theoretical PHY maxima, not file-transfer speeds. Wi-Fi 5's ~6.9 Gbps maximum assumes eight spatial streams and 160 MHz channels; Wi-Fi 4's 600 Mbps assumes four streams and 40 MHz, and Wi-Fi 6's ~9.6 Gbps assumes eight streams and 160 MHz. Client capabilities, interference and protocol overhead lower throughput. [Cisco reference](https://www.cisco.com/c/dam/global/en_ca/assets/ciscoconnect/2013/assets/docs/wireless-feature-updates-ian-procyk-cisco-connect-2013-toronto.pdf).

---

_See also: [Core_1/1.3_Hardware.md](../Core_1/1.3_Hardware.md) for full hardware domain notes._
