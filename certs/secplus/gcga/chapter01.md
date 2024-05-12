# Core Security Goals

Core security goals often incorporate the CIA triad 
 - `Confidentiality`
 - `Integrity`
 - `Availability`

## Use Case

A use case describes a goal that an organization wishes to achieve. Common naming strategy for use-case is noun verb format.

---

## Ensure Confidentiality

`Confidentiality` prevents the unauthorized disclosure of data. In short "`auth == access` & `!auth == !access`"

### Encryption 

`Encryption` scrambles data to make it unreadable by unauthorized personnel. Authorized personnel can decrypt the information, while making it extremely difficult for unauthorized to decrypt it.

### Access Controls

`Identification`, `authentication`, and `authorization` provide access controls and help ensure that only authorized personnel can access data.

 - `Identification` - Users claim an identity with a unique username.

 - `Authentication` - Users prove their identity with authentication, such as with a password.

 - `Authorization` - Lastly you grant or restrict access to resources, such as with permissions.

---

## Provide Integrity

`Integrity` provides assurances that data has not changed. This includes ensuring that no one has modified, tampered with, or corrupted the data.

You can use hashing to enforce integrity. Comparing file hashes before and after duplicating/transferring/validating ensures file integrity.

--- 

## Increase Availability

`Availability` indicates that data and services are available when needed. For example our offnet machines in the office run from 0700-1700 everyday 

### Redundancy and Fault Tolerance

`Redundancy` adds duplication to critical systems and provides `fault tolerance`. In other words a system with `fault tolerance` can suffer a fault, but it can tolerate it and continue to operate.

Examples:
 - Disk redundancies
 - Server redundancies
 - Network redundancies
 - Power redundancies

### Scalability and Elasticity

Both `scalability` and `elasticity` contribute to high availability. The primary difference is that static systems are scaled up or out manually, while dynamic systems use elasticity to scale up or out.

 - `Scalability` - adding more ram to ya server (we can only add so much) ⚖️
 - `Elasticity` - dynamically adding more to the server (like resources are infinite) but also removing them when not in use. stretching like a rubber band under heavy usage and returning to normal when not. 💵

### Patching 

Another method for ensuring availability is by keeping them up to date with patches. I'm not elaborating any further... 🤷‍♂️

### Understanding Resiliency

`Resiliency` methods help systems heal themselves or recover from faults with minimal downtimes. 

### Resource vs Security Constraints

Bigger hashes take more power to enc/decry and take up more space on the disk.

---

# Basic Risk Concepts

`Risk` is the possibility or likelihood of a threat exploiting a vulnerability.

`Managerial Controls` - are primarily admin in function. They are typically documented in an organization's security policy and focus on managing risk.

`Operational Controls` - help ensure that the day-to-day operations of an organization comply with the security policy. People implement them.

`Technical Controls` - Use tech such as hardware, software, and firmware to reduce vulnerabilities.

Others included (more self explanatory)
 - Preventive controls
 - Detective controls
 - Deterrent controls
 - Compensating controls
 - Physical controls

---

# Using Command-Line Tools

### Windows Commands
 - `ping`
 - `hping`
 - `ipconfig` and `ifconfig`
 - `netstat`
 - `tracert` and `traceroute`
 - `pathping`
 - `arp`


### Unix Commands
 - `cat`
 - `grep`
 - `head`
 - `tail`
 - `logger`
 - `journalctl`
 - `chmod`

---

# Understanding Logs

  Windows logs
  Network logs
  Centralized logging methods
   - SIEM System
   - Syslog
   - Syslog-ng & Rsylog
   - nxlog
  
  Linux logs