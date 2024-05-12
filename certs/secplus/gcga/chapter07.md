# **Protecting Against Advanced Attacks**

## **Understanding Attack Frameworks**

### **Cyber Kill Chain**
Historically `kill chain` has been a military concept related to an attack. It starts with the identification of a target, dispatching resources to the target, someone deciding to attack and giving the order, and it ends with destruction of the target. Military personnel attempt to break an opponents kill chain, such as by disrupting communication methods.

 1. `Reconnaissance`
 2. `Weaponization`
 3. `Delivery`
 4. `Exploitation`
 5. `Installation`
 6. `Command and Control (C2)`
 7. `Actions on Objectives`

### **Diamond Model of Intrusion Analysis**
The `Diamond Model of Intrusion Analysis` focuses on understanding the attackers by analyzing four key components of every intrusion event.

 - `Adversary`
 - `Capabilities`
 - `Infrastructure`
 - `Victim`

### **MITRE ATT&CK**
`MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge)` is a knowledge of tactics and techniques used in real-world attacks. The knowledge base is presented in a matrix or table format.

---

## **Identifying Network Attacks**

### **DoS Versus DDoS**
Dos is one computer, DDoS is multiple difference being attack strength.

### **SYN Flood Attacks**
Sends a ton of SYN/ACK without completing the handshake. Leaves the server with multiple open connections.

### **Spoofing**
spoofs ip, mac, or email

### **On-Path Attacks**
(sometimes called man in the middle attack) is a form of active interception or active eavesdropping.

### **Secure Socket Layer Striping**
Changes HTTPS to HTTP leaving data unencrypted.

### **Layer 2 Attacks**

#### **ARP Poisoning Attacks**
`ARP poisoning` is an attack that misleads computers or switches about the actual MAC address of a system. The MAC address is the physical address, or hardware address, assigned to the NIC. ARP resolves the IP addresses of the systems to their hardware address and stores the result in an area of memory known as ARP cache.

ARP uses two primary messages:
 - `ARP request`
 - `ARP reply`

**ARP On-Path Attacks** - In an ARP on-path attack, an attacker can eavesdrop, redirect network traffic, and, in some cases, insert malicious code.

**ARP DoS Attacks** - An attacker can also use ARP poisoning in Dos attack. For example, an attacker can send an ARP reply with a bogus MAC address for the default gateway. The default gateway is the IP address of a router connection that provides a path out of the network. If all the computers cache a bogus MAC address for the default gateway, none of them can reach it, and it stops all traffic out of the network.

#### **MAC Flooding**
`MAC flooding` is an attack against a switch that attempts to overload it with different MAC addresses associated with each physical port. You typically have only one device connected to any physical port. During normal operation, the switchs internal table store the MAC address associated with this device and maps it to the port. An attacker sends large amounts of traffic with spoofed MAC addresses to the same port in a MAC flooding attack.

#### **MAC Cloning**
MAC cloning is simply changing a systems MAC address

---

### **DNS Attacks**

#### **DNS Poisoning Attacks**
A `DNS poisoning` attack attempts to modify or corrupt DNS data. For example, a successful DNS poisoning attack can modify the IP the IP address associated with *google.com* and replace it with a malicious websites ip address.

#### **Pharming Attacks**
A `pharming attack` is another type of attack that manipulates the DNS name resolution process. It either tries to corrupt the DNS server or the DNS client.

#### **URL Redirection**
`URL redirection` is a common technique used to redirect traffic to a different page within a site.

#### **Domain Hijacking**
In a `domain hijacking` attack, an attacker changes a domain name registration without permission from the owner. Attackers often do so with social engineering techniques to gain unauthorized access to the domain owners email account.

#### **Domain Reputation**
`Domain reputation` helps ISPs determine the likelihood that an email is being sent by a legitimate organization or it is a malicious e-mail. Low rep = ISP may decide to drop the emails.

#### **DNS Sinkhole**
A `DNS sinkhole` is a DNS server that gives incorrect results for one or more domain names.

#### **DNS Log Files**
`DNS log files` record DNS queries, such as each request to resolve a hostname to an IP address. These log entries would include the system that sent the request and the IP address returned for the hostname.

---

### **Replay Attacks and Session Replays**
A `replay attack` is one where an attacker replays data that was already part of a communication session. The attacker first captures data sent over a network between two system. The attacker modifies the data and then tries to impersonate one of the clients in the original session and send modified data in session replays.

---

## **Summarizing Secure Coding Concepts**

### **OWASP**
The `Open Web Application Security Project (OWASP)` is a nonprofit foundation that is focused on improving the security of software.

### **Code Reuse and Dead Code**
`code reuse` saves time and helps prevent the introduction of new bugs. `dead code` is code that is never executed or used.

### **Third-Party Libraries and SDKs**

### **Input Validation**

#### **Client-Side and Server Side Input Validation**

#### **Other Input Validation Techniques**

---

### **Avoiding Race Conditions**
When two or more modules of an application, or two or more applications, attempt to access a resource at the same time, it can cause a conflict known as a `race condition`

Attackers can sometimes exploit `time of check to time of use (TOCTOU)` race condition. This is sometimes called a `state attack`. The attacker tries to race the operating system to do something malicious with ata after the operating system verifies access is allowed (time of check) but before the operating system performs a legitimate action at the time of use.

### **Proper Error Handling**
 - `Errors to the user should be general`
 - `Errors to the devs should be detailed and logged`

### **Code Obfuscation and Camouflage**
`Obfuscation` attempts to make something unclear or difficult to understand.

### **Software Diversity**
Automated software diversity is sometimes used to mimic the use of multiple different core languages. Normally, a compiler converts code written in a programming language into binary executable file.

#### **Outsourced Code Development**
 - Make sure code works as expected
 - Vulnerable code
 - Malicious code
 - Lack of updates

#### **Data Exposure**
Most applications work with data,and it's essential to protect the data. Secure coding techniques take steps to protect data at rest, in transit, and in processing. If it isn't protected it can result in a data breach.

#### **HTTP Headers**
 - `HTTP strict-transport security`
 - `Content-secure-policy`
 - `x-frame-options`

#### **Secure Cookie**
A `secure cookie` is one that has a secure attribute set. This ensures that the cookie is only transmitted over secure channels, such as HTTPS.

#### **Code Signing**
Certificates are used for various purposes, such as encryption and authenticating users and computers. They can also be used to authenticate and validate software code. As an example, devs can purchase a certificate and associate it with an application or code. This code signing process provides a digital signature for the code, and the certificate includes the hash of the code.

---

### **Analyzing and Reviewing Code**
 - Static code analysis
 - Manual code review
 - Dynamic code analysis
 - Sandboxing

### **Software Version Control**

### **Secure Development Environment**
 - Development
 - Test
 - Staging
 - Production
 - Quality Assurance

### **Database Concepts**

#### **Normalization**
`Normalization` of a database refers to organizing the tables and columns to reduce redundant data and improve overall database performance.

#### **SQL Queries**

---

### **Provisioning and Deprovisioning**

### **Integrity Measurement**
refers to how extensively the code was tested.

### **Web Server Logs**

### **Using Scripting and Automation**

---

## **Identifying Malicious Code and Scripts**

### **PowerShell**
look in task mgr for powershell cmdlets

### **Bash**
logs showing sh is being invoked to run scripts

### **Python**
any system reference to .py files

### **Macros**

### **Visual Basic for Applications(VBA)**
if a system acts erratically after opening a file that could be a macros/vba script.

### **OpenSSL**

### **SSH**

---

## **Identifying Application Attacks**

### **Zero-Day Attacks**

### **Memory Vulnerabilities**

#### **Memory Leak**
a bug in a computer app that causes the application to consume more and more memory the longer it runs.

#### **Buffer Overflows and Buffer Overflow Attacks**
A `buffer overflow` occurs when an application receives more input, or different input, than it expects. like inputting 10char into a 9char limit input box and submitting.

#### **Integer Overflow**
same as last but for integer

#### **Pointer/Object Deference**
when you point to a location in memory.

---

### **Other Injection Attacks**

#### **Dynamic Link Library Injection**
DLL injection is changing the working code libraries while the app is running through injection.

#### **Lightweight Directory Access Protocols Injection**
LDAP specifies the formats and methods used to query databases of objects such as users, computers, and other objects within a network. LDAP injection attack is sometimes possible when a application is used to query an LDAP-based database. 

Best way to prevent this is by validating the input before using it.

#### **Extensible Markup Language Injection**
within input boxes xml is input to execute malicious code.

---

### **Directory Traversal**
is a specific type of injection attack that attempts to access a file including the full directory path or traversing the directory structure on a computer.

### **Cross-Site Scripting**
XSS is a web app vulnerability that allows attackers to inject scripts into webpages. the CWE team has included XSS in their annual list of the top 25 most dangerous software weaknesses for several years. it is number 1 on their 2020 list.

 - `reflected xss or non-persistent`
 - `stored xss or persistent`

### **Cross-Site Request Forgery**
modifying the url to execute account commands upon loading.
domain.com/edit?action=set&key=email=attackers@pwn.com

### **Server-Side Request Forgeries**

### **Client-Side Request Forgeries**
using cookies to manipulate server responses

### **Driver Manipulation**
deep understanding attack of drivers and driver code. used to redirect apps to use malicious drivers

### **Artificial Intelligence and Machine Learning**

#### **AI and ML in Cybersecurity**
 - google uses machine learning to block as many as 100million spam emails daily.

#### **Adversarial Artificial Intelligence**
attempts to fool ai by supplying it with deceptive input
 - sign reading ai / but we put stickers on stop signs and confuse the AI

#### **Tainted Data for Machine Learning**


#### **Security of Machine Learning Algorithms**