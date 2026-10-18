# Cheat Sheet: Command-Line Reference

> Quick reference for Windows, Linux, and macOS CLI commands tested on CompTIA A+ Core 2 (220-1202).

---

## Windows Commands

### Network Diagnostics

| Command    | Description                                          | Key Options / Examples                                                                                                |
| ---------- | ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `ipconfig` | Show IP configuration for all adapters               | `ipconfig /all` — detailed; `/release` — release DHCP lease; `/renew` — request new IP; `/flushdns` — clear DNS cache |
| `ping`     | Test connectivity between two hosts                  | `ping 8.8.8.8` — test internet; `ping -t <host>` — continuous; `ping -n 10 <host>` — send 10 packets                  |
| `tracert`  | Trace route and identify hops to destination         | `tracert google.com`; `-d` to skip DNS resolution                                                                     |
| `nslookup` | Query DNS records                                    | `nslookup google.com`; `nslookup google.com 8.8.8.8` — use specific DNS                                               |
| `netstat`  | View active network connections and ports            | `-a` all connections; `-n` numeric; `-b` show owning process; `-o` show PID                                           |
| `pathping` | Combines ping and tracert; shows packet loss per hop | `pathping google.com`                                                                                                 |
| `net`      | Manage network resources and users                   | `net use \\server\share` — map share; `net user` — view users; `net share` — view shares                              |
| `arp`      | View/modify ARP cache (IP-to-MAC mappings)           | `arp -a` — display cache                                                                                              |
| `nbtstat`  | NetBIOS over TCP/IP statistics                       | `nbtstat -n` — local names; `-a <hostname>` — remote names                                                            |

### File System Commands

| Command          | Description                            | Example                                                              |
| ---------------- | -------------------------------------- | -------------------------------------------------------------------- |
| `dir`            | List directory contents                | `dir /a` — include hidden; `dir /s` — recursive                      |
| `cd`             | Change directory                       | `cd C:\Users\Admin\Desktop`                                          |
| `md` / `mkdir`   | Create a directory                     | `mkdir NewFolder`                                                    |
| `rd` / `rmdir`   | Remove a directory                     | `rd /s /q OldFolder` — remove all contents without prompting         |
| `copy`           | Copy one or more files                 | `copy file.txt D:\backup\`                                           |
| `xcopy`          | Copy files and directory tree          | `xcopy /s /e /y source\ dest\`                                       |
| `robocopy`       | Robust file copy with advanced options | `robocopy src dst /mir` — mirror (sync); `/z` — restartable          |
| `move`           | Move files or rename directories       | `move file.txt C:\archive\`                                          |
| `del`            | Delete files                           | `del /f /q file.txt` — force delete without prompt                   |
| `ren` / `rename` | Rename file or directory               | `ren old.txt new.txt`                                                |
| `type`           | Display text file contents             | `type config.txt`                                                    |
| `attrib`         | Set or clear file attributes           | `attrib +h file.txt` — hide; `attrib -r file.txt` — remove read-only |
| `fc`             | File compare — show differences        | `fc file1.txt file2.txt`                                             |
| `tree`           | Display directory structure visually   | `tree /f` — include files                                            |
| `where`          | Find file location in PATH             | `where python`                                                       |

### System and Maintenance Commands

| Command                                      | Description                                                   | Notes                                                                       |
| -------------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `sfc /scannow`                               | System File Checker — scan and repair protected Windows files | Run as administrator; takes ~5 min                                          |
| `dism /online /cleanup-image /restorehealth` | Repair Windows component store using Windows Update           | Run before or after SFC if SFC fails                                        |
| `chkdsk`                                     | Check disk for file system errors                             | `/f` — fix errors; `/r` — find bad sectors; requires reboot on system drive |
| `diskpart`                                   | Interactive disk partitioning tool                            | Start with `list disk` and `detail disk`; verify the disposable lab disk before any destructive command |
| `format`                                     | Format a volume                                               | `format D: /fs:NTFS /q` — quick format as NTFS                              |
| `gpupdate /force`                            | Force Group Policy to re-apply                                | `/force` reapplies all policies                                             |
| `shutdown`                                   | Shutdown or restart the computer                              | `/s /t 0` — immediate shutdown; `/r /t 0` — immediate restart               |
| `tasklist`                                   | Display running processes                                     | `tasklist /fi "imagename eq chrome.exe"` — filter                           |
| `taskkill`                                   | End a running process                                         | `/im chrome.exe /f` — by name; `/pid 1234 /f` — by PID                      |
| `msinfo32`                                   | Display system information                                    | Run from Run dialog                                                         |
| `winver`                                     | Show Windows version and build number                         | Run from Run dialog                                                         |
| `regedit`                                    | Open Registry Editor                                          | Use with caution                                                            |
| `net start <service>`                        | Start a Windows service                                       | `net start "Print Spooler"`                                                 |
| `net stop <service>`                         | Stop a Windows service                                        | `net stop "Print Spooler"`                                                  |

> **Destructive operations:** `diskpart clean`, formatting, recursive deletion and `robocopy /mir` can erase data. Practice only on a disposable VM disk or backed-up test folder. `/mir` deletes destination items absent from the source. Confirm the selected disk and destination before proceeding.

---

### Boot and Recovery Commands (WinRE)

| Command               | Description                                   |
| --------------------- | --------------------------------------------- |
| `bootrec /fixmbr`     | Writes a new Master Boot Record               |
| `bootrec /fixboot`    | Writes a new boot sector                      |
| `bootrec /scanos`     | Scans for Windows installations on all drives |
| `bootrec /rebuildbcd` | Rebuilds the Boot Configuration Data store    |
| `bcdedit`             | View/edit boot configuration entries          |

---

## Linux / macOS Commands

### Navigation and File Operations

| Command  | Description                                | Example                                                               |
| -------- | ------------------------------------------ | --------------------------------------------------------------------- |
| `pwd`    | Print working directory (current location) | `pwd` → `/home/user`                                                  |
| `ls`     | List directory contents                    | `ls -la` — long format including hidden files                         |
| `cd`     | Change directory                           | `cd /etc`                                                             |
| `cp`     | Copy files or directories                  | `cp file.txt /tmp/`; `cp -r dir/ /backup/` — recursive                |
| `mv`     | Move or rename files                       | `mv old.txt new.txt`; `mv file.txt /new/path/`                        |
| `rm`     | Remove files or directories                | `rm file.txt`; `rm -rf dir/` — recursive force (caution)              |
| `mkdir`  | Create a directory                         | `mkdir -p /opt/app/config` — create parent dirs as needed             |
| `rmdir`  | Remove an empty directory                  | `rmdir emptydir`                                                      |
| `touch`  | Create empty file or update timestamp      | `touch newfile.txt`                                                   |
| `cat`    | Display file contents                      | `cat /etc/hosts`                                                      |
| `less`   | Scroll through a file                      | `less /var/log/syslog`                                                |
| `head`   | Show first N lines of a file               | `head -20 file.txt`                                                   |
| `tail`   | Show last N lines; follow live log         | `tail -f /var/log/syslog`                                             |
| `find`   | Search for files                           | `find /home -name "*.txt"`                                            |
| `locate` | Fast file search using a database          | `locate filename` (requires `updatedb`)                               |
| `grep`   | Search text patterns in files              | `grep "error" /var/log/syslog`; `-i` case-insensitive; `-r` recursive |
| `wc`     | Word/line/byte count                       | `wc -l file.txt` — count lines                                        |

### System Information and Processes

| Command    | Description                                        | Windows Equivalent           |
| ---------- | -------------------------------------------------- | ---------------------------- |
| `ps`       | Show running processes                             | `tasklist`                   |
| `ps aux`   | Show all processes with details                    | `tasklist /v`                |
| `top`      | Live process monitor                               | Task Manager                 |
| `htop`     | Interactive process monitor (installed separately) | Task Manager                 |
| `kill`     | Send signal to a process by PID                    | `taskkill /pid`              |
| `killall`  | Kill all processes with a given name               | `taskkill /im`               |
| `df`       | Disk free space                                    | `dir` (approximate)          |
| `du`       | Disk usage of a directory                          | —                            |
| `free`     | RAM usage                                          | Task Manager → Performance   |
| `uptime`   | How long the system has been running               | `net statistics workstation` |
| `uname -a` | Kernel version and system info                     | `winver`                     |
| `lscpu`    | CPU information                                    | `msinfo32`                   |
| `lsblk`    | List block devices (disks)                         | Disk Management              |
| `fdisk -l` | List disks and partitions (root)                   | `diskpart list disk`         |

> **Platform differences:** `ip`, `ss`, `free`, `lscpu` and `lsblk` are Linux tools, not standard macOS commands. On macOS use tools such as `ifconfig`, `route -n get default`, `netstat`, `vm_stat`, `system_profiler` and `diskutil`. Package managers and command options also vary; consult `man` on the target system.

---

### Networking Commands (Linux/macOS)

| Command      | Description                                         | Windows Equivalent       |
| ------------ | --------------------------------------------------- | ------------------------ |
| `ifconfig`   | Show/configure network interfaces (legacy)          | `ipconfig`               |
| `ip addr`    | Show IP addresses (modern replacement for ifconfig) | `ipconfig`               |
| `ip route`   | Show routing table                                  | `route print`            |
| `ping`       | Test connectivity                                   | `ping`                   |
| `traceroute` | Trace route to destination                          | `tracert`                |
| `nslookup`   | DNS query                                           | `nslookup`               |
| `dig`        | Advanced DNS query tool                             | —                        |
| `netstat`    | Network connections                                 | `netstat`                |
| `ss`         | Socket statistics (modern netstat)                  | `netstat`                |
| `curl`       | Transfer data from URLs; test HTTP                  | —                        |
| `wget`       | Download files from the web                         | —                        |
| `ssh`        | Secure Shell remote access                          | Remote Desktop (`mstsc`) |
| `scp`        | Secure copy over SSH                                | —                        |

### Permissions and Users

| Command   | Description                                  | Example                                              |
| --------- | -------------------------------------------- | ---------------------------------------------------- |
| `chmod`   | Change file permissions                      | `chmod 755 script.sh`                                |
| `chown`   | Change file owner/group                      | `chown user:group file.txt`                          |
| `chgrp`   | Change group only                            | `chgrp devteam file.txt`                             |
| `sudo`    | Run command as superuser                     | `sudo apt update`                                    |
| `su`      | Switch to another user                       | `su - username`                                      |
| `passwd`  | Change user password                         | `passwd username`                                    |
| `useradd` | Create new user                              | `sudo useradd -m newuser`                            |
| `usermod` | Modify user account                          | `sudo usermod -aG sudo username` — add to sudo group |
| `userdel` | Delete user                                  | `sudo userdel -r username` — remove home dir too     |
| `groups`  | Show group memberships                       | `groups username`                                    |
| `id`      | Show UID and group info                      | `id username`                                        |
| `who`     | Show logged-in users                         | `who`                                                |
| `w`       | Show who is logged in and what they're doing | `w`                                                  |

### Package Management

| Distro                   | Command | Example                                                        |
| ------------------------ | ------- | -------------------------------------------------------------- |
| Ubuntu/Debian            | `apt`   | `sudo apt install nmap`; `sudo apt update && sudo apt upgrade` |
| Red Hat/CentOS 7         | `yum`   | `sudo yum install nmap`                                        |
| Red Hat/Fedora/CentOS 8+ | `dnf`   | `sudo dnf install nmap`                                        |

### File Permissions Reference

```
Permission string:  - r w x r - x r - -
Position:           ↑ ↑ ↑ ↑ ↑ ↑ ↑ ↑ ↑ ↑
                    | | | | | | | | | |
                    type owner group others
```

| Symbol | Numeric | Permission    |
| ------ | ------- | ------------- |
| `r`    | 4       | Read          |
| `w`    | 2       | Write         |
| `x`    | 1       | Execute       |
| `-`    | 0       | No permission |

| Octal | String | Permissions    |
| ----- | ------ | -------------- |
| 7     | rwx    | Full access    |
| 6     | rw-    | Read + Write   |
| 5     | r-x    | Read + Execute |
| 4     | r--    | Read only      |
| 0     | ---    | No access      |

---

## Windows vs Linux Equivalents Quick Reference

| Task              | Windows                       | Linux/macOS                |
| ----------------- | ----------------------------- | -------------------------- |
| List directory    | `dir`                         | `ls`                       |
| Change directory  | `cd`                          | `cd`                       |
| Copy files        | `copy` / `xcopy` / `robocopy` | `cp` / `rsync`             |
| Move/rename       | `move` / `ren`                | `mv`                       |
| Delete file       | `del`                         | `rm`                       |
| Create directory  | `mkdir`                       | `mkdir`                    |
| Delete directory  | `rmdir /s`                    | `rm -rf`                   |
| Find text in file | `findstr`                     | `grep`                     |
| View processes    | `tasklist`                    | `ps aux`                   |
| Kill process      | `taskkill`                    | `kill` / `killall`         |
| Network config    | `ipconfig`                    | `ip addr` / `ifconfig`     |
| View open ports   | `netstat -an`                 | `netstat -an` / `ss -tuln` |
| DNS lookup        | `nslookup`                    | `nslookup` / `dig`         |
| Trace route       | `tracert`                     | `traceroute`               |
| Remote CLI access | `ssh` (PowerShell)            | `ssh`                      |
| View command help | `command /?`                  | `man command`              |
| Disk usage        | `dir /s`                      | `du -sh`                   |
| Free disk space   | —                             | `df -h`                    |

---

_See also: [Core_2/2.1_Operating_Systems.md](../Core_2/2.1_Operating_Systems.md) for full OS domain notes._
