# Labs Overview

> Hands-on lab guides to reinforce the practical skills tested in CompTIA A+ Performance-Based Questions (PBQs).

---

## Why Do Labs?

The CompTIA A+ exam includes **Performance-Based Questions (PBQs)** that require you to complete tasks in a simulated environment — not just select an answer from a list. These questions test whether you can:

- Configure a network adapter's TCP/IP settings
- Navigate and modify files using the command line
- Identify cable types and connector specifications
- Set up a basic network in a simulated topology

Beyond the exam, hands-on experience is what separates candidates who get job interviews from those who do not. Hiring managers can tell the difference between someone who memorized answers and someone who has actually done the work.

---

## Available Labs

| Lab                                                        | Skills Covered                                                    | Tools Needed                                 |
| ---------------------------------------------------------- | ----------------------------------------------------------------- | -------------------------------------------- |
| [Lab 01: Home Lab Setup](Lab_01_Home_Lab_Setup.md)         | VirtualBox installation, VM creation, OS installation             | VirtualBox (free), Windows ISO or Ubuntu ISO |
| [Lab 02: Network Simulation](Lab_02_Network_Simulation.md) | Router configuration, IP addressing, VLANs, basic troubleshooting | Cisco Packet Tracer (free)                   |

---

## Free Tools for Your Home Lab

| Tool                          | Download                        | Use                               |
| ----------------------------- | ------------------------------- | --------------------------------- |
| **VirtualBox**                | virtualbox.org                  | Type 2 hypervisor for running VMs |
| **Cisco Packet Tracer**       | netacad.com (free registration) | Network simulation                |
| **Ubuntu ISO**                | ubuntu.com/download             | Free Linux OS for lab VMs         |
| **Windows Server Evaluation** | microsoft.com/evalcenter        | 180-day free Windows Server trial |
| **GNS3**                      | gns3.com                        | Advanced network emulation        |
| **Wireshark**                 | wireshark.org                   | Network packet analysis           |

---

## Minimum System Requirements for a Home Lab

| Resource | Minimum                                                  | Recommended |
| -------- | -------------------------------------------------------- | ----------- |
| CPU      | 4-core with virtualization support (Intel VT-x or AMD-V) | 6+ core     |
| RAM      | 8 GB                                                     | 16 GB       |
| Storage  | 100 GB free                                              | 250 GB SSD  |
| OS       | Windows 10/11 Pro or macOS                               | Same        |

> Enable virtualization in BIOS/UEFI before installing VirtualBox. Look for **Intel VT-x** or **AMD-V** in the CPU settings and ensure it is enabled.

---

## Adding More Labs

This directory is intentionally expandable. See [CONTRIBUTING.md](../CONTRIBUTING.md) for how to submit new lab guides.

Suggested future labs:

- Windows Server AD DS basic setup
- Linux user and permission management
- BitLocker drive encryption walkthrough
- Wi-Fi security configuration on a SOHO router
- Disk partitioning with `diskpart` and `fdisk`
