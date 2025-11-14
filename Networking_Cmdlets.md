Basic Networking Command List  
Applied Networking Concepts – Windows and Ubuntu

This report documents hands-on interaction with the Windows and Ubuntu networking stacks using common administrative utilities. All tasks were performed inside VirtualBox virtual machines, with screenshots captured throughout. The work includes analyzing IP configuration, validating DHCP behavior, resolving DNS, inspecting ARP tables, tracing routes, and reviewing foundational networking theory. Troubleshooting is also incorporated, including resolving DHCP failures through Windows' automated repair tools.

  
**Windows Networking – Command Usage and Analysis**

```PowerShell
ipconfig
```  
Used to display core network details such as IPv4 address, subnet mask, and default gateway. This provides a quick view of the system’s active interface configuration.  

<img width="598" height="246" alt="ipconfig" src="https://github.com/user-attachments/assets/e535c7be-c7d2-41de-a285-2abe1f001998" />

```PowerShell
ipconfig /all
```  
Shows full adapter configuration including hostname, MAC address, DHCP status, DNS servers, lease information, and detailed network parameters.  

<img width="684" height="480" alt="ipconfig all" src="https://github.com/user-attachments/assets/6eb174a9-530c-4329-b3f4-c293ae22ed33" />


```PowerShell
ipconfig /release
```  
Attempts to drop the current DHCP lease. The command initially failed with “The operation failed as no adapter is in the state permissible for this operation,” which indicated the Ethernet interface was not using DHCP. The issue was resolved by running the Windows Network Troubleshooter, which re-enabled DHCP for the adapter. After DHCP was restored, the command successfully released the address.  

<img width="539" height="113" alt="ipconfig release" src="https://github.com/user-attachments/assets/65d1c3bd-81e6-4871-ba94-9518480f7d87" />

<img width="521" height="186" alt="ipconfig release FIXED" src="https://github.com/user-attachments/assets/704cc8b4-7f26-439f-84f6-d84e91a6a2ad" />

```PowerShell
ipconfig /renew
```
Requests a new DHCP lease. Prior to fixing DHCP, the command returned an error. Once DHCP was re-enabled via troubleshooting, Windows successfully obtained a valid 192.168.x.x address.  

<img width="541" height="110" alt="ipconfig renew" src="https://github.com/user-attachments/assets/429c7ae6-919c-4594-adae-34fa28f007ee" />

<img width="521" height="209" alt="ipconfig renew FIXED" src="https://github.com/user-attachments/assets/ee33e651-63eb-4043-9f63-643873ca0764" />

```PowerShell
ping 8.8.8.8
```  
Used to verify connectivity and measure round-trip time to Google’s public DNS server. Confirms ICMP operation and basic external reachability.  

<img width="458" height="212" alt="ping" src="https://github.com/user-attachments/assets/50c692d4-e3ef-44ca-8911-58de3fc166a3" />

```PowerShell
tracert 8.8.8.8
```
Displays the route traffic takes from the local machine to the destination, showing each routing hop along the path.  

<img width="646" height="334" alt="tracert" src="https://github.com/user-attachments/assets/ca729c1f-93df-4637-a811-b8426ec68d3f" />

```PowerShell
arp -a
```
Displays the ARP table, which contains mappings between IPv4 addresses and their corresponding MAC addresses.  

<img width="435" height="178" alt="arp" src="https://github.com/user-attachments/assets/f2231518-fffd-42ae-8886-c2cb8dec9e87" />
  
**Windows – Additional Networking Tasks**

Obtaining the MAC Address  
`getmac` was used to retrieve the system’s physical (MAC) address.  

<img width="636" height="103" alt="getmac" src="https://github.com/user-attachments/assets/5a074a78-c05b-482d-8386-74092323aa2d" />

DNS Server Query  
`nslookup google.com` was used to identify the DNS resolver and confirm successful name resolution.  

<img width="347" height="145" alt="nslookup" src="https://github.com/user-attachments/assets/bcac0146-b7aa-4429-9f8b-dffbf730774a" />


Explanation of the ARP Table  
The ARP table stores IPv4-to-MAC address mappings that allow communication on the local network. Windows dynamically updates these entries as devices are discovered. The table enables Layer 3 to Layer 2 translation so that Ethernet frames can be delivered to the correct physical device.

---
  
## Ubuntu Linux Networking – Command Usage and Analysis

```Bash
ifconfig
```  
Displays interface information such as IPv4 address, broadcast address, netmask, and MAC address.  

<img width="859" height="629" alt="ubuntu ifconfig" src="https://github.com/user-attachments/assets/c33bf531-7eaf-459a-a671-fa5fc6c0b0b4" />

```Bash
ping -c 4 8.8.8.8
```
Tests connectivity to an external host with a fixed number of ICMP requests.  

<img width="661" height="227" alt="ubuntu ping" src="https://github.com/user-attachments/assets/b52f8124-6cff-4f57-bcbe-c1cbc6cfecd8" />

```Bash
traceroute 8.8.8.8
```  
Shows the path each packet takes across intermediary routers to reach the destination.  

<img width="673" height="732" alt="ubuntu traceroute" src="https://github.com/user-attachments/assets/9850b1e5-ee60-4a69-b820-3fe95db9a974" />

```Bash
arp -a
```
Shows IP-to-MAC address mappings known by the local Linux system.  

<img width="586" height="50" alt="ubuntu arp" src="https://github.com/user-attachments/assets/9ea33134-118f-4497-b455-fa7fee71a89f" />
  
**Ubuntu – Additional Networking Tasks**

MAC Address  
Identified using ```ip link```.  

<img width="1152" height="146" alt="ubuntu ip link" src="https://github.com/user-attachments/assets/a21fc817-5c78-40f2-aab7-dd7cf41d075b" />

IP Address  
Identified using ```ip addr show```.  

<img width="1019" height="432" alt="ubuntu ip addr show" src="https://github.com/user-attachments/assets/5bb1c38f-0ced-4fff-80f4-e3aaf06583ec" />



DHCP Verification  
The `nmcli device show` command confirms DHCP-provided IPv4 configuration and shows DHCP options delivered by the server.  

<img width="912" height="923" alt="ubuntu nmcli device show" src="https://github.com/user-attachments/assets/9033bfc6-f0c3-45bb-b764-3a3170273e69" />

DHCP Client Request  
Xsudo dhclient -vX was used to demonstrate a DHCP discovery and request sequence from the Linux VM.  
[Screenshot – dhclient]

**Networking Devices – Hub, Switch, Router**

Hub  
A hub operates at the Physical Layer (Layer 1). It repeats incoming signals out all other ports without inspecting traffic. It does not maintain MAC tables, does not filter frames, and broadcasts all traffic. Common form factors include small desktop devices with at least four ports.  

<img width="800" height="450" alt="image" src="https://github.com/user-attachments/assets/9c50db83-cfbc-4a14-83c2-a11b9a5d13b8" />

Switch  
A switch operates at the Data Link Layer (Layer 2). It maintains a MAC address table and forwards frames only to the correct destination port. This reduces collisions and improves efficiency. Switches typically start at four to eight ports and come in desktop or rack-mount form factors.  

<img width="800" height="450" alt="image" src="https://github.com/user-attachments/assets/432c2fd3-098a-4616-b254-9c06390ad337" />

Router  
A router operates at the Network Layer (Layer 3). It makes forwarding decisions based on IP addresses, performs routing between networks, and may implement NAT and firewall functions. Routers generally include at least two interfaces (LAN/WAN) and are available as home devices or enterprise rack-mounted units.  

<img width="800" height="233" alt="image" src="https://github.com/user-attachments/assets/f80b6ad2-1c6b-44dd-87e7-411da775e897" />
  
**Networking Theory – MAC, IP, DNS, DHCP, DORA**

What Makes Up a MAC Address  
A MAC address is a 48-bit identifier composed of an Organizationally Unique Identifier (first 24 bits) and a device-specific identifier (last 24 bits). It uniquely identifies a network interface at Layer 2.  

<img width="800" height="674" alt="image" src="https://github.com/user-attachments/assets/ec6a6d58-5d62-42b7-a4ae-fa7c8223d502" />

What Makes Up an IP Address  
An IPv4 address consists of a network portion and a host portion, defined by the subnet mask. The network portion identifies the network, while the host portion identifies devices within that network.  

<img width="823" height="402" alt="image" src="https://github.com/user-attachments/assets/86a06bdc-9ab9-4bb2-9cb1-c161bc1ba8e8" />

Explanation of DNS  
DNS resolves human-readable domain names into numerical IP addresses. It is essential for locating servers, web services, and network resources.

Explanation of DHCP  
DHCP automatically assigns IP addresses and related configuration (gateway, DNS, subnet mask). This allows systems to join networks without manual configuration.  
[Screenshot – DHCP lease information]

Explanation of the DORA Process  
DHCP uses a four-step sequence:  
• Discover – The client broadcasts a request for configuration  
• Offer – The DHCP server responds with an available address  
• Request – The client formally requests that address  
• Acknowledge – The server approves the lease and provides configuration  
[Screenshot – DHCP client request]


