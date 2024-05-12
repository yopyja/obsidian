# Implementing Policies to Mitigate Risks

## Exploring Security Policies

### Personnel Policies
Companies frequently develop policies to define and clarify issues related to personnel. This include personnel behavior, expectations, and possible consequences. Personnel learn these policies when they are hired and as changes occur.

#### Acceptable Use Policy
It often describes the purpose of a computer systems and networks, how users can access them, and the responsibilities of users when they access the systems.

#### Mandatory Vacations
`Mandatory vacation` policies help detect when employees are involved in malicious activity, such as fraud or embezzlement.

#### Separation of Duties
Separation of duties is a principle that prevents any single person or entity from being able to complete all the functions of a critical or sensitive process. It helps prevent fraud, theft, and errors.

#### Least Privilege
The principle of `least privilege` specifies that individuals and processes are granted only the privileges needed to perform assigned tasks or functions, but no more.

#### Job Rotation
`Job rotation` is a concept that has employees rotate through different jobs to learn the processes and procedures in each job. From a security perspective, job rotation helps prevent or expose dangerous shortcuts or even fraudulent activity. Employees might rotate through jobs temp or perm.

#### Clean Desk Space
A `clean desk space` policy directs users to keep their areas organized and free of papers.
 - Keys
 - Cell phones
 - Access cards
 - Sensitive papers
 - Logged-on computer
 - Printouts left in the printer
 - Password on Post-it notes
 - File cabinets left open or unlocked
 - Personal items such as mail with Personally Identifiable Information (PII)

#### Background Check
It's common for organizations to perform background checks on potential employees and even after employees are hired. `Background checks` investigate employees histories to discover anything about them that might make them less-than-ideal for any given job.

#### Onboarding
`Onboarding` is the process of granting individuals access to an orgs computing resources after being hired.

#### Offboarding
`Offboarding` is the process of removing an employees access when they leave the company.

A `non-disclosure agreement(NDA)` is used between two entities to ensure that proprietary data is not disclosed to unauthorized entities.

#### Social Media Analysis
In the context of personnel security policies, social media analysis refers to monitoring employee activity on social media network.

#### Third-Party Risk Management
Organizations interact with entities outside the organization (commonly called third parties) for various reasons, such as purchasing supplies, creating partnerships, and more. These relationships often introduce risks that need to be managed.

A `supply chain` includes all the elements required to produce and sell products and services. In some cases, the supply chain becomes an attack vector.

`Vendor diversity` is often required in policies to grant extra resilience to sed attacks.

`End of Life (EOL)` and `End of Service Life (EOSL)`

`Service Level Agreement(SLA)` - an agreement between a company and a vendor that stipulates performance expectations, such as minimum uptime and maximum downtime.

`Memorandum of understanding(MOU)` - an MOU, sometimes called a `memorandum of agreement(MOA)` expresses and understanding between two or more parties indicating their intention to work together towards a common goal.

`Business Partners Agreement(BPA)` - 

#### Terms of Agreement
A `term of agreement` refers to the period that an agreement shall be in effect.

#### Measurement System Analysis
A `measurement systems analysis(MSA)` evaluates the processes and tools used to make measurements. The MSA uses various methods to identify variations within a measurement process that can result in invalid results.

---

## Incident Response Policies
Many orgs create `incident response policies` to help personnel identify and respond to incidents. A `security incident` is an adverse event or series of events that can negatively affect the confidentiality, integrity, or availability of data or systems within the organization, or that has the potential to do so.

As an example, a `data breach` is a security incident where unauthorized entities access data. Common data breaches occur after an attacker gains access to a network, finds vulnerable systems holding data, and exfiltrates or extracts it.

### Incident Response Plan
An `incident response plan` provides more detail then the incident response policy. It provides organizations with a formal, coordinated plan that personnel can use when responding to an incident.

Some of the common elements included with an incident response plan include:
 - Definitions of incident types
 - Incident response team
 - Roles and responsibilities

#### Communication Plan
A `communication plan` is part of an incident response plan, and it provides direction on how to communicate issues related to an incident. As with all elements of a incident response plan, it's important to create communication plan before the incident. If a plan isn't in place, the wrong people may talk to the media and give the impression that the incident is causing chaos within the organization.

It's common for a communication plan to include the following elements:
 - First responders
 - Internal communication
 - Reporting requirements
 - External communication
 - Law enforcement
 - Customer communication

#### Data Breach Responses
Lawsuits, monetary loss


#### Stakeholder Management
Communication with them is important
don't give too much away but give them what they want.

---

### Incident Response Process
 - Preparation
 - Identification
 - Containment
 - Eradication
 - Recovery
 - Lessons Learned

### Understanding SOAR
A trend in incident response is the use of `Security Orchestration, Automation, and Response (SOAR)` tools to respond to low-level events automatically.

#### Playbooks
A steps document for formal procedures to follow for well-known incidents.

#### Runbooks
Runbooks implement guidelines documented in playbooks for automated services to handle them. like spam filters on emails n such.

---

## Understanding Digital Forensics
Organizations implement digital forensic techniques when collecting information after an incident.

### Key Aspects of Digital Forensics

#### Admissibility of Documentation and Evidence

 - `Tags`
 - Chain of Custody
 - Legal Hold
 - Video
 - Interviews
 - Event Logs
 - Sequence of Events
 - Reports

#### On-Premises Vs. Cloud Concerns

 - right to audit
 - regulatory jurisdiction
 - data breach notification laws

---

### Acquisition and Preservation
When performing data acquisition for digital forensics, it's important to follow specific procedures to ensure that the data is not modified.

#### Order of Volatility
`Order of volatility` refers to the order in which you should collect evidence. Volatile means that it is not permanent.

Most to least volatile:
 - Cache
 - RAM
 - Swap or pagefile
 - Disk
 - Attached
 - Network

#### Data Acquisition

Examples include:
 - Web history
 - Recycle bin
 - Windows error reporting
 - remote desktop protocol (RDP) cache


#### Forensic Tools

Capturing Data
 - dd
 - memdump
 - WinHex
 - FTK imager
 - Autopsy

Verifying Integrity
 - Hashes and checksums
 - Provenance - refers to tracing something back to its origin
 - sha1sum command is used to create and compare hashes

Bandwidth Monitors


#### Electronic Discovery
`eDiscovery` is the identification and collection of electronically stored information. This includes files of any kind, voice mail, social media entries, and website data.

Examples:
 - File - file metadata includes items such as when a files was created who created it, when it was modified, and when it was last accessed.
 - Email
 - Web
 - Mobile - often provides the most metadata information (location, apps, messages, web)

#### Data Recovery
Files that have been deleted can be restored if the user did not properly sanitize the machine.

---

### Strategic Intelligence and Counterintelligence

---

## Protecting Data

### Classifying Data Types

Example:
 - TopSecret
 - Secret
 - Confidential

Sensitive information identifiers used by private companies
 - Public Data
 - Private Data
 - Confidential Data
 - Proprietary Data
 - Financial Information
 - Employee Data
 - Customer Data

### PII and Health Information

PII includes:
 - Full name
 - Birthday and birthplace
 - Medical and health information
 - street or email address information
 - personal characteristics, such as biometric data
 - any type of identification number (SSN or DLN)

### Impact Assessment
An impact assessment helps an organization understand the value of data by considering the impact if it is lost or released to the public.

Data governance refers to the process an organization uses to manage, process, and protect data.

While data quality is a core goal of data governance, many organizations are motivated to implement data governance to comply with external laws and regulation. Some of the regulations that affect risk posture are listed here:
 - HIPAA - health information
 - Gramm-Leach Bliley Act (GLBA) - financial service
 - Sarbane-Oxley Act (SOX) - requires executives within an org take individual responsibility for the accuracy of financial reports
 - General Data Protection Regulation (GDPR) - EU directive mandates the protection of privacy of individuals who live in the EU

GDPR and other laws mandate the use of privacy notices on websites.

### Privacy Enhancing Technologies
Several methods can be used to provide additional privacy protections for data.

 - Data masking  (name: patrick jordan => john pseudo)
 - Anonymization (medical report of patients w/o their pii on it makes it general data)
 - Pseudo-Anonymization (medical reports of patients with random generated info in place of their pii)
 - Tokenization (converts sensitive pii into a hash/token and is able to be changed back)

data retention policy - details how long data should be stored and where

---

### Data Sanitization
 - file shredding -some applications remove all remnants of a file using a shredding technique. they do so by repeatedly overwriting the space where the file is located with 1s and 0s.
 - wiping - a disk wiping writes different patterns of 1s and 0s on a disk
 - erasing and overwriting - ssds use flash memory instead of magnetic storage platters. overwriting is necessary
 - paper shredding - snip snip
 - burning - incinerator
 - pulping - reduces shredded paper to a mash
 - pulverizing - hammer to disk
 - degaussing - magnet drives
 - third party companies - make others do it and blame is shifted

---

## Training Users

### Computer-Based Training

### Phishing Campaigns

### Phishing Simulations

### Gamification

### Capture the Flag

### Role-Based Awareness Training