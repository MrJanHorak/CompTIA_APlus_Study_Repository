# Lab 02: Network Simulation with Cisco Packet Tracer

> **Skill Area:** Networking, IP addressing, SOHO configuration, basic troubleshooting
> **Time Required:** 45–90 minutes
> **Cost:** Free
> **Tools:** Cisco Packet Tracer

---

## Objectives

By the end of this lab you will be able to:

1. Install Cisco Packet Tracer
2. Build a basic SOHO network topology
3. Configure IP addressing (static and DHCP)
4. Verify connectivity using `ping` and `ipconfig`
5. Identify and fix a deliberately introduced network fault

---

## Prerequisites

- A computer with a web browser
- Free Cisco Networking Academy account (required to download Packet Tracer)

---

## Part 1: Download and Install Cisco Packet Tracer

Packet Tracer requires a free Cisco NetAcad account.

1. Go to [netacad.com](https://www.netacad.com)
2. Click **Sign Up** and create a free account
3. After logging in, search for **Packet Tracer** in the course catalog
4. Enroll in the free **"Getting Started with Cisco Packet Tracer"** course
5. Find the download link in the course resources (Windows, macOS, and Linux versions available)
6. Install Packet Tracer
7. Launch Packet Tracer and log in with your NetAcad credentials

---

## Part 2: Build a Basic SOHO Network

You will build a network that mirrors a typical small office or home office environment.

### Target Topology

```
[Internet Cloud]
       |
   [Cable Modem]
       |
   [SOHO Router]
     /    \
[Switch]  [Wireless Laptop]
  |   |
[PC1] [PC2]
```

### Step-by-Step Build

1. Open Packet Tracer and start a **new blank project**

2. **Add devices** (drag from the device panel at the bottom):
   - 1× Cloud-PT (represents the internet)
   - 1× Home Router (found under Router or Home devices)
   - 1× Switch (2960 or equivalent)
   - 2× PC
   - 1× Laptop

3. **Connect devices** using the appropriate cables:
   - Cloud to Router WAN port: **Ethernet straight-through**
   - Router LAN port to Switch: **Ethernet straight-through**
   - Switch to each PC: **Ethernet straight-through**
   - Router to Laptop: **Wireless** (if using wireless interface) or straight-through

> **Cable selection tip:** When unsure, select **Automatically Choose Connection Type** (the lightning bolt icon) and Packet Tracer will pick the correct cable.

---

## Part 3: Configure the Router

1. Click on the router → select the **GUI** tab (or CLI tab for command-line)
2. Navigate to **Setup** (Basic Setup)
3. Configure the following:

| Setting        | Value                                 |
| -------------- | ------------------------------------- |
| Internet IP    | Assigned by the "ISP" (leave as DHCP) |
| Local IP (LAN) | `192.168.1.1`                         |
| Subnet Mask    | `255.255.255.0`                       |
| DHCP Server    | **Enabled**                           |
| DHCP Start IP  | `192.168.1.100`                       |
| Max Users      | `50`                                  |

4. Click **Save Settings**

---

## Part 4: Configure the PCs

### PC1 — DHCP (automatic)

1. Click on PC1 → **Desktop** tab → **IP Configuration**
2. Select **DHCP**
3. Wait a moment — the PC should receive an IP address from the router
4. Record the IP address assigned: ******\_\_\_******

### PC2 — Static IP

1. Click on PC2 → **Desktop** tab → **IP Configuration**
2. Select **Static**
3. Enter:

| Setting         | Value           |
| --------------- | --------------- |
| IP Address      | `192.168.1.50`  |
| Subnet Mask     | `255.255.255.0` |
| Default Gateway | `192.168.1.1`   |
| DNS Server      | `8.8.8.8`       |

---

## Part 5: Verify Connectivity

Open the **Command Prompt** on each device (Desktop → Command Prompt) and run the following commands. Record your results.

### From PC1

| Test            | Command                          | Expected Result | Your Result |
| --------------- | -------------------------------- | --------------- | ----------- |
| Loopback        | `ping 127.0.0.1`                 | 4 replies       |             |
| Local IP        | `ping 192.168.1.x` (your own IP) | 4 replies       |             |
| Default gateway | `ping 192.168.1.1`               | 4 replies       |             |
| PC2             | `ping 192.168.1.50`              | 4 replies       |             |
| Internet        | `ping 8.8.8.8`                   | 4 replies       |             |

### View IP Configuration

On PC1, run `ipconfig` and record:

| Field           | Value |
| --------------- | ----- |
| IPv4 Address    |       |
| Subnet Mask     |       |
| Default Gateway |       |

---

## Part 6: Troubleshooting Exercise — Find and Fix the Fault

Your instructor (or you, following the instructions below) introduces a fault into the network. Your task is to diagnose it using the CompTIA 6-step troubleshooting methodology.

### Introduce the Fault

1. Click on PC1 → Desktop → IP Configuration
2. Change the Default Gateway to `192.168.1.99` (incorrect)
3. Click OK

### Symptoms

- PC1 can ping PC2 (`192.168.1.50`) — **succeeds?** \_\_\_
- PC1 can ping the router (`192.168.1.1`) — **succeeds?** \_\_\_
- PC1 can ping the internet (`8.8.8.8`) — **succeeds?** \_\_\_

### Apply the Troubleshooting Methodology

Fill in this worksheet as you diagnose:

| Step                     | Your Analysis                                |
| ------------------------ | -------------------------------------------- |
| 1 — Identify the Problem | What symptoms are you observing?             |
| 2 — Theory               | What do you think is causing this?           |
| 3 — Test the Theory      | What did you check to confirm?               |
| 4 — Plan of Action       | What change will you make?                   |
| 5 — Implement and Verify | What did you change? Does it work now?       |
| 6 — Document             | Summarize the fault and fix in one sentence. |

### Expected Diagnosis

> **Fault:** The default gateway on PC1 was set incorrectly to `192.168.1.99` instead of `192.168.1.1`. PC1 can reach devices on the local subnet (same /24 network) but cannot route traffic beyond the subnet because it sends inter-network traffic to a non-existent gateway.
>
> **Fix:** Set the default gateway on PC1 to `192.168.1.1`.

---

## Bonus Challenge

### Challenge 1: Add a Server

- Add a generic Server device to the topology
- Assign it a static IP of `192.168.1.10`
- Configure the PCs to use the Server's IP as their DNS server
- Observe how DNS is used by network clients

### Challenge 2: Subnet Design

You have been given the network address `192.168.10.0/24`.

Design two subnets — one for the office LAN and one for a guest Wi-Fi VLAN:

- Office LAN: `192.168.10.0/25` (hosts 192.168.10.1–192.168.10.126)
- Guest Wi-Fi: `192.168.10.128/25` (hosts 192.168.10.129–192.168.10.254)

Modify your Packet Tracer topology to implement this addressing scheme.

---

## Lab Summary

Confirm you can answer these questions without referring to the lab steps:

1. What is the difference between a DHCP-assigned IP address and a static IP address?
2. A PC on your network has the IP address `169.254.45.23`. What does this tell you?
3. If a device can ping its default gateway but cannot reach the internet, where is the problem?
4. What is the purpose of specifying a default gateway on an end device?
5. In a `/24` subnet, how many usable IP addresses are available for hosts?

---

_Previous: [Lab 01 — Home Lab Setup](Lab_01_Home_Lab_Setup.md) | Back to: [Labs Overview](README.md)_
