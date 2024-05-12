# **Exploring Networking Tech & Tools** 🕸

## **Reviewing Basic Networking Concepts** 🙃

| # | Layer          | Job                                   | Type     | Don't Forget |
|---|----------------|---------------------------------------|----------|--------------|
| 7 | `Application`  | Network Process to Application        | Data     | All          |
| 6 | `Presentation` | Data Representation & Encryption      | Data     | People       |
| 5 | `Session`      | Inter-Host Communication              | Data     | Seem         |
| 4 | `Transport`    | End-to-end Connections & Reliability  | Segments | To           |
| 3 | `Network`      | Path Determination & IP               | Packets  | Need         |
| 2 | `Data Link`    | Mac & LLC (Physical Addressing)       | Frames   | Data         |
| 1 | `Physical`     | Media, Signals, & Binary Transmission | Bits     | Processing   |

 ---

Some basic attack methods that happen over networks:
 - `Sniffing attack` - Attackers often use protocol analyzer to capture data sent over a network.
 - `DoS & DDoS` - A denial-of-service (DoS) attack is a service attack from a single source that attempts to disrupt the service provided by another system. A Distributed DoS (DDoS) attack includes multiple computers attacking a single target.
 - `Poisoning attack` - Many protocols store data in cache for temporary access. Poisoning attacks attempt to corrupt the cache with different data.

--- 

### **Basic Networking Protocols**

 - `TCP` - Provides connection-oriented traffic (guaranteed delivery)
 - `UDP` - Provides connectionless sessions (without a three-way handshake)
 - `IP` - The Internet Protocol (IP) identifies host in a TCP/IP network and delivers traffic from one host to another using IP addresses.
 - `ICMP` - Internet Control Message Protocol (ICMP) is used for testing basic connectivity and includes tools such as ping, pathping, and tracert.
 - `ARP` - Address Resolution Protocol (ARP) resolves IPv4 addresses. MACs are also called physical addresses or hardware addresses.


| Range           | Type                     |     |
| --------------- | ------------------------ | --- |
| `0`-`1023`      | Well-known Ports         |     |
| `1024`-`49151`  | Registered Ports         |     |
| `49152`-`65535` | Dynamic of Private Ports |     |

A few `Well known ports`:

| Port | Name     | Comment                                   |
|------|----------|-------------------------------------------|
| 21   | `ftp`      | File Transfer Protocol                    |
| 22   | `ssh`      | Secure Shell (SSH) service                |
| 23   | `telnet`   | Telnet service                            |
| 25   | `smtp`     | Simple Mail Transfer Protocol             |
| 80   | `http`     | Hypertext Transfer Protocol               |
| 88   | `kerberos` | Kerberos network authentication           |
| 115  | `sftp`     | Secure File Transfer Protocol             |
| 443  | `https`    | Secure Hypertext Transfer Protocol        |
| 993  | `imaps`    | Internet Message Access Protocol over SSL |
| 994  | `ircs`     | Internet Relay Chat over SSL              |
| 995  | `pop3s`    | Post Office Protocol v.3 over SSL         |

---

### **Implementing Protocols for Use Cases**

#### **Voice and Video Use Case**
 - Real-time Transport Protocol (RTP) - 🔓
 - Secure Real-time Transport Protocol (SRTP) - Secure
 - Session Initiation Protocol (SIP) - Traceable

#### **File Transfer Use Case**

- `FTP` - File Transfer Protocol
- `TFTP` - Trivial File Transfer Protocol
- `SSH` - Secure Shell
- `SSL` - Secure Sockets Layer
- `TLS` - Transport Layer Security
- `IPsec` - Internet Protocol security
- `SFTP` - Secure File Transfer Protocol (uses SSH)
- `FTPS` - File Transfer Protocol Secure (uses TLS)

SSL Vs. TLS
```
SSL has been compromised and is not recommended for use. In Sept 2014, a team at Google discovered a serious vulnerability with SSL that they named the POODLE attack. POODLE is short for Padding Oracle on Downgraded Legacy Encryption. SSL is not maintained so this vulnerability still remains. TLS is goated with the sauce.
```

#### **Email and Web Uses Cases**

 - `SMTP` - Simple Mail Transfer Protocol
 - `POP3/S` - Post Office Protocol v3
 - `IMAP4` & `Secure IMAP` - Internet Message Access Protocol
 - `HTTP`
 - `HTTPS`

#### **Directory Services and LDAPS**
`Lightweight Directory Access Protocol` (LDAP) - specifies the formats and methods used to query directories. `LDAP Secure` encrypts data with TLS using TCP port 636.

#### **Remote Access Use Case**
Telnet sends info over networks as cleartext thus ssh is often preferred when remoting into a machine. `Remote Desktop Protocol` (RDP) uses either TCP 3389 or UDP 3389 and allows users to access microsoft systems.

#### **OpenSSH**
A suite of tools that simplify the use of SSH to connect to remote servers securely. It also supports the use of SCP and SFTP to transfer files securely.

#### **Time Sync Use Case**
There are many instances where systems need to be using the same time (or at least reasonably close time). For example kerberos authentication requires all systems to be within 5 min of each other. `Network Time Protocol` (NTP)

#### **Network Address Allocation Use Case**
**Dynamic Host Configuration Protocol (DHCP)** - commonly used to dynamically assign IP addresses to hosts. DHCP also assigns other TCP/IP info, such as subnet masks, default gateways, DNS server address, and much more.

**IPv4** - IPv4 uses 32-bit IP addresses expressed in dotted decimal format.

**IPv6** - Although the number of IP addresses at first seemed inexhaustible, the Internet Assigned Numbers Authority (IANA) assigned the last block of IPv4 addresses in Feb 2011. IPv6 uses 128-bit IP addresses expressed in hexadecimal format.

#### **Domain Name Resolution Use Case**
The primary purpose of Domain Name System (DNS) is for domain name resolution. DNS resolves hostnames to IP addresses. Systems are constantly querying DNS, though it is usually transparent to users.

DNS Servers host data in zones, which you can think of as databases. Zones include multiple records such as the following:
 - `A` - Also called a host record. This Record holds the hostname and IPv4 address and is the most commonly used record in a DNS server.
 - `AAAA` - This record holds the hostname and IPv6 address. Similar to an A record but for IPv6
 - `PTR` - Also called a pointer record. It is the opposite of an A record. Instead of a DNS client querying DNS with the name, the DNS client queries DNS with the IP address.
 - `MX` - Also called mail exchange or mail exchanger. An MX record identifies a mail server used for email.
 - `CNAME` - A canonical name, or alias, allows a single system to have multiple names associated with a single IP address.
 - `SOA` - The start of authority (SOA) record includes information about the DNS zone and soe of its settings.

**DNSSEC** - One of the primary methods of preventing DNS cache poisoning is with Domain Name System Security Extensions (DNSSEC).  A suite of extensions to DNS that provides validation for DNS responses.

`nslookup` - command short for name server lookup to trouble problems related to DNS.

`dig` - the command-line tool has replaced nslookup on linux systems. It is sometimes referred to as domain info groper.

#### **Subscription Service Use Case**
Subscription-based business model.

#### **Quality of Service**
QoS -  Allows admins to prioritize certain types of traffic over other types of traffic.

---

## **Understanding Basic Networking Devices**

`Unicast` - One-to-one traffic
`Broadcast` - One-to-all traffic

### **Switches** 🛑
This device learns which computers are attached to each of its physical ports. It then uses this knowledge to create internal switched connections when two computers communicate with each other.

#### **Security Benefits of a Switch**
If the traffic isnt unicast, a sniffer could capture data. Hubs on the otherhand broadcast unicast messages out to everyone. Due to this reason I'm out... jk companies just uses switches now. 

#### **Port Security**
`Port security` limits the computers that can connect to physical ports on a switch. MAC filtering is another example of port security.

#### **Broadcast Storm and Loop Prevention**
`Spanning Tree Protocol (STP)` or the newer `Rapid STP` (RSTP) both provide `broadcast storm prevention` and `loop prevention`.

#### **Bridge Protocol Data Unit Guard**
STP sends `Bridge Protocol Data Unit (BPDU)` messages in a network to detect loops. When the loops are detected, STP shuts down or blocks traffic from switch ports sending redundant traffic.

---

### **Routers** 🚦
`Routers` connects multiple network segments into a single network and routes traffic between the segments.

#### **Routers and ACLs**
`Access control lists (ACLs)` are rules implemented on a router (and on firewalls) to identify what traffic is allowed and what traffic is denied.

Router ACLs provide basic packet filtering. They filter packets based on IP addresses, ports, and some protocols, such as ICMP or IPsec. based on the protocol identifiers:
- `IP addresses and networks`
- `Ports`
- `Protocol numbers`

#### **Implicit Deny**
`Implicit deny` is an important concept to understand, especially in the context of ACLs. Setting rules within the router to grant access to specific servers.

#### **The Route Command and Route Security**
`route` command is used to display or modify a systems's routing table on both Windows and Linux systems.

---

### **Firewalls** 🧱
A `firewall` filters incoming and outgoing traffic for a single host or between networks.

#### **Host-Based Firewalls**
Monitors traffic going in and out of a single host, such as a server or workstation.

#### **Software Vs. Hardware Firewalls**
Software is an application on like a host machine, hardware is a device that is dedicated to managing traffic.

#### **Stateless Firewall Rules**
`Stateless firewalls` use rules implicated in ACLs to identify allowed and block traffic. They generally include the following elements:
 - `Permission`
 - `Protocol`
 - `Source`
 - `Destination`
 - `Port` || `Protocol`

#### **Stateful Vs. Stateless**
A stateful inspects traffic and makes decisions based on the traffic context or state. Stateless has rules to follow and will follow them exactly.

#### **Web Application Firewall**
A `web app firewall (waf)` is a firewall specifically designated to protect web applications.

#### **Next-Gen Firewall**
A `next-gen firewall (NGFW)` is an advanced firewall that adds capabilities that aren't available in first-gen or second-gen firewalls. NGFW performs deep-packet inspection, adding application-level inspection as a core feature. Which  it can then identify application commands and detect potentially malicious traffic.

---

## **Implementing Network Designs**

### **Intranet Vs. Extranet**

 - `Intranet` - is an internal network.
 - `Extranet` - is part of a network that can be accessed by authorized entities from outside of the network.

### **Screened Subnet**
A `screened subnet` (aka a demilitarized zone or DMZ) is a buffered zone between a private network and the internet.

#### **Network Address Translation Gateway**
`Network Address Translation` is a protocol that translates public ip addresses to private and vis versa.

 - Public IP addresses dont need to be purchased for all clients
 - NAT hides internal computers from the internet

 - Static NAT
 - Dynamic NAT

#### **Physical Isolation and Air Gaps**
Network literally cannot reach out ever. Supervisory control and data acquisition (SCADA) systems. Like powerplants, water treatment facilities.

#### **Logical Separation and Segmentation**
Routers segment traffic between networks using rules withing ACLs. Administrators use subnetting to divide larger IP addresses into smaller ranges.

#### **Isolating Traffic with VLAN**
A `virtual local area network (vlan)` uses a switch group several different computers into a virtual network.

#### **East-West Traffic**
`east-west` traffic refers to traffic between servers.

#### **Zero Trust**
A `zero trust network` is a network that doesn't trust any devices by default.

---

### **Network Appliances**
`Network appliances` are dedicated systems designed to fulfill a specific need.

### **Proxy Servers**
Many networks use proxy servers (or forward proxy servers) to forward request for services (such as HTTP and HTTPS).

#### **Caching Content for Performance**
The proxy server increase performance of Internet by caching each result received from the Internet.

#### **Transparent Proxy Vs. Non-Transparent Proxy**
`Transparent proxy` will accept and forward request without modifying them. `non-transparent proxy` server can modify or filter request.

#### **Reverse Proxy**
A `reverse proxy` accepts request from the internet, typically for a single web server.

---

### **Unified Threat Management**
Unified Threat Management (UTM) is a single solution that combines multiple security controls. Which might include:
 - `URL filtering`
 - `Malware inspection`
 - `Content inspection`
 - `DDoS mitigator`

### **Jump Server**
A `jump server` (sometimes called a jump box) is a hardened server used to access and manage devices in another network with a different security zone.

### **Security Implications for IPv6**
It new so old machines might freak out when given IPv6