# Cheat Sheet: Ports and Protocols

> Quick reference for all ports tested on CompTIA A+ Core 1 (220-1201) and Core 2 (220-1202).

---

## Complete Port Reference Table

| Port        | Protocol        | Service / Application                                          | Transport | Mnemonic                                                                |
| ----------- | --------------- | -------------------------------------------------------------- | --------- | ----------------------------------------------------------------------- |
| **20**      | FTP-DATA        | FTP Data Transfer                                              | TCP       |                                                                         |
| **21**      | FTP             | FTP Control (commands)                                         | TCP       | _Twenty-one guns for File Transfer Protocol_                            |
| **22**      | SSH             | Secure Shell — encrypted remote access                         | TCP       | _22 = SSH — two secure locks_                                           |
| **23**      | Telnet          | Unencrypted remote access (legacy)                             | TCP       | _23 = Telnet — two-three, insecure me!_                                 |
| **25**      | SMTP            | Sending email (Simple Mail Transfer Protocol)                  | TCP       | _25 = SMTP — send mail, 25 cents a stamp_                               |
| **53**      | DNS             | Domain Name System — hostname to IP resolution                 | UDP/TCP   | _53 = DNS — sounds like "d-n-s" in Spanish (el cielo tiene 53 nombres)_ |
| **67**      | DHCP Server     | DHCP — server assigns IP to clients                            | UDP       |                                                                         |
| **68**      | DHCP Client     | DHCP — client receives IP                                      | UDP       | _67/68 = DHCP — server/client pair_                                     |
| **80**      | HTTP            | Unencrypted web traffic                                        | TCP       | _80 = HTTP — boring, unsecured freeway (8-0-hour)_                      |
| **110**     | POP3            | Email download from server (Post Office Protocol v3)           | TCP       | _110 = POP3 — like an old post office, "pop" the mail down_             |
| **137–139** | NetBIOS / NetBT | Legacy Windows file and printer sharing                        | UDP/TCP   |                                                                         |
| **143**     | IMAP            | Email sync with server (Internet Message Access Protocol)      | TCP       | _IMAP keeps mail on the server; 143 = "I-4-three" = I keep for me_      |
| **161**     | SNMP            | Network device monitoring (Simple Network Management Protocol) | UDP       |                                                                         |
| **162**     | SNMP Trap       | SNMP alert/trap notifications                                  | UDP       | _161/162 = SNMP — monitors devices, traps issues_                       |
| **389**     | LDAP            | Directory queries — Active Directory, LDAP servers             | TCP       | _389 = LDAP — look up users in the directory_                           |
| **443**     | HTTPS           | Encrypted web traffic (HTTP Secure)                            | TCP       | _443 = HTTPS — suitcase with three locks (4-4-3) keeping data secure_   |
| **445**     | SMB/CIFS        | Windows file sharing (Server Message Block)                    | TCP       | _445 = SMB — Super Mario Brothers jumping over blocks (file blocks)_    |
| **548**     | AFP             | Apple Filing Protocol — macOS file sharing                     | TCP       | _548 = AFP — Apple Five-Four-Eight filing cabinet_                      |
| **3389**    | RDP             | Remote Desktop Protocol                                        | TCP       | _3389 = RDP — a snowman (3,3,8,9) appears on the remote desktop_        |

---

## Grouped by Function

### Email Protocols

| Port | Protocol          | Direction                | Notes                                            |
| ---- | ----------------- | ------------------------ | ------------------------------------------------ |
| 25   | SMTP              | Sending email            | Server-to-server and client-to-server            |
| 110  | POP3              | Receiving email          | Downloads and deletes from server (typically)    |
| 143  | IMAP              | Receiving email          | Syncs; keeps mail on server; multi-device access |
| 465  | SMTPS             | Sending email (secure)   | SMTP over SSL — older method                     |
| 587  | SMTP (Submission) | Sending email (secure)   | Modern SMTP with STARTTLS — preferred            |
| 993  | IMAPS             | Receiving email (secure) | IMAP over SSL                                    |
| 995  | POP3S             | Receiving email (secure) | POP3 over SSL                                    |

### Remote Access Protocols

| Port | Protocol | Encrypted? | Notes                                               |
| ---- | -------- | ---------- | --------------------------------------------------- |
| 22   | SSH      | Yes        | Secure CLI remote access                            |
| 23   | Telnet   | **No**     | Legacy; avoid in production                         |
| 3389 | RDP      | Yes (TLS)  | Windows GUI remote control                          |
| 5900 | VNC      | Optional   | Cross-platform; encryption depends on configuration |

### File Transfer Protocols

| Port  | Protocol | Encrypted? | Notes                                            |
| ----- | -------- | ---------- | ------------------------------------------------ |
| 20/21 | FTP      | **No**     | Clear-text file transfer                         |
| 22    | SFTP     | Yes        | FTP-like over SSH; completely different protocol |
| 443   | FTPS     | Yes        | FTP over SSL (Explicit or Implicit)              |
| 445   | SMB      | Optional   | Windows file sharing; use SMBv3 for encryption   |
| 548   | AFP      | Optional   | Apple file sharing                               |

### Network Services

| Port    | Protocol | Notes                                   |
| ------- | -------- | --------------------------------------- |
| 53      | DNS      | UDP for queries; TCP for zone transfers |
| 67/68   | DHCP     | UDP; server on 67, client on 68         |
| 161/162 | SNMP     | Monitoring (161); Traps (162)           |
| 389     | LDAP     | Directory lookups                       |
| 636     | LDAPS    | LDAP over SSL                           |

### Web Protocols

| Port | Protocol | Encrypted? |
| ---- | -------- | ---------- |
| 80   | HTTP     | No         |
| 443  | HTTPS    | Yes (TLS)  |

---

## Memory Techniques for Port Numbers

### Visualization Method

Creating a mental image that ties the port number to its function significantly improves recall.

| Port            | Visualization                                                                    |
| --------------- | -------------------------------------------------------------------------------- |
| **22 (SSH)**    | Two padlocks on a door — two locks, secure shell                                 |
| **23 (Telnet)** | An old-fashioned telephone with no lock (unsecured)                              |
| **25 (SMTP)**   | A mailbox with "25 cents postage" written on it                                  |
| **53 (DNS)**    | A phone book (53 = the old area code feeling) — looks up names                   |
| **80 (HTTP)**   | A wide-open highway (80 mph) — no security                                       |
| **443 (HTTPS)** | A suitcase with three combination locks (4-4-3) — locked web traffic             |
| **445 (SMB)**   | Super **M**ario **B**rothers jumping over blocks (445 looks like his silhouette) |
| **3389 (RDP)**  | A snowman (three circles: 3, 3, 8, 9) standing in front of a computer screen     |

### Pattern Recognition

- **20/21** — Two-digit pairs often come together (FTP data + control)
- **67/68** — Another pair (DHCP server/client)
- **137–139** — NetBIOS occupies a range
- **161/162** — SNMP pair (monitor + trap)
- **Ports with "S" (secure) versions tend to add:** `0` (POP3 → 995) or move to 443/636/993

---

## Common TCP vs UDP Patterns

**Generally TCP:** Connection-oriented services that require reliable delivery

- HTTP/HTTPS, FTP, SSH, Telnet, SMTP, POP3, IMAP, RDP, LDAP, SMB

**Generally UDP:** Fast, low-overhead services where speed > reliability

- DNS queries, DHCP, SNMP, VoIP, streaming, TFTP

**Both:** DNS (queries = UDP; zone transfers = TCP), NetBIOS, SNMP

---

_See also: [Core_1/1.2_Networking.md](../Core_1/1.2_Networking.md) for full networking domain notes._
