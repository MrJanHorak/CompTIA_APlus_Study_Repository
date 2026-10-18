# Labs Overview

> Practical exercises for CompTIA A+ 220-1201/220-1202.

## Available Practice

| Exercise | Skills | Tools |
| --- | --- | --- |
| [Lab 01: Home Lab Setup](Lab_01_Home_Lab_Setup.md) | Guest installation, networking and snapshots | VirtualBox and Ubuntu Desktop |
| [Lab 02: Network Simulation](Lab_02_Network_Simulation.md) | DHCP, static addressing, routing, DNS and fault isolation | Cisco Packet Tracer |
| [ExamWizardz public practice](https://www.examwizardz.app/pbq-practice) | Short simulations and PBQ-style tasks | Browser; selected exercises need no account |

Practice should include explaining the fault, making a controlled change and verifying the outcome. Browser simulations complement direct experience with an OS and physical components.

## Tools and Access

| Tool | Official source | Access notes |
| --- | --- | --- |
| VirtualBox | [Downloads](https://www.virtualbox.org/wiki/Downloads) | Base package is free; the separately licensed Extension Pack is not needed here |
| Packet Tracer | [Cisco Networking Academy](https://www.netacad.com/cisco-packet-tracer) | Desktop simulator; free Cisco account/course access may be required |
| Ubuntu | [Desktop downloads](https://ubuntu.com/download/desktop) | Free; match the ISO architecture to the host |
| Windows evaluation | [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter) | Optional time-limited evaluation; check architecture and terms |
| Wireshark | [Downloads](https://www.wireshark.org/download.html) | Optional packet-analysis practice |

## Host Requirements for Lab 01

These are planning recommendations for one Ubuntu Desktop 26.04 LTS guest, not universal VirtualBox minimums.

| Resource | Planning recommendation |
| --- | --- |
| CPU | Compatible 64-bit CPU; enough capacity for 2 guest vCPUs and the host |
| RAM | 16 GB host RAM; allocate at least 6 GB to this Ubuntu guest and keep sufficient memory for the host |
| Storage | At least 80 GB free for installation media, a growing virtual disk and snapshots |
| Host OS | A supported Windows 11, macOS or Linux release; Windows Pro is not required for VirtualBox |
| Architecture | x86-64 host → amd64 guest; Apple silicon → a supported Arm64 guest and matching VirtualBox package |

On x86 hosts, enable Intel VT-x/AMD-V in firmware. Apple silicon does not have this PC BIOS setting. Check [Oracle's host/guest requirements](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/installation.html). Ordinary Windows 10 support ended October 14, 2025; check ESU/LTSC conditions if maintaining a legacy host.

## Verification Status

Revised October 18, 2026 against vendor documentation. The two local walkthroughs have been reviewed for consistency but have not been executed end to end on the listed application/guest versions. Record your application version, host architecture, results and any changed menu labels when reporting a correction. Do not treat expected results as a test record.

The ExamWizardz public IP-troubleshooting sample was completed through grading without an account; the full library was not evaluated. See [resource review notes](../Resources/Recommended_Resources.md).

## Contributing a Lab

Include objective references, exact tool/guest versions, prerequisites, addressing, expected results and recovery steps. Use harmless files and disposable virtual disks. Follow [CONTRIBUTING.md](../CONTRIBUTING.md).
