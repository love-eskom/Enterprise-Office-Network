# Troubleshooting Guide

## Problem 1

### Issue
PCs were not receiving IP addresses.

### Cause
Router was not forwarding DHCP broadcasts across the isolated network zones.

### Solution
Configured `ip helper-address` on every router subinterface to act as an active relay.

---

## Problem 2

### Issue
DNS returned: Hostname Unresolved.

### Cause
DNS record had not been added to the application server data table.

### Solution
Created the DNS record: `www.techsolutions.local` pointing to `192.168.50.4`.

---

## Problem 3

### Issue
SSH connection failed.

### Cause
RSA keys had not been generated to activate the encryption engine.

### Solution
Configured:
- hostname
- ip domain-name
- crypto key generate rsa

Enabled SSH on VTY lines.

---

## Problem 4

### Issue
Guest VLAN could access internal departments.

### Cause
ACL not applied to the interface gateway checkpoint.

### Solution
Created an Extended ACL and applied it inbound on VLAN 40.

---

## Problem 5

### Issue
Folder generation failed with positional parameter errors in terminal.

### Cause
Attempted to run Linux-style space-separated folder targets (`mkdir docs configs screenshots`) inside Windows PowerShell 5.1.

### Solution
I swapped spaces for commas (`mkdir docs, configs, screenshots`) to match PowerShell array syntax rules.

---

## Problem 6

### Issue
Git status and branch pushing commands threw a fatal repository error.

### Cause
Ran Git workflows before initializing the local project tracking database or adding trackable files.

### Solution
Executed `git init` to build the hidden tracking registry, and added physical file entries using `New-Item`.

---

## Problem 7

### Issue
Switch port range command allocation was rejected by the system.

### Cause
A three-digit syntax entry typo (`interface range fa03/1-5`) was passed to fixed 24-port switch hardware.

### Solution
Corrected the command string to align with valid hardware numbers (`interface range fa0/1-5`).

---

## Problem 8

### Issue
Core infrastructure trunk port uplink connection failed to route traffic.

### Cause
Port `Fa0/24` was accidentally locked down inside Access VLAN 50 (Servers), stripping away transport tags.

### Solution
Cleared the access mapping rule using `no switchport access vlan 50` and explicitly forced `switchport mode trunk`.

---

## Problem 9

### Issue
Trunk port refused to activate or drop out of the standard `show vlan brief` table.

### Cause
The physical copper straight-through link was plugged into port `Fa0/1` instead of the configured `Fa0/24` interface.

### Solution
Deleted the line, re-wired the cable from Switch port `Fa0/24` to Router port `Gig0/0`, and issued `no shutdown`.

---

## Problem 10

### Issue
The web browser returned a "Server Reset Connection" alarm page.

### Cause
Attempted to fetch web assets from `http://192.168.50.3` (The DNS Server) which doesn't host an active web daemon.

### Solution
Directed browser endpoint requests to the actual functional target Web Host IP address: `http://192.168.50.4`.

---

## Problem 11

### Issue
Guest network client computers completely lost access to their own local default gateway.

### Cause
Broad extended ACL rules on the router sub-interface accidentally blocked communications targeting the gateway itself.

### Solution
Placed an explicit gateway safety override permit statement (`permit ip 192.168.40.0 0.0.0.255 host 192.168.40.1`) at the very top of the list.

---

## Problem 12

### Issue
Topology diagram failed to render locally in the markdown preview pane.

### Cause
Directory depth syntax tracking mismatch (`screenshots/topology.png`) because the document was executed from inside the `docs` folder.

### Solution
Prepended parent directory tracking flags to step backward out of the subfolder boundary path (`../screenshots/topology.png`).

---

## Useful Verification Commands

### Switch
show vlan brief
show interfaces trunk
show port-security
show running-config

---

### Router
show ip interface brief
show access-lists
show ip route
show running-config
show ip ssh
