# **Basic Networking Cmdlets**

[![Windows](https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white)](https://www.microsoft.com/windows)  [![Linux](https://img.shields.io/badge/Platform-Ubuntu-E95420?logo=ubuntu&logoColor=white)](https://ubuntu.com/)  [![PowerShell](https://img.shields.io/badge/Shell-PowerShell-5391FE?logo=powershell&logoColor=white)](https://learn.microsoft.com/powershell/)  [![Bash](https://img.shields.io/badge/Shell-Bash-4EAA25?logo=gnubash&logoColor=white)](https://www.gnu.org/software/bash/)  [![Networking](https://img.shields.io/badge/Domain-Networking-0052CC)]()  [![Documentation](https://img.shields.io/badge/Type-Technical_Documentation-grey)]()

---

## **Project Overview**

This project provides a technically detailed walkthrough of foundational networking commands across **Windows** and **Ubuntu Linux**, documenting how each tool exposes the behavior of the underlying network stack. The write-up emphasizes interpretation rather than basic usage; explaining what each output reveals about addressing, routing, ARP table population, DNS resolution, and DHCP negotiation.

Troubleshooting scenarios are included as well, notably resolving a DHCP failure inside a virtualized Windows environment by analyzing adapter behavior, switching VirtualBox networking modes, and validating DHCP client recovery. This mirrors the real diagnostic process used by system administrators, SOC analysts, and network technicians.


---

## **Skills Demonstrated**

Although the focus is on documentation and analysis rather than automation, this project reflects several core competencies relevant in enterprise environments:

### **Windows Networking Skills**
- Interpreting IPv4 addressing and subnet behavior  
- Reading full adapter profiles (DHCP, DNS, lease times, MAC addresses)  
- Validating connectivity with ICMP  
- Using traceroute to understand routing paths  
- Analyzing ARP tables for local L2 visibility  
- Diagnosing DHCP client failures and resolving VirtualBox networking issues  

### **Linux Networking Skills**
- Understanding interface state and addressing via `ifconfig`, `ip`, and `nmcli`  
- Performing ICMP, traceroute, and ARP analysis  
- Observing DHCP negotiation using `dhclient -v`  
- Comparing Linux vs. Windows networking behavior  

### **Troubleshooting & Analysis**
- Identifying misconfigured virtual networking modes  
- Restoring DHCP functionality  
- Correlating network-layer symptoms with system-level configuration  
- Producing organized technical documentation  

---

## **Why This Project Matters**

Enterprise IT environments rely heavily on accurate interpretation of networking tools. These commands are used daily to:

- Identify addressing conflicts  
- Confirm DHCP relay or scope integrity  
- Investigate ARP poisoning or duplicate MAC issues  
- Debug DNS resolution delays  
- Analyze latency or routing asymmetry  
- Validate host reachability and network segmentation  
- Understand how hypervisors alter network topology  

This project documents that workflow in a clean, repeatable format.

---

## **Full Documentation**

The full cross-platform analysis, including screenshots and detailed interpretation, is available here:

**[Basic_Networking_Cmdlets.md](./Basic_Networking_Cmdlets.md)**

---


