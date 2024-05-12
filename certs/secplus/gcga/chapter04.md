# **Securing Your Network**

## **Exploring Advanced Security Devices**

### **Understanding IDSs and IPSs**
`Intrusion detection systems` (IDS) monitor a network and send alerts when they detect suspicious events on a system or network.

`Intrusion prevention systems` (IPS) react to attacks and prevent them from reaching systems and networks.

#### **HIDS**
`Host-based intrusion detection system` is additional software installed on a system such as a workstation or server. It protects the individual host, can detect potential attacks, and protects critical operating system files.

#### **NIDS**
`Network-based intrusion detection system` monitors activity on the network. NIDS cannot detect anomalies on individual systems or workstations unless the anomaly causes a significant difference in network traffic.

#### **Sensor and Collector Placement** 
Depends on what you want to measure...

 - `Internet side` - will see all traffic and attacks on your network.
 - `Internal side` - will see what attacks make it into your network.
 - `Both sides` - lol just have two sensors duh.

#### **Detection Methods**
There are two primary detection methods:
 - `Signature-based (also called definition-based)` - uses a database of known vulnerabilities or known attack patterns.
 - `Heuristic- or behavioral-based (also called anomaly-based)` - Starts by collecting data on the network identifying the networks regular operation or normal behavior.

#### **Data Sources and Trends**
IDS commonly include an `aggregator` to store log entries from dissimilar systems. The IDS can analyze these log entries to provide insight to trends.

#### **Reporting Based on Rules**
IDS reports on events of interest based on rules configured within the IDS.

#### **False Positives Versus False Positives**

|                   | **Accurate**                       | **Not Accurate**                    |
|-------------------|------------------------------------|-------------------------------------|
| **No Attack**     | True Negative _(No alarm/alert)_   | False Positive _(Alarm/alert sent)_ |
| **Actual Attack** | True Positive _(Alarm/alert sent)_ | False Negative _(No alarm/alert)_   |


---

### **IPS Versus IDS-Inline Versus Passive**
| **IPS** 🛡                                                                                             | **IDS** 👀                                                                                                        |
|------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| Can detect, react to, and prevent attacks                                                            | Monitors and will respond after detecting an attack, but it doesn't prevent attacks                             |
| Is inline with traffic (all traffic passes through the IPS, and the IPS can block malicious traffic) | Is out-of-band with traffic. (it does monitor network traffic, but the traffic does not travel through the IDS) |

### **Honeypots** 🍯
A `honeypot` is a sweet looking server, or at least to an attacker. The server is often poorly locked down as to bait in an attack as the admins can analyze the attack and harden the main servers while not losing any of the CIA triad. Main goals being:
 - `Deceive the attackers and divert them from the live network`
 - `Allow observation of an attacker`

### **Honeynets** 🍯🍯🍯
A `honeynet` is a group of honeypots within a separate network or zone but accessible from an organization's primary network.

### **Honeyfile** 🍯📄
A `honeyfile` is a file designed to attract the attention of an attacker. The primary way a file can attract an attacker is by the name. (_i.e. password.txt_) 😂

### **Fake Telemetry**
Telemetry refers to collecting information such as statistical data and measurements and forwarding it to a centralized system for processing. `Fake telemetry` corrupts the data sent to monitoring systems and can disrupt a system.

---

## **Securing Wireless Networks**

### **Reviewing Wireless Basics**
 - `Access Point` - connects wireless clients to a wired network. However, many APs also have routing capabilities.
 - `All wireless routers are APs` - These are APs with an extra capability-routing.
 - `Not all APs are wireless routers` - Many APs do not have any additional capabilities.

#### **Band Selection and Channel Overlaps**
 - `2.4GHz` - far reaching / steady 
 - `5GHz` - near reaching / faster speeds

#### **Access Point SSID**
Wireless networks are identified by a service set identifier (SSID), which is simply the wireless network name.

#### **Enabling MAC Filtering**
The `MAC` address (also called a physical address or hardware address) is a 48-bit hexadecimal address used to identify network interface cards (NICs). `Media access control (MAC) filtering` can be enabled on many wireless routers. 

**Note**:
> MAC filtering can restrict access to a wireless network to specific devices. However an attacker can use a sniffer to discover allowed MAC addresses and proceed to `MAC clone` (change its MAC signature on their machine to gain access to the network) aka `MAC cloning attack`


---

### **Site Surveys and Footprinting** 🗺 🦶
`Site surveys` examine  the wireless env to identify potential issues such as areas with noise or other devices operating on the same frequency bands. They can often also generate `heat maps` of the physical location, which gives you a color-coded representation of wireless signals. Wireless `footprinting` creates a detailed diagram of APs and hotspots within an organization. By overlaying the heat map onto a basic architectural drawing of an organization's space. It's possible to see the location of the APs along with the `dead spots` and `hotspots`.

### **Wireless Access Point Placement**
The most commonly used wireless antenna on both APs and wireless devices is an omnidirectional (or omni) antenna.

### **Wireless Cryptographic Protocols**
Because wireless networks broadcast over the air, anyone who has a wireless can intercept the transmissions.

**Note**:
> In the early days of wireless networks, security was an afterthought. As a result, early wireless cryptographic protocols such as `Wired Equivalent Privacy(WEP)` and `Wi-Fi Protected Access(WPA)` were weak, and attackers quickly found ways to exploit them. WEP and WPA are deprecated and should not be used.

#### **WPA2 and CCMP**
The WiFi Alliance developed `WiFi Protected Access 2(WPA2)` to replace earlier cryptographic protocols. WPA2 (aka IEEE 802.11i) uses strong cryptographic protocols such as `Advanced Encryption Standard(AES)` and `Counter-mode/CBC-MAC Protocol(CCMP)`.

#### **Open, PSK, and Enterprise Modes**
WPA2 can operate in either `Open`, `pre-shared key(PSK)`, or `Enterprise` modes.
 - `Open mode` - doesn't use any security. Instead all data is transferred in clear text.
 - `PSK mode` - users access the wireless network anonymously with a PSK or passphrase. 
 - `Enterprise mode` - forces users to authenticate with unique credentials before granting them access to the wireless network.

When you select Enterprise mode, you'll need to enter three pieces of information:
 - `RADIUS server` - You enter the IP address assigned to the 802.1X server which is often a RADIUS server.
 - `RADIUS port` - You enter the port used by the RADIUS server. Default: 1812 Alt: 1645
 - `Shared Secret` - The shared secret is similar to a password, and you must enter it here exactly as it is entered on the RADIUS server. This is different than the user's password.

Note:
> This doesn't provide authentication; User claims identity with username and prove their identity with a password. While just a password without username provides authorization w/o authentication.

#### **WPA3 and Simultaneous Authentication of Equals**
`Wi-Fi Protected Access 3(WPA3)` - is the newest cryptographic protocol. It uses `Simultaneous Authentication of Equals(SAE)` instead of the PSK used with WPA2.

SAE is a variant of the Dragonfly Key Exchange, which is based on the Diffie-Hellman key exchange (initially published in 1976) aka robust, time-tested cryptographic protocols.

---

### **Authentication Protocols**
Wireless networks support several different authentication protocols. Many are built on the `Extensible Authentication Protocol(EAP)`, an authentication framework that provides general guidance for authentication methods.

Some methods are:
 - `EAP` - provides a method for two systems to create a secure encryption key, aka a `Pairwise Master Key(PMK)`
 - `Protected EAP(PEAP)` - provides an extra layer of protection for EAP by encapsulating the EAP conversation in a TLS tunnel. Requires a cert on the server but not the client.
 - `EAP-FAST` - Cisco designed EAP-Flexible Authentication via Secure Tunneling (EAP-FAST).
 - `EAP-TLS` - One of the most secure EAP standards, differs from PEAP by requiring cert on server and clients.
 - `EAP-TTLS` - Extension of PEAP, allowing systems to use older authentication methods. Cert only on the server.
 - `RADIUS Federation` - like SSO (a federation requires two or more entities (i.e. companies) that share the same identity management system)

### **IEEE 802.1X Security** 
`IEEE 802.1X` is a port-based authentication protocol. It requires users or devices to authenticate when they connect to a specific wireless access point or a specific physical port.

### **Controller and Access Point Security**
After doing a site survey and determining the best location for APs, it's also important to consider the physical security.

### **Captive Portals**
A `captive portal` is a technical solution that forces clients using web browsers to complete a specific process before it allows them to the network. Common examples include:
 - `Free Internet Access` - Many hospitals and other medical facilities provide free internet
 - `Paid Internet Access` - Many hotels, resorts, cruise ships, and airlines, provide internet access to customers but on a pay-as-you-go basis.
 - `Alternative to IEEE 802.1X` - Adding an 802.1X server can be expensive and is sometimes not a feasible option.

---

## **Understanding Wireless Attacks**

### **Disassociation Attacks**
Effectively sending a packet to an AP telling it to kick another device off.

### **Wi-Fi Protected Setup**
Allows users to configure wireless devices without typing in the passphrase. When WPS is pressed, theres a 30sec window to enter a pin or have the device connect. WPS is susceptible to brute-force attacks.

### **Rogue Access Point**
A `rogue access point(RAP)` is an AP placed within a network without official authorization. Slurps up packets. Can be wireless and physical.

### **Evil Twin**
An `evil twin` is a rogue access point with the same SSID (or similar) as a legitimate access point. You can think of the SSID of the of the evil twin as a twin of the legitimate AP's SSID.

### **Jamming Attacks**
Attacker can transmit noise or another radio signal on the same frequency used by a wireless network. This interferes with the wireless transmissions and can seriously degrade performance.

### **IV Attacks**
An `initialization vector(IV)` is a number used by encryption systems, and a wireless IV attack attempts to discover the pre-shared key after first discovering the IV.

### **Near Field Communication Attacks**
`Near Field Communication(NFC)` is a group of standards used on mobile devices that allow them to communicate with other mobile devices. NFC readers are used to conduct `eavesdropping attack`.

### **RFID Attacks**
`Radio-frequency Identification(RFID` systems include an RFID tags placed on objects. They are used to track and manage info on objects. Common attacks include:
 - `Sniffing or eavesdropping` - capture a token
 - `Replay` - using a sniffed token
 - `DoS` - spamming the reader with frequencies hindering the system useless

### **Bluetooth Attacks**
Bluetooth is a short-range wireless system used in `personal area networks(PANs)`. Common attacks include:
 - `Bluejacking` - is the practice of sending unsolicited messages to nearby bluetooth devices.
 - `Bluesnarfing` - refers to the unauthorized access to, or theft of information from, a bluetooth device.
 - `Bluebugging` - is like Bluesnarfing but takes it to the next level by installing a backdoor on the device to later be used over the internet.

### **Wireless Replay Attacks**
In a `replay attack`, an attacker captures data sent between two entities, modifies it, and then attempts to impersonate one of the parties by replaying the data.

### **War Driving and War Flying**
`War driving` is the practice of looking for a wireless networking. Although war driving is more common in cars you can just as easily do it by walking around in a large city. `War flying` is similar to war driving. However, instead of walking or driving around, people fly around in private planes. In some cases, people have intercepted wireless transmissions at altitudes of 2500ft.

---

## **Using VPNs for Remote Access** 
A `virtual private network(vpn)` is often used for remote access. Direct access VPNs allow users to access private networks via a public network. The public network is commonly the Internet, but it can also be a semiprivate leased line from a telecommunications company.

### **VPNs and VPN Appliances**
It's possible to create a `VPN` by enabling services on server. Larger organizations often use a VPN appliance which is dedicated device used for VPNs aka `VPN appliance`.

### **Remote Access VPN**
`Remote access VPN (aka direct access VPN)` allows remote users to connect to internal networks.

#### **IPsec as a Tunneling Protocol**
IPsec supports both **Tunnel mode** and **Transport mode**.
 - `Tunnel mode` - encrypts the entire IP packet, including both the payload and the packet headers, and VPNs commonly use Tunnel mode.
 - `Transport mode` - only encrypts the payload and is commonly used in private networks. there isn't any need to hide ip addresses in a closed ecosystem.

IPsec provides security in two ways:
 - `Authentication` - IPsec includes an `Authentication Header(AH)` to allow each of the IPsec conversation hosts to authenticate with each other before exchanging data.
 - `Encryption` - IPsec includes `Encapsulating Security Payload(ESP)` to encrypt data and provide confidentiality. ESP includes AH so it provides the CIA triad.

#### **SSL/TLS as a Tunneling Protocol**
Some tunneling protocols use TLS to secure the VPN channel. As an example `Secure Socket Tunneling Protocol(SSTP)` encrypts VPN traffic using TLS over port 443.

#### **Split Tunnel Versus Full Tunnel**
| Split tunnel                                                          | Full tunnel                                   |
|-----------------------------------------------------------------------|-----------------------------------------------|
| Administrator determines what traffic should use the encrypted tunnel | all traffic goes through the encrypted tunnel |

#### **Site-to-site VPNs**
`Site-to-site VPNs` includes two vpn servers that act as gateways for two networks separated geographically. (like on-base -> downtown bespin servers) 

#### **Always-On VPN**
When the host device is always using a VPN.

#### **L2TP as a Tunneling Protocol**
`Layer 2 Tunneling Protocol` is a tunneling protocol that is also used for VPNs. The most recent version is L2TPv3. However none of the L2TP versions provide any sort of encryption so it is not used by itself for VPN traffic. It is often paired with another protocol, such as IPsec, then passed to L2TP for the transport.

#### **HTML5 VPN Portal**
Some network devices include the ability to configure an `HTML5 VPN portal`. An HTML5 VPN allows users to connect to the VPNusing their web browser, making it rather simple for the users.

---

### **Network Access Control**
`Network Access Control(NAC)` methods provide continuous security monitoring by inspecting computers and preventing them from accessing the network if they fail the inspection.

#### **Host Health Checks**
Common host health checks are:
 - The clients firewall is enabled
 - The clients operating system is up to date and has all the current patches and fixes
 - the clients antivirus software is up to date and has all update signature definitions

#### **Agent Versus Agentless NAC**
 - `Permanent Agent NAC` - Installed and remains on the client
 - `Dissolvable Agent NAC` - Sometimes remains or self uninstalls after reporting the health check
 - `Agentless NAC` - Accomplished like a network scan done from a server on the network.

---

### **Authentication and Authorization Methods**

#### **PAP**
`Password Authentication Protocol(PAP)` - is used with Point-to-Point Protocol(PPP) to authenticate clients. Downside it sends passwords as cleartext over networks 😂

#### **CHAP**
`Challenge Handshake Authentication Protocol(CHAP)` - also uses PPP and authenticates remote users, but it is more secure than PAP. Client and server both know a shared secret (similar to a password) used in the authentication process.

#### **RADIUS**
`Remote Authentication Dial-In User Service(RADIUS)` - is a centralized authentication service. Instead of each individual VPN server needing a separate database to identify who can authenticate, the VPN servers forward the authentication request to a central RADIUS server. Like SSO.

#### **TACACS+**
Terminal Access Controller Access-Control System Plus(TACACS+) - is an alternative to RADIUS, and provides two essential security benefits over RADIUS. `Full Encryption` & `Multiple challenges and responses`. Can also interact with Kerberos.

**AAA Protocols** - provide authentication, authorization, and accounting.