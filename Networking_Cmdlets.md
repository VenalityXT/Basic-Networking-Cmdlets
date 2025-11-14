# Networking Lab Report  
Applied Networking Concepts – Windows & Ubuntu

## Overview  
This report documents a complete set of practical networking tasks performed across Windows and Ubuntu Linux environments.  
The work includes interacting with the network stack, analyzing configuration details, inspecting ARP and routing behavior, verifying DNS/DHCP functionality, and applying basic networking theory.  
All tasks were executed in isolated VirtualBox VMs, with screenshots captured to verify each step.

---

# Assignment 1 – Applied Networking Concepts (Windows)

## Task: Interact with the Windows networking stack  
Below are the required networking commands, their purposes, and documented outputs.

---

## 1. XipconfigX  
**Purpose:** Displays basic IP configuration including IPv4, subnet mask, gateway, and adapter state.

**Screenshot:**  
[Insert Screenshot: Windows – ipconfig]

---

## 2. Xipconfig /allX  
**Purpose:** Provides the full networking configuration, including:  
- Hostname  
- MAC address  
- DHCP status  
- DHCP lease information  
- DNS servers  
- Adapter details  
- Autoconfiguration settings  

**Screenshot:**  
[Insert Screenshot: Windows – ipconfig /all]

---

## 3. Xipconfig /releaseX  
**Purpose:** Attempts to release the system’s DHCP lease.  

### Notes on Behavior  
Initially, the VM returned:  
*“The operation failed as no adapter is in the state permissible for this operation.”*  
This occurred because the Ethernet interface had DHCP disabled at the host level.  
The Windows troubleshooter automatically re-enabled DHCP for the adapter, after which the release command worked as expected.

**Screenshot (before fix):**  
[Insert Screenshot: Windows – release error]

**Screenshot (after fix):**  
[Insert Screenshot: Windows – release successful]

---

## 4. Xipconfig /renewX  
**Purpose:** Requests a new DHCP address from the DHCP server.  
After DHCP was restored using the built-in troubleshooter, the command succeeded and obtained a valid 192.168.x.x address.

**Screenshot (before fix):**  
[Insert Screenshot: Windows – renew error]

**Screenshot (after fix):**  
[Insert Screenshot: Windows – renew successful]

---

## 5. Xping 8.8.8.8X  
**Purpose:** Tests reachability and round-trip latency to Google’s public DNS server using ICMP.

**Screenshot:**  
[Insert Screenshot: Windows – ping]

---

## 6. Xtracert 8.8.8.8X  
**Purpose:** Traces the route packets take to a destination, showing intermediate hops.

**Screenshot:**  
[Insert Screenshot: Windows – tracert]

---

## 7. Xarp -aX  
**Purpose:** Displays the system’s ARP table, showing IP-to-MAC address mappings.

**Screenshot:**  
[Insert Screenshot: Windows – arp -a]

---

# Assignment 2 – Applied Networking Concepts 2 (Windows)

## Required Tasks

### 1. Obtain MAC Address  
Command used: XgetmacX  
**Screenshot:**  
[Insert Screenshot: Windows – getmac]

---

### 2. Obtain IP Address  
Command used: XipconfigX  
**Screenshot:**  
[Insert Screenshot: Windows – ipconfig]

---

### 3. Obtain ARP Table Mapping  
Command used: Xarp -aX  
**Screenshot:**  
[Insert Screenshot: Windows – arp -a]

---

### 4. Explain ARP Table  
**Summary Explanation:**  
The ARP table stores mappings between Layer 3 IPv4 addresses and Layer 2 MAC addresses.  
Dynamic entries are learned through ARP requests and responses, while static entries represent reserved or broadcast mappings.  
Windows references this table to deliver frames on the local network segment.

---

### 5. Obtain DNS Server  
Command used: Xnslookup google.comX  
**Screenshot:**  
[Insert Screenshot: Windows – nslookup]

---

# Assignment 3 – Applied Networking Concepts (Ubuntu Linux)

## Required Tasks  
These commands were executed after installing Xnet-toolsX.

---

## 1. XifconfigX  
**Purpose:** Shows interface details such as IPv4 address, netmask, and MAC address.

**Screenshot:**  
[Insert Screenshot: Ubuntu – ifconfig]

---

## 2. Xping -c 4 8.8.8.8X  
**Purpose:** Tests connectivity and packet statistics.

**Screenshot:**  
[Insert Screenshot: Ubuntu – ping]

---

## 3. Xtraceroute 8.8.8.8X  
**Purpose:** Shows the path packets take through each router on the network.

**Screenshot:**  
[Insert Screenshot: Ubuntu – traceroute]

---

## 4. Xarp -aX  
**Purpose:** Displays ARP table entries for local network devices.

**Screenshot:**  
[Insert Screenshot: Ubuntu – arp -a]

---

# Assignment 4 – Applied Networking Concepts 2 (Ubuntu)

## 1. Obtain MAC Address  
Command used: Xip linkX  
**Screenshot:**  
[Insert Screenshot: Ubuntu – ip link]

---

## 2. Obtain IP Address  
Command used: Xip addr showX  
**Screenshot:**  
[Insert Screenshot: Ubuntu – ip addr]

---

## 3. Obtain ARP Table Mapping  
Command used: Xarp -aX  
**Screenshot:**  
[Insert Screenshot: Ubuntu – arp -a]

---

# Assignment 5 – Computer Networking Theory

## Required Devices  
For each device below, describe purpose, OSI layer, similarities/differences, and form factor.

### 1. Hub  
- Operates at Layer 1 (Physical)  
- Broadcasts all traffic to all ports  
- No MAC learning or switching logic  
- Minimum ports: typically 4  
- Form factor: small desktop device  

**Image Placeholder:**  
[Insert Image – Hub]

---

### 2. Switch  
- Operates at Layer 2 (Data Link)  
- Maintains MAC address tables  
- Sends frames only to the correct port  
- Minimum ports: 4–8  
- Form factor: desktop or rack-mount  

**Image Placeholder:**  
[Insert Image – Switch]

---

### 3. Router  
- Operates at Layer 3 (Network Layer)  
- Makes forwarding decisions based on IP routes  
- Connects different networks and performs NAT  
- Minimum ports: typically 2 (WAN/LAN)  
- Form factor: home router or enterprise rack-mount  

**Image Placeholder:**  
[Insert Image – Router]

---

# Assignment 6 – Network Theory Concepts

## 1. What Makes Up a MAC Address  
A MAC address is a 48-bit identifier consisting of:  
- **OUI** (first 24 bits) identifying the manufacturer  
- **Device ID** (last 24 bits) uniquely identifying the interface  

**Screenshot:**  
[Insert Screenshot – MAC address]

---

## 2. What Makes Up an IP Address  
An IPv4 address consists of:  
- Network portion  
- Host portion  
Defined by its subnet mask.  

**Screenshot:**  
[Insert Screenshot – IPv4 Address]

---

## 3. Explain DNS  
DNS translates human-readable names (google.com) into IP addresses.  
It operates at Application Layer and enables domain-based routing.

**Screenshot:**  
[Insert Screenshot – nslookup]

---

## 4. Explain DHCP  
DHCP automatically assigns IP configuration parameters including:  
- IPv4 Address  
- Subnet Mask  
- Default Gateway  
- DNS Servers  

It uses the DORA process: Discover, Offer, Request, Acknowledge.

**Screenshot:**  
[Insert Screenshot – DHCP lease proof from ipconfig /all]

---

## 5. Show DHCP Client Identifier (CLID) Request  
Command used: Xipconfig /renewX  
This forces the system to request a new lease from the DHCP server.

**Screenshot:**  
[Insert Screenshot – renew output]

---

# End of Document
