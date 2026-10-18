# Lab 01: Home Lab Setup with VirtualBox

> **Skills:** Virtualization, OS installation, VM networking and snapshots

> **Time:** Allow 60–120 minutes plus downloads

> **Cost:** Free base VirtualBox package and Ubuntu

> **Reference configuration:** VirtualBox 7.2; Ubuntu Desktop 26.04 LTS amd64 on a supported x86-64 host

> **Validation:** Documentation reviewed October 18, 2026; this workflow has not been run end to end on that configuration.

## Prerequisites and Architecture

Read the [host requirements](README.md#host-requirements-for-lab-01). Use a supported host OS and enough free memory and storage. Administrator privileges are needed to install VirtualBox's host drivers.

- **Intel/AMD host:** Select the host installer and Ubuntu **amd64** ISO. On Windows, Task Manager → Performance → CPU should show virtualization enabled. If disabled, enable Intel VT-x/AMD-V in firmware using the PC manufacturer's instructions.
- **Apple silicon:** Select the macOS Apple-silicon installer and an **Arm64** Ubuntu guest supported by that VirtualBox release. x86-64 guests cannot be virtualized on an Arm host. Unattended installation and Guest Additions features can differ; use [Oracle's compatibility information](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/installation.html) before proceeding. The reference configuration above is the x86-64 path.

The separately licensed VirtualBox Extension Pack is not required.

## Part 1: Download and Install

1. Download VirtualBox from [Oracle](https://www.virtualbox.org/wiki/Downloads), matching your host OS and CPU.
2. Download the **Ubuntu Desktop 26.04 LTS** ISO from [Ubuntu](https://ubuntu.com/download/desktop), matching your guest architecture. Choose the LTS release rather than following a changing “latest” release automatically.
3. Install VirtualBox with its normal virtualization/networking components. A network-driver installation can briefly interrupt host networking.
4. Launch VirtualBox Manager.

Ubuntu's page lists at least 6 GB memory and 25 GB storage for this desktop release. This lab allocates more disk space for updates. Download sizes and menu wording vary by point release.

## Part 2: Create the Guest

Choose **New** in VirtualBox Manager.

| Setting | Value |
| --- | --- |
| Name | Ubuntu-Lab |
| ISO | The matching Ubuntu 26.04 LTS image |
| OS type | Linux / Ubuntu, matching amd64 or Arm64 |
| Installation | Skip unattended installation where that option exists |
| RAM | 6144 MB minimum; 8192 MB if the host has enough spare memory |
| vCPU | 2 |
| Disk | New dynamically allocated VDI, 50 GB |
| Networking | Adapter 1 attached to NAT |

Leave sufficient resources for the host. Dynamic allocation saves initial disk use but the disk and snapshots can grow. Do not attach host physical disks.

Start the VM, choose the installer and follow its language, keyboard and account prompts. Select the newly created **virtual** disk for installation. The installer's erase option is appropriate only after confirming this is the disposable 50 GB VM disk. Restart after installation; detach the ISO from the virtual optical drive if it boots the installer again.

Inside the guest, install updates:

```bash
sudo apt update
sudo apt upgrade
```

Restart the guest if prompted.

## Part 3: Optional Guest Additions

Guest Additions can improve display resizing and pointer integration. Features depend on the host/guest combination; shared clipboard and drag-and-drop require separate settings.

For a supported Ubuntu guest:

1. Install prerequisites:

   ```bash
   sudo apt update
   sudo apt install build-essential dkms linux-headers-$(uname -r)
   ```

2. Use the VM window's **Devices → Insert Guest Additions CD Image**.
3. If the guest did not mount the image automatically, mount it:

   ```bash
   sudo mkdir -p /mnt/vbox-additions
   sudo mount /dev/sr0 /mnt/vbox-additions
   ls /mnt/vbox-additions
   ```

4. Confirm the mounted image contains the installer, then run it:

   ```bash
   sudo sh /mnt/vbox-additions/VBoxLinuxAdditions.run
   ```

5. Reboot and check whether the guest display resizes with the VM window.

If the drive name, mount point or features differ, consult the [VirtualBox user guide](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/). Do not run a guessed installer path or assume x86 feature parity on Arm.

## Part 4: Observe Networking

Start with NAT. In Ubuntu, record addresses and routes:

```bash
ip addr
ip route
```

Open a browser to a known HTTPS site. A failed ping alone does not prove internet access is broken; networks may filter ICMP.

Shut down the VM before changing Adapter 1's attachment mode.

| Mode | Setup | Expected behavior |
| --- | --- | --- |
| NAT | Keep the default adapter setting | Guest normally receives a VirtualBox DHCP address and can initiate external connections; unsolicited inbound access needs configuration |
| Bridged | Select the correct physical interface on a permitted lab LAN | Guest can appear as another LAN device; DHCP/access depend on LAN policy and wireless/driver support |
| Host-only | Create/select a host-only network; enable its DHCP server or configure static addresses | Host and guests on that network can communicate; no external routing by default |
| Internal network | Attach two guests to the same internal network name; configure static addresses on that isolated network | Those guests can communicate; host/external access is absent by default |

Host-only is not limited to one guest talking only to the host. An internal network does not automatically supply DHCP.

For the optional internal-network test, use 192.168.50.10/24 and 192.168.50.11/24 on the two guests, with no gateway. Use the guest network settings and actual interface names, then ping the peer. Restore NAT afterward.

| Mode | Guest IP/mask | Default route | Host/peer reachable? | HTTPS works? |
| --- | --- | --- | --- | --- |
| NAT | | | | |
| Bridged, if permitted | | | | |
| Host-only | | | | |
| Internal, optional | | | | |

Source: [Oracle networking documentation](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/networkingdetails.html).

## Part 5: Prove Snapshot Restore with a Harmless File

1. In the guest terminal, create a marker:

   ```bash
   printf '%s\n' 'before snapshot' > ~/a-plus-snapshot.txt
   cat ~/a-plus-snapshot.txt
   ```

2. Shut down Ubuntu normally. In VirtualBox Manager's **Snapshots** view, take a snapshot named **Before marker change**.
3. Start the VM. Change the marker and confirm the new content:

   ```bash
   printf '%s\n' 'after snapshot' > ~/a-plus-snapshot.txt
   cat ~/a-plus-snapshot.txt
   ```

4. Shut down the VM. Restore **Before marker change** from the Snapshots view. Restoring discards changes since that snapshot; retain another snapshot first if needed.
5. Start Ubuntu. Run:

   ```bash
   cat ~/a-plus-snapshot.txt
   ```

   **Expected:** `before snapshot`.

This demonstrates disk-state rollback without deleting system files. Snapshots depend on the VM's storage chain and are not independent backups.

## Review

1. Why must a guest ISO match the host architecture for this VirtualBox lab?
2. What distinguishes NAT, bridged, host-only and internal networking?
3. Which modes need a separately configured DHCP server or static addresses?
4. What changed when you restored the snapshot?
5. Why must the host retain spare RAM and disk space?

Record your host OS/architecture, VirtualBox version, Ubuntu release and observed results.

_Next: [Lab 02 — Network Simulation](Lab_02_Network_Simulation.md)_
