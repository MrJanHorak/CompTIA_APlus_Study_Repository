# Lab 01: Home Lab Setup with VirtualBox

> **Skill Area:** Virtualization, OS installation, VM management
> **Time Required:** 30–60 minutes
> **Cost:** Free
> **Tools:** VirtualBox, Ubuntu ISO (or Windows ISO)

---

## Objectives

By the end of this lab you will be able to:

1. Install VirtualBox on a Windows or macOS host
2. Create and configure a new Virtual Machine
3. Install Ubuntu Linux (or Windows) as a guest OS
4. Demonstrate understanding of VM Network modes (NAT vs Bridged)
5. Take a VM snapshot and restore from it

---

## Prerequisites

- A host computer meeting the minimum lab requirements (see [Labs/README.md](README.md))
- Virtualization enabled in BIOS/UEFI (Intel VT-x or AMD-V)
- Internet connection to download tools

---

## Part 1: Verify Virtualization Support

Before installing VirtualBox, confirm that hardware virtualization is enabled.

### Windows

1. Open **Task Manager** (Ctrl+Shift+Esc)
2. Click the **Performance** tab
3. Click **CPU**
4. Look for **Virtualization: Enabled** in the lower right

If it shows **Disabled:**

1. Restart the computer and enter BIOS/UEFI (usually F2, F10, Del, or F12 during POST)
2. Navigate to the CPU or Advanced settings
3. Enable **Intel VT-x** or **AMD-V** (varies by motherboard)
4. Save and exit

---

## Part 2: Download Required Files

Download both files before starting installation:

| File                   | URL                                                                        | Size    |
| ---------------------- | -------------------------------------------------------------------------- | ------- |
| **VirtualBox**         | [virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) | ~100 MB |
| **Ubuntu Desktop ISO** | [ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)         | ~4.7 GB |

> **Alternative:** If you want to practice with Windows, download a free evaluation ISO from [microsoft.com/evalcenter](https://www.microsoft.com/en-us/evalcenter). Choose "Windows 11 Enterprise Evaluation" — valid for 90 days.

---

## Part 3: Install VirtualBox

1. Run the downloaded VirtualBox installer
2. Accept all default options
3. Allow the installer to install device drivers when prompted (these are necessary for VM network and USB support)
4. Launch VirtualBox after installation completes

---

## Part 4: Create a New Virtual Machine

1. In VirtualBox Manager, click **New**
2. Configure as follows:

| Setting   | Value                                       |
| --------- | ------------------------------------------- |
| Name      | `Ubuntu-Lab`                                |
| Folder    | Default (or a folder on your largest drive) |
| ISO Image | Browse to the Ubuntu ISO you downloaded     |
| Type      | Linux                                       |
| Version   | Ubuntu (64-bit)                             |

3. Check **Skip Unattended Installation** (we want to see the full install process)
4. Click **Next**

### Allocate Hardware Resources

| Setting           | Minimum | Recommended  |
| ----------------- | ------- | ------------ |
| Base Memory (RAM) | 1024 MB | 2048–4096 MB |
| Processors (vCPU) | 1       | 2            |

> Only allocate what your host can spare. Leave at least 4 GB of RAM for your host OS.

5. Create a Virtual Hard Disk:
   - **Disk size:** 20 GB minimum; 30–50 GB recommended
   - **Type:** VDI (VirtualBox Disk Image)
   - **Storage:** Dynamically allocated (only uses actual space; grows up to max)

6. Review the summary and click **Finish**

---

## Part 5: Install Ubuntu

1. Select your `Ubuntu-Lab` VM and click **Start**
2. Ubuntu will boot from the ISO
3. Select **Try or Install Ubuntu**
4. Click **Install Ubuntu**
5. Configure:
   - Language: English
   - Keyboard: Your preference
   - Network: Leave default for now
   - Installation type: **Erase disk and install Ubuntu** (this is inside the VM — it will not affect your real computer)
6. Set your username and password
7. Wait for installation to complete (~10–20 minutes)
8. Click **Restart Now** when prompted
9. Press **Enter** when it asks you to remove the installation medium (VirtualBox handles this automatically)

---

## Part 6: Install VirtualBox Guest Additions

Guest Additions improves the VM experience by enabling:

- Auto-resizing of the display
- Shared clipboard between host and guest
- Drag-and-drop file transfer
- Improved mouse integration

1. In the Ubuntu VM, click **Devices** (top menu bar in VirtualBox) → **Insert Guest Additions CD Image**
2. Open a terminal in Ubuntu (right-click desktop → Open Terminal)
3. Run:
   ```bash
   sudo apt update
   sudo apt install build-essential dkms linux-headers-$(uname -r)
   sudo mount /dev/cdrom /media/cdrom
   sudo /media/cdrom/VBoxLinuxAdditions.run
   ```
4. Restart the VM: `sudo reboot`

---

## Part 7: Explore VM Network Modes

Understanding VM network modes is an exam-ready skill. Practice by switching modes and observing behavior.

### Check Current Network Settings

1. Shut down the Ubuntu VM
2. In VirtualBox Manager, select the VM → **Settings** → **Network**
3. **Adapter 1** is enabled; default mode is **NAT**

### Test Each Mode

| Mode                 | Steps                                                                 | Expected Result                                                                                   |
| -------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **NAT**              | Keep default                                                          | Ubuntu gets internet access; not reachable from host network                                      |
| **Bridged**          | Change to Bridged; start VM; run `ip addr`                            | Ubuntu gets an IP from your home DHCP (appears as a separate device on your LAN)                  |
| **Host-Only**        | Change to Host-Only; start VM; run `ip addr`                          | Ubuntu gets an IP from VirtualBox's internal range (192.168.56.x); can communicate with host only |
| **Internal Network** | Change to Internal; add a second VM to the same internal network name | VMs can communicate with each other only                                                          |

**Record your observations in the table below:**

| Mode      | IP Address Received | Can ping 8.8.8.8? | Can ping host machine? |
| --------- | ------------------- | ----------------- | ---------------------- |
| NAT       |                     |                   |                        |
| Bridged   |                     |                   |                        |
| Host-Only |                     |                   |                        |

---

## Part 8: Take and Restore a Snapshot

Snapshots are a critical VM management skill for both the exam and real-world technician work.

### Take a Snapshot

1. With Ubuntu running, click **Machine** → **Take Snapshot**
2. Name it: `Clean Install - Before Changes`
3. Click **OK**

### Make a Change to "Break" the VM

1. Open a terminal in Ubuntu
2. Run: `sudo rm /etc/hosts`
   _(This removes the hosts file — a harmless change to practice restoring from snapshot)_
3. Try running: `ping localhost` — you should see a name resolution failure

### Restore the Snapshot

1. Shut down the VM
2. In VirtualBox Manager, click the **Snapshots** icon (hamburger menu next to the VM name)
3. Right-click the snapshot → **Restore Snapshot**
4. Start the VM
5. Verify: `ping localhost` — should work again

---

## Lab Summary

Confirm you can now answer these questions without referring to the lab steps:

1. What setting in BIOS/UEFI must be enabled for VirtualBox to run 64-bit VMs?
2. What is the difference between NAT and Bridged network mode in a VM context?
3. What is the purpose of Guest Additions in VirtualBox?
4. What is a VM snapshot and when would you use one in a real-world scenario?
5. If you gave a VM 4 GB of RAM and your host only has 8 GB total, what risk does this create?

---

_Next Lab: [Lab 02 — Network Simulation with Cisco Packet Tracer](Lab_02_Network_Simulation.md)_
