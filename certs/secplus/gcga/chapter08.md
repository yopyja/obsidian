# Using Risk Management Tools

## Understanding Risk Management
`Risk` is the likelihood that a threat will exploit a vulnerability. A `vulnerability` is a weakness, and a `threat` is a potential danger. The result is a negative impact on the organization. Impact refers to the magnitude of harm that can be caused if a threat exploits a vulnerability.

### Threats
 - `Malicious human threats` - 
 - `Accidental human threats` - 
 - `Environmental threats`

A `threat assessment` helps an organization identify and categorize threats. It attempts to predict the threats against an organizations assets, along with the likelihood the threat will occur.

### Risk Types

 - `Internal`
 - `External`
 - `IP theft`
 - `Software compliance/licensing`
 - `Legacy systems and legacy platforms`
 - `Multiparty`

### Vulnerabilities
A `vulnerability` is a flaw or weakness in software, hardware, or a process that a threat could exploit, resulting in a security breach.

 - `Default configurations`
 - `Lack of malware protection or updated definitions`
 - `Improper or weak patch management`
 - `Lack of firewalls`
 - `Lack of organizational policies`

---

### Risk Management Strategies
`Risk management` is the practice of identifying, monitoring, and limiting risks to a manageable level. It doesn't eliminate risks but instead identifies methods to limit or mitigate them.

Some basic terms:
 - `Risk awareness`
 - `Inherent risk`
 - `Residual risk`
 - `Control risk`
 - `Risk appetite`

Risk management strategies:
 - `Avoidance`
 - `Mitigation`
 - `Acceptance`
 - `Transference`
 - `Cybersecurity insurance`

#### Risk Assessment Types
A `risk assessment`, or `risk analysis`, is an important task in risk management. It quantifies or qualifies risks based on different values or judgements. A risk assessment starts by first identifying assets and asset values. 

An `asset` includes any product, system, resource, or process that an organization values, and the `asset value` identifies the worth of the asset to the organization.

A `risk control assessment` (sometimes called a risk and control assessment) examines an organizations known risks and evaluates the effectiveness of in-place controls.

The `risk control self-assessment` is a risk control assessment, but employees perform it.

A `quantitative risk assessment` measures the risk of using a specific monetary amount. The monetary amount makes it easier to prioritize risks.

 - Single loss expectancy (SLE)
 - Annual rate of occurrence (ARO)
 - Annual loss expectancy (ALE)

A `qualitative risk assessment` uses judgement to categorize risk based on the likelihood of occurrence (or probability) and impact. `Impact` is the magnitude of harm resulting from a risk.

The final phase of the risk assessment is the report. This identifies the risks discovered during the assessment and the recommended controls.

#### Risk Analysis
Risk assessments use a variety of techniques to analyze risks. Generically, a `risk analysis` identifies potential issues that could negatively impact an organizations goals and objectives.

  - `Risk register`
  - `Risk matrix`
  - `Heat map`

#### Supply Chain Attacks
A `supply chain` includes all the elements required to produce and sell a product.

---

### Threat Hunting
`Threat hunting` is the process of actively looking for threats within a network before an automated tool detects and reports on the threat.

---

## Comparing Scanning and Testing Tools

### Checking for Vulnerabilities
The overall goal of a vulnerability assessment is to assess the security posture of systems and networks. The identify vulnerabilities or weaknesses within systems. They typically include the following high-level steps:
 - Identify assets and capabilities
 - Prioritize assets based on value
 - Identify vulnerabilities and prioritize them
 - Recommend controls to mitigate serious vulnerabilities

#### Password Cracker
A `password cracker` attempts to discover a password. 
 - Offline password cracker
 - Online password cracker

#### Network Scanners
A `network scanner` uses various techniques to gather information about hosts within a network.
 - Arp ping scan
 - Syn stealth scan
 - Port scan
 - Service scan
 - OS detection

#### Vulnerability Scanning

 - Identify vulnerabilities
 - Identify misconfigurations
 - Passively test security controls
 - Identify lack of security controls

Weak configurations often include:
 -  Open ports and services
 -  Unsecure root accounts
 -  Default account and passwords
 -  Default settings
 -  Unpatched systems
 -  Errors
 -  Open permissions
 -  Unsecure protocols
 -  Weak encryption
 -  Weak passwords
 -  Sensitive data

Analyzing Vulnerability Scan Outputs:
 - A list of hosts that it discovered and scanned
 - A detailed list of applications running on each host
 - A detailed list of open ports and services found on each host
 - A list of vulnerabilities discovered on any of the scanned hosts
 - Recommendations to resolve any of the discovered vulnerabilities

#### Credential Versus Non-Credentialed
Security scans can run with users credentials or no user credentials to show the potential damage that could occur if a threat actor gains access to a internal account.


#### Configuration Review
A `configuration compliance scanner` performs a configuration review of systems to verify that they are configured correctly.

---

### Penetration Testing
`Penetration testing` actively assesses deployed security controls within a system or network.

#### Rules of Engagement
It's important to obtain authorization before beginning any vulnerability or penetration testing. This outlines the `rules of engagement`.

#### Reconnaissance
Penetration testers use a variety of methods for `reconnaissance` (sometimes called `footprinting`). During the reconnaissance phase, the penetration tester (or attacker) attempts to learn as much as possible about a network. Testers use both passive recon and active network recon and discovery when gathering information on targets.

`Passive reconnaissance` collects information about a targeted system, network, or organization using open source intelligence (OSINT).

`Network recon and discovery` methods use tools to send data to systems and analyze the responses.
 - IP scanner
 - Nmap
 - Netcat
 - Scanlless
 - Dnsenum
 - Nessus
 - hping
 - Sn1per
 - Curl

#### Footprinting Versus Fingerprinting
`Network footprinting` provides a big-picture view of a network, including the Internet Protocol (IP) addresses active on a target network

`Fingerprinting` then homes in on individual systems to provide details of each. This is similar to how fingerprints identify an individual.

#### Initial Exploitation
After scanning the target, testers discover vulnerabilities. They then take it a step further and look for a vulnerability that they can exploit.

#### Persistence
`Persistence` is an attackers ability to maintain a presence in a network for weeks, months, or even years without being detected.

#### Lateral Movement
`Lateral movement` refers to the way attackers maneuver throughout a network.

#### Privilege Escalation
When the attacker gains more and more privileges within a network or system.

#### Pivoting
`Pivoting` is the process of using various tools to gain additional information.

#### Known, Unknown, and Partially Known Testing Environments
 - `Unknown`
 - `Known`
 - `Partially known`

#### Cleanup
`Cleanup` is one of the last steps of a penetration test. It includes removing all traces of the penetration tester's activities.

 - Removing any user accounts created on the systems in the network
 - Removing any scripts or applications added or installed on systems
 - Removing any files, such as logs or temporary files, created on systems.
 - Reconfiguring all settings modified by testers during penetration test.

---

### Bug Bounty Programs
A `bug bounty` program provides monetary incentive for security researchers to discover bugs or vulnerabilities.

### Intrusive Versus Non-Intrusive Testing
Intrusive can harm systems

### Exercise Types
 - `red team` - attack
 - `blue team` - defend
 - `purple team` - not a competition but helps both sides learn and grow
 - `white team` - oversees the CTF event

---

## Capturing Network Traffic

### Packet Capture and Replay
You can capture packets using a `protocol analyzer`, which is sometimes called sniffing or using a sniffer.

### Tcpreplay and 
`Tcpreplay` is a suite of utilities used to edit packet captures and send theedited packets over the network.

`Tcpdump` command is a command-line protocol analyzer. It allows you to capture packets like you can with WireShark.

### NetFlow, sFlow, and IPFIX
`NetFlow` is a feature available on many routers and switches that can collect IP traffic statistics and send them to a NetFlow collector.

`sFlow` a sampling protocol. It provides traffic information based on a preconfiguration.

`IP Flow Information Export (IPFIX)` is very similar to Netflow v9 Analysis.

---

## Understanding Frameworks and Standards
A `framework` is a structure used to provide a foundation. Cybersecurity frameworks typically use a structure of basic concepts, and they provide guidance to professionals on how to implement security in various systems.

### Key Framework

The following list show some standards relevant to cybersecurity:
 - ISO 27001
 - ISO 27002
 - ISO 27701
 - ISO 31000

SOC 2 addresses five trust service principles: confidentiality, integrity, availability, security, and privacy. There are two versions of this report:
 - SOC 2 Type I
 - SOC 2 Type II

### Risk Management Framework
The seven steps are:
 - Prepare
 - Categorize information systems
 - Select security controls
 - Implement security controls
 - Assess security controls
 - Authorize information systems
 - Monitor security controls

The Cybersecurity Framework includes three components:
 - Framework core
 - Framework implantation tiers
 - Framework profiles

### Reference Architecture
In cybersecurity, `reference architecture` is a document or set of documents that provides a set of standards.

### Exploitation Framework
 - Metasploit Framework
 - BeEF (Browser Exploitation Framework)
 - w3af (Web Application Attack and Audit Framework)

### Benchmarks and Configuration Guides
In addition to frameworks, you can also use various guides to increase security.