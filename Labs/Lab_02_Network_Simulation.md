# Lab 02: Addressing and Fault Isolation with Cisco Packet Tracer

> **Skills:** DHCP, static IPv4, default gateways, routing and DNS

> **Time:** 60–90 minutes

> **Cost:** Free Cisco account/course access may be required

> **Reference interface:** Packet Tracer 8.2.x with a 2911 router and 2960 switch; menu labels can differ in newer versions

> **Validation:** Revised by document and address-plan review October 18, 2026; not executed end to end in Packet Tracer.

## Scope

Build an isolated simulation with two subnets. The second subnet represents a remote service; it is not the real internet. Every expected reply below has a configured destination and return path. No cloud icon, modem, real public DNS service or NAT is needed.

IOS commands are supplied to construct the exercise. Memorizing this router configuration is not an A+ objective.

## Part 1: Install and Add Devices

Get Packet Tracer from [Cisco Networking Academy](https://www.netacad.com/cisco-packet-tracer), following its account/course and download instructions for your supported desktop OS.

Create a blank project with:

- One **2911 router**, named R1.
- One **2960 switch**, named S1.
- Two **PC-PT** clients, named PC1 and PC2.
- One **Server-PT**, named RemoteServer.

Connect using copper straight-through cables:

```text
PC1 FastEthernet0 ── S1 FastEthernet0/1
PC2 FastEthernet0 ── S1 FastEthernet0/2
S1 GigabitEthernet0/1 ── R1 GigabitEthernet0/0
R1 GigabitEthernet0/1 ── RemoteServer FastEthernet0
```

Use these exact device models so interface names match the commands. If your model differs, identify its ports before configuring. Wait for link negotiation; the first ping can lose a packet while ARP resolves.

## Part 2: Address Plan

| Device/interface | IPv4 | Mask | Default gateway |
| --- | --- | --- | --- |
| R1 G0/0, LAN | 192.168.1.1 | 255.255.255.0 | Not needed for these directly connected networks |
| R1 G0/1, remote subnet | 198.51.100.1 | 255.255.255.0 | Not needed |
| PC1 | DHCP, normally 192.168.1.100 or later | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.1.50 | 255.255.255.0 | 192.168.1.1 |
| RemoteServer | 198.51.100.10 | 255.255.255.0 | 198.51.100.1 |

198.51.100.0/24 is a documentation range used here inside the simulator. LAN addresses .1 through .99 are excluded from DHCP so PC2's static address cannot collide with the pool.

## Part 3: Configure R1

Open R1's **CLI**, answer **no** to the initial configuration dialog if shown, and enter:

```text
enable
configure terminal
hostname R1
interface gigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
 exit
interface gigabitEthernet0/1
 ip address 198.51.100.1 255.255.255.0
 no shutdown
 exit
ip dhcp excluded-address 192.168.1.1 192.168.1.99
ip dhcp pool APLUS-LAN
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 198.51.100.10
 exit
end
copy running-config startup-config
```

Accept the default destination filename when saving. R1 routes between its directly connected subnets without static routes.

Inspect the result:

```text
show ip interface brief
show ip route
show ip dhcp binding
```

**Expected:** G0/0 and G0/1 show up/up once their peers are connected. The routing table has connected routes for 192.168.1.0/24 and 198.51.100.0/24. DHCP bindings appear after PC1 requests a lease.

## Part 4: Configure the Server and Clients

### RemoteServer

1. **Desktop → IP Configuration → Static**: set 198.51.100.10, mask 255.255.255.0, gateway 198.51.100.1 and DNS 198.51.100.10.
2. **Services → HTTP**: turn HTTP on.
3. **Services → DNS**: turn DNS on. Add an **A record** named `web.example.test` with address **198.51.100.10**, and save/add it.

### PC1

Choose **Desktop → IP Configuration → DHCP**. Record the assigned address, mask, gateway and DNS using **Desktop → Command Prompt → `ipconfig`**. The exact lease address depends on the simulator's allocation order.

### PC2

Choose **Desktop → IP Configuration → Static** and set 192.168.1.50, mask 255.255.255.0, gateway 192.168.1.1 and DNS 198.51.100.10.

## Part 5: Establish a Working Baseline

Run these commands from PC1's simulated Command Prompt:

| Command | Expected after ARP/link convergence |
| --- | --- |
| `ping 192.168.1.1` | Replies from the local gateway |
| `ping 192.168.1.50` | Replies from PC2 on the same subnet |
| `ping 198.51.100.10` | Replies from the server across R1 |
| `ping web.example.test` | Resolves to the server and receives replies |

In PC1's **Web Browser**, open `http://web.example.test`. **Expected:** the simulated server's HTTP page.

If a baseline test fails, resolve it before introducing a fault. Check port state/cabling, masks, both router interfaces, the server's return gateway, and DNS/HTTP services. Record actual results. Save this working project as **APlus-Lab02-Baseline.pkt** using Packet Tracer's **File → Save As**; this file becomes your recovery point after you have verified it.

## Part 6: Introduce One Fault

1. Record PC1's DHCP-acquired IPv4 configuration.
2. Select **Static** in PC1's IP Configuration. Enter the same IP, mask and DNS as the baseline, but deliberately set its gateway to **192.168.1.99**.
3. Repeat the baseline tests.

| Test | Expected with the wrong gateway |
| --- | --- |
| Ping PC2 | Works: PC2 is local |
| Ping R1's LAN IP | Works: that interface is local |
| Ping RemoteServer by IP | Fails: off-subnet traffic needs a valid gateway |
| Open the server by name | Fails: DNS server is also off-subnet |

A DNS failure here is a consequence of unreachable routing, not a missing DNS record. Ping the known server IP to separate routing from name resolution.

Use the professional troubleshooting framework:

| Step | Record |
| --- | --- |
| 1 — Identify | Baseline, symptoms and affected scope |
| 2 — Theory | Suspected wrong gateway |
| 3 — Test | Compare `ipconfig` with the address plan and compare local/remote pings |
| 4 — Plan and implement | Restore the gateway to 192.168.1.1 |
| 5 — Verify and prevent | Repeat all baseline tests; document the correct address plan |
| 6 — Document | Fault, evidence, change and observed outcome |

Alternatively select DHCP again to restore automatic addressing, then confirm all settings. The methodology itself is supporting professional practice, not a directly tested V15 methodology objective.

## Optional DNS Fault

After restoring the baseline, set only PC1's DNS server to unused **198.51.100.99** while preserving its correct IP, mask and gateway.

- Ping 198.51.100.10: expected to work.
- Resolve a name not previously used, `new.example.test`: first add this A record on RemoteServer, pointing to 198.51.100.10. With incorrect DNS it should fail.
- Restore PC1's DNS to 198.51.100.10 and retry: expected to resolve and work.

Using a new name avoids mistaking a cached answer for successful DNS-server access.

## Review

1. Why can a client with an incorrect gateway still ping another local client?
2. Why does RemoteServer need its own gateway?
3. Why does a connected Cloud-PT icon alone not supply internet service?
4. What distinguishes a routing fault from a DNS fault?
5. Why are static addresses excluded from the DHCP pool?

Record Packet Tracer version and all baseline/fault/recovery results before calling your saved project verified.

_Previous: [Lab 01 — Home Lab Setup](Lab_01_Home_Lab_Setup.md) | [Labs Overview](README.md)_
