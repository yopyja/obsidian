# **Securing Hosts and Data**

## **Summarizing Virtualization Concepts**
`Virtualization` allows you to host one or more virtual systems, or `virtual machines` (VMs), on a single physical machine.

When discussing VMs we should understand a few of the following terms:
 - `Hypervisor` - software that creates, runs, and manages the VMs is the Hypervisor.
 - `Host` - physical system hosting the VMs is the host.
 - `Guest` - operating systems running on the host system are guests or guest machines.
 - `Host scalability` - refers to the ability to resize the computing capacity of the VM.
 - `Host elasticity` - refers to the ability to dynamically change resources assigned to the VM based on the load.

> Virtualization typically provides the best `return on investment` (ROI) when an organization has many underutilized servers.

### **Thin Client and Virtual Desktop Infrastructure**

A `thin client` is a computer with enough resources to boot and connect to a server to run specific applications or desktops. While a `virtual desktop infrastructure (vdi)` hosts a user's desktop operating system on a server.

### **Containers**
`Container Virtualization` runs services or applications within isolated `containers` or `application cells`.

```
 [ App ]  [ App ]  [ App  ]
    ↕️        ↕️        ↕️
 [    Host OS Kernel      ]
             ↕
 [ Host Computer Hardware ]     
```

### **VM Escape Protection**  🔥
`VM escape` is an attack that allows an attacker to access the host system from within the virtual system. Vendors release patches to prevent these attacks from happening, stay up to date.

### **VM Sprawl Avoidance**
`VM spawl` occurs when an organization has many VMs that aren't appropriately managed. Ensure policies are up to snuff with the VM management to prune deprecated machines.

### **Replication** 
It's worth pointing out virtual machines are simply files. Making copies of these VM files, you can use them as backups. Replication makes it easy to restore a failed virtual server.

### **Snapshots** 📸
A `snapshot` provides you with a copy of a VM at a moment in time, which you can use as a backup. Admins commonly take snapshots of systems prior to performing any risky operation.

### **Non-Persistance**
`Persistance` is when a user logs into a vm and makes changes to system files n such... they will stay. `Non-Persistance` is when say a user logs off a vm and the image rolls back to a preconfigured snapshot to save resources.

---

## **Implementing Secure Systems**

### **Endpoint Security**
`Endpoints` are computing devices such as servers, desktops, laptops, mobile devices, or IoT devices. `Endpoint detection and response (EDR)`, sometimes called `endpoint threat detection and response (EDTR)`, provides continuous monitoring of endpoints.

EDR tools are part of a defense-in-depth strategy. Commonly uses HIDS n such for protection.

### **Hardening Systems**
`Hardening` is the practice of making operating systems (OS) or applications more secure from its default installation. 

### **Configuration Management**
`Configuration Management` practices help organizations deploy systems with secure configurations. Admins often use baselines and imaging with configuration management.

### **Secure Baseline and Integrity**
A `baseline` is a known starting point, and organizations commonly use `secure baselines` to provide known starting points for systems. The use of baselines works in the three steps:
 1. `Initial baseline configuration` - admins use various tools to deploy systems consistently in a secure state.
 2. `Integrity measurements for baseline deviation` - automated tools monitor the system for any baseline changes, which is a common security issue. 
 3. `Remediation` - NAC methods can detect some changes to baseline settings and automatically isolate or quarantine system in a remediation network.

### **Using Master Images for Baseline Configurations**
One of the most common methods of deploying systems is with images starting with a master image.
 1. Admins start with a blank VM and configure it to specification
 2. They then capture the image which it then becomes the `master image`
 3. Lastly they deplo

This provides a `secure starting point` and `reduce costs`

### **Patch Management Policy**
`Patch management` ensures that systems and applications stay up to date with current patches. This is one of the most efficient ways to reduce operating system and application vulnerabilities.

### **Change Management Policy**
The worst enemies of many networks have been unrestrained administrators. Policies / rules of engagement on how to patch, manage, deploy, and delete anything should always be in place to keep everyone accountable.

### **Application Approved Lists and Block Lists**
Whitelisting and blacklisting software on systems duh

### **Application Programming Interfaces**
`Application Programming Interface (API)` - is a software component that gives developers access to features or data within another application, a service, or an operating system.

APIs are susceptible to attacks, so developers need to address several API considerations to ensure that the APIs aren't vulnerable:
 - `Authentication`
 - `Authorization`
 - `Transport level security`

### **Microservice and APIs**
`Microservices` are code modules designed to do one thing well. They are typically small code modules that receive a value and respond with a value.

### **FDE and SED**
`Full disk encryption (FDE)` encrypts an entire disk. `Self-encrypting drives (SEDs)`, also known as hardware-based FDE drives. When users power up the machine, they enter their credentials to decrypt the drive and boot the system

---

### **Boot Integrity**
`Boot integrity` verifies the integrity of the operating system and boot loading systems. A `measured boot` goes through enough of the boot process to perform these checks without allowing a user to interact with the system.

#### **Boot Security and UEFI**
The `Basic Input/Output System(BIOS)` includes software that provides a computer with basic instructions on starting. Newer systems use `Unified Extensible Firmware Interface(UEFI)` instead of BIOS. UEFI performs many of the same functions as BIOS but provides enhancements. For example, it can boot from larger disks, and it is designed to be CPU-independent.

#### **Trusted Platform Module**
A `trusted platform module(TPM)` is a hardware chip on the computer's motherboard that stores cryptographic keys used for encryption.

TPM supports secure `boot attestation` processes. When the system boots, the `secure boot` process checks the files against stored signatures to ensure they haven't changed.

`Remote attestation` process works like the secure boot process. Instead of checking the boot files against the report stored in the TPM, it uses a separate system.

TPMs ship with a unique `Rivest, Shamir, Adleman(RSA)` private key burned to it, which is used for asymmetric encryption and can be sued to support authentication. This private key is matched with a public key and provides a `hardware root of trust` or a known secure starting point.

#### **Hardware Security Module**
A `hardware security module(HSM)` is a security device you can add to system to manage, generate, and securely store cryptographic keys.

A `microSD HSM` is a microSD card that includes an HSM.

---

### **Protecting Data**
Data is the most valuable resource any org manages, second only to its people. If you ever tune into the news, you've likely heard about data breaches at organizations around the world. secure coding techniques and well enforced confidentiality (like encryption) is key.

---

### **Data Loss Prevention**
Organizations often use `data loss prevention(DLP)` techniques and technologies to prevent data loss.

#### **Rights Management**
`Rights management` (often called digital rights management) refers to the technologies used to provide copyright protection for copyrighted works.

#### **Removable Media**
USB type stuff... in short they pretty risky.

#### **Data Exfiltration**
`Data exfiltration` is the unauthorized transfer of data outside an organization and is a significant concern.

#### **Protecting Confidentiality**
Refer to chapter 1

#### **Database Security**
salted hashes & tokenization

---

## **Summarizing Cloud Concepts**
`Cloud computing` refers to accessing computing resources via a different location than your local computer.

Amazon Elastic Compute Cloud (Amazon EC2) provide a wide range of services combining virtualization with cloud computing.

### **Software as a Service** 🕸
`Software as a Service(SaaS)` includes any software or application provided to users over a network such as the Internet. Internet users access the SaaS apps via a web browser.

### **Platform as a Service**
`Platform as a Service(PaaS)` provides customers with a preconfigured computing platform they can use as needed. It provides the customer with and easy-to-configure operating system, combined with appropriate applications and on-demand computing.

### **Infrastructure as a Service**
`Infrastructure as a service(IaaS)` allows an organization to outsource equipment requirements, including hardware and all other support operations. The IaaS service provider owns the equipment, houses it in its data center, and performs all the required hardware maintenance. The customer essentially rents access to the equipment and often pays on a per-use basis.

### **Anything as a Service**
`Anything as a Service(XaaS)` refers to cloud services beyond SaaS, PaaS, and IaaS. XaaS includes a wide assortment of services that can be delivered via the cloud, such as communications, databases, desktops, storage, security, and more.

### **Cloud Deployment Models**
 - `Public cloud` like amazon, google, ms, and apple.
 - `Private cloud` like spacecamp
 - `Community cloud` il2 spacecamp 
 - `Hybrid cloud` combination of multiple clouds

### **Managed Security Service Provider**
A `managed security service provider(MSSP)` is a third-party vendor that provides security services for smaller companies.

MSSP may provide:
 - Patch management
 - Vulnerability scanning
 - Spam and virus filtering
 - Data loss prevention(DLP)
 - Virtual private network connections
 - Proxy services for web content filtering
 - Intrusion detection and prevention systems
 - Unified threat management(UTM) appliances
 - Advanced firewalls such as next-gen firewalls(NGFWs)

### **Cloud Service Provider Responsibilities**
`Cloud service provider(CSP)` is an entity that offers one or more cloud services via one or more cloud computing models.

### **Cloud Security Controls**
When picking a CSP, and organization needs to consider various cloud security controls. 

Listed security controls:
 - `High availability and high availability across zones`
 - `Resource policies`
 - `Secrets management`
 - `Secrets management`
 - `Integration and auditing`

Cloud-based storage have the following characteristics:
 - `Permissions`
 - `Encryption`
 - `Replication`

Cloud-based networks have the following characteristics:
 - `Virtual networks`
 - `Public and private subnets`
 - `Segmentation`
 - `Security Groups`
 - `Dynamic resource allocation`
 - `Instance awareness`
 - `Virtual private cloud(VPC) endpoint`
 - `Transit gateway`
 - `Container security`

---

### **On-Premises Versus Off-Premises**

| **On-Premises**                                                              | **Off-Premises**                                                      |
|--------------------------------------------------------------------------|-------------------------------------------------------------------|
| Organization retains complete control over all the cloud based resources, can be expensive to maintain | CSP performs the maintenance, and ensures hardware is operational, data location is unknown |

---

### **Cloud Access Security Broker**
A `cloud access security broker(CASB)` is a software deployed between an organization's network and cloud provider. It provides security by monitoring traffic and enforces security policies.

### **Cloud-Based DLP**
`Cloud-based DLP` solutions allow an organization to implement policies for data stored in the cloud.

### **Next-Gen Secure Web Gateway**
A `next-gen secure web gateway(SWG)` is a combination of a proxy server and a stateless firewall.

Some services it can provide are:
 - URL filtering
 - Stateless packet filtering
 - Malware detection and filtering
 - Network-based data loss protection(DLP)
 - Sandboxing to check for threats

### **Firewall Considerations**
When creating virtual networks in the cloud, there are some additional items to consider. Cloud based firewalls operate on all seven layers of the OSI model. cost depends on how you utilize them with you CSP.

### **Infrastructure as Code**
`Infrastructure as Code` refers to managing and provisioning data centers with code to define VMs and virtual networks. It reduces complexities of creating virtual objects by allowing administrators to run a script to create them.

**Software-Defined Networking(SDN)** - uses virtualization technologies to route traffic instead of using hardware routers and switches.

**Software-Defined Visibility(SDV)** - refers to the technologies used to view all network traffic.

### **Edge and Fog Computing**
`Edge computing` is the practice of storing and processing data close to the devices that generate and use the data.

`Fog computing` is almost the same thing as edge computing. The primary difference is that fog computing uses a network close to the device and may have multiple nodes sensing and processing data within the fog network.

---

## **Deploying Mobile Devices Securely**

### **Deployment Models**
The following list identifies some common deployment models for mobile devices:
 - Corporate-owned
 - COPE (corporate-owned, personally enabled)
 - BYOD (bring your own device)
 - CYOD (choose your own device)

### **Connection Methods and Receivers**
 - Cellular
 - Wi-Fi
 - Bluetooth
 - NFC (near field communication)
 - RFID
 - Infrared
 - USB
 - Point-to-point
 - Point-to-multipoint
 - Payment methods

---

### **Mobile Device Enforcement and Monitoring**
`Mobile device management(MDM)` includes technologies to manage mobile devices. The goal is to ensure these devices have security controls in place to keep them secure. Some vendors sell `unified endpoint management(UEM)` solutions to manage mobile devices.

MDM concepts:
 - Application management
 - Full device encryption
 - Storage segmentation
 - Content management
 - Containerization
 - Passwords and PINs
 - Biometrics
 - Screen locks
 - Remote wipe
 - Geolocation
 - Geofencing
 - GPS tagging
 - Context-aware authentication
 - Push notifications

#### **Unauthorized Software**
Common terms:
 - `Third-party app stores` - these stores don't undergo the same level of scrutiny as apps on the app store.
 - `Jailbreaking` - refers to removing all software restrictions from an apple device.
 - `Rooting` - the process of modifying an android device to give the user root-level access.
 - `Over-the-air(OTA) updates` - due to the os being installed on flash it is considered firmware, updates to the os often use OTA to keep the device up to date
 - `Custom firmware` - Download custom firmware/os and overwriting the current system
 - `Sideloading` - the process of copying an application package in the `Application Packet Kit(APK)` format to the device and then activating it.

#### **Messaging Services**
 - `Short Message Service(SMS)` - Texting 
 - `Multimedia Messaging Service(MMS)` - Texting w/ media (pictures, videos)
 - `Rich communication services(RCS)` - a newer communication protocol designed to replace SMS for text messaging.

#### **Hardware Control**
MDM can disable features on devices keeping unwanted virus off say, camera, mic, screen.

#### **Unauthorized Connections**
Smartphones support `tethering`, which allows you to share ones devices Internet connection with other devices. As well as `hotspot`, `Wi-Fi Direct`, `carrier unlocking`

---

### **SEAndroid**
The `security-enhanced Android(SEAndroid)` security model uses the `Security-Enhanced Linux(SELinux)` to enforce access security.
 - `Enforcing mode` - This mode enforces SELinux policy. Any activity that is denied by the policy is blocked and logged.
 - `Permissive mode` - This mode does not enforce the SELinux policy, but does log all activity that the policy would block if it was in enforcing mode. Helpful for testing new systems.

---

## **Exploring Embedded Systems**
An `embedded system` is any device that has a dedicated function and uses a computer system to perform that function. Some examples are:
 - Field Programmable Gate Array(FPGA)
 - Arduino
 - Raspberry Pi

### **Understanding Internet of Things**
IoT refers to a wide assortment of technologies that interact with the physical world.

### **ICS and SCADA Systems**
An `industrial control system(ICS)` typically refers to systems within a large facilities such as power plants or water treatment facilities. A `supervisory control and data acquisition(SCADA) system` typically controls an ICS by monitoring it and sending it commands.

Common uses of ICS and SCADA Systems include:
 - `Manufacturing and industrial`
 - `Facilities`
 - `Energy`
 - `Logistics`

### **IoT and Embedded Systems**
Wearables, implants, System on a chip(SOC), real-time operating system(RTOS)

### **Security System Constraints**
A challenge with embedded systems is keeping them up to date with security fixes.

### **Embedded System Constraints**
 - Compute
 - Crypto
 - Power
 - Range
 - Authentication
 - Network
 - Cost
 - Inability to patch
 - Implied trust
 - Weak defaults

### **Communication Considerations**
 - `5G` - 5G can reach peak speeds higher than 4G
 - `Narrow-band` - As the name implies, narrow-band signals have a very narrow frequency range.
 - `Baseband radio` - Baseband radio signal include frequencies that are very near zero. They are typically used when transferring data over cable rather than air.
 - `Subscriber identity module (SIM) cards` - Mobile devices such as smartphones and tablets.
 - `Zigbee` - is a suite of communication protocols used for smaller networks, such as within a home for home automation.