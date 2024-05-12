### The Practice of Cyber Security
The problem of dealing with an intelligent opponent requires a different approach, discipline, and mindset compared to facing a naturally-occurring or accidental problem. Whether we are simulating an attack or defending against one, we will need to consider the perspective and potential actions of our opponent, and try to anticipate what they might do. Opponents are human beings with *agency*, they can reason, predict, judge, analyze, conjecture, and deliberate.

> Human beings are a *critical* component of cybersecurity.

Another important aspect of security is that it usually involves *reasoning under uncertainty*. The problem of the intelligent adversary and the problem of uncertainty both suggest that understanding cyber security necessitates learning more about how we think as human agents, and how to solve problems. This means we'll need to adopt and nurture specific mindsets that will help us as we learn and apply our skills.

Security is not only about understanding technology and code, but also about your own mind and that of your adversary. We tend to think of a mindset as *a set of beliefs that inform our personal perspective on something*. Two contrasting examples of well-known mindsets are the *fixed* mindset and the *growth* mindset. An individual with a fixed mindset believes that their skill/talent/capacity to learn is what is and that there is no gain to be made by trying to improve. On the other hand, a growth mindset encourages the belief that mental ability is flexible and adaptable, and that one can grow their capacity to learn over time.

Another extremely valuable mindset is the aptly-coined *security mindset*. Proposed by researcher *Bruce Schneier*, this mindset encourages constant questioning of how one can attack (or defend) a system. OffSec encourages learners to adopt the *Try Harder* mindset. To better understand this mindset, let's quickly consider two potential perspectives in a moment of *failure*.

1. If my attack or defense fails, it represents a truth about my current `skills` / `processes` / `configs` / `approach` as much as it is a truth about the system.
2. If my attack or defense fails, this allows me to learn something new, change my approach, and do something differently.
### Threats and Threat Actors
The term *cybersecurity* came to mainstream use from a military origin. For clarity, we'll use cybersecurity to describe the protection of access and information specifically on the internet.

*Risk* the possibility of something happening; because this applies to many domains outside of cybersecurity and information technology. A simple way to define risk is to consider two axes: the *probability* that something negative will occur, and the *impact* on something we value if such an event happens.

| Probability | Impact |
| ----------- | ------ |
| Low         | Low    |
| Low         | High   |
| High        | Low    |
| High        | High   |

As cybersecurity professionals, we should always consider risk by examining the questions:
 - How likely is it that a particular attack might happen?
 - What would be the worst possible outcome if the attack occurs.

*Ransomware* is type of malware that infects computer systems and then locks a legitimate user from accessing it properly. Often, users are contacted by the attacker and asked for a ransom to unlock their machine or documents. 

- *Social engineering* generally exploits vulnerabilities in people.
- *Threat* is something that poses a risk to an asset we care about protecting.
- *Threat Actor* a term signifying agency, motivation, and intelligence.
- *Vulnerability* is a flaw that allows a threat to cause harm.
- *Common Vulnerability Scoring System* (CVSS) used to score vulnerabilities
	- 10.0 Critical
- *Sanitization* is a security measure of checking, cleaning, and filtering data inputs from sources.
	- *Whitelist sanitizing* allows only valid characters and code strings.
	- *Blacklist sanitizing* cleans the input by removing unwelcomed characters.
	- *Escape sanitizing* rejects invalid data request and strips inputs in order to not be seen as codes.
- *Exploits* occur when objectives provide the user with access or privileges that they aren't supposed to have, and when they are pursued deliberately and maliciously.
- *Attack surface* describes all the points of contact on our system or network that could be vulnerable to exploitation.
- *Attack Vector* is a specific vulnerability and exploitation combination that can further a threat actor's objectives.

The most common characters are Alice and Bob. Eve, Mallory, and Trent are also common names, and have fairly well-established "personalities" (or functions). The names often use alliterative mnemonics (for example, Eve, "eavesdropper"; Mallory, "malicious") where different players have different motives. Other names are much less common and more flexible in use. Sometimes the genders are alternated: Alice, Bob, Carol, Dave, Eve, etc.

### CIA Triad
- **Confidentiality**: Can actors who should not have access to the system or information access the system or information?
- **Integrity**: Can the data or the system be modified in some way that is not intended?
- **Availability**: Are the data or the system accessible when and how they are intended to be?

### Security Principles, Controls, and Strategies
Two excellent resources for security principles are David Wheeler's [website](https://dwheeler.com/secure-programs/Secure-Programs-HOWTO/follow-good-principles.html) and the [OWASP cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/Secure_Product_Design_Cheat_Sheet.html#security-principles)

[_The Principle of Least Privilege_](https://en.wikipedia.org/wiki/Principle_of_least_privilege) expresses the idea that each part within a system should only be granted the lowest possible privileges needed to achieve its task. Whether referring to users on a machine or lines of code in a program, correctly adhering to this discipline can greatly narrow the attack surface.

The [_Zero Trust_](https://en.wikipedia.org/wiki/Zero_trust_security_model) security model takes the Principle of Least Privilege and carries it to its ultimate conclusion. This model advocates for removing all implicit trust in networks and has a goal of protecting access to resources, often with granular authorization processes for every resource request.

[_Open Security_](https://en.wikipedia.org/wiki/Open_security), a somewhat counter-intuitive principle, states that the security of a system should not depend on its _secrecy_. In other words, even if an attacker knows exactly how the system's security is implemented, the attacker should still be thwarted.

[_Defense in Depth_](https://en.wikipedia.org/wiki/Defense_in_depth_(computing)) advocates for adding defenses to as many layers of a system as possible, so that if one is bypassed, another may still prevent full infiltration.
#### Security Controls & Strategies
- 24/7 vigilance
- Threat modeling
- Table top discussions
- Continuous training on tactics, processes, and procedures
- Continuous automated patching
- Continuous supply chain verification
- Secure coding and design
- Daily log reviews
- Multiple layers of well-implemented [_Security Controls_](https://csrc.nist.gov/glossary/term/security_control)

*Shamir's Secret Sharing* - Requiring multiple admins to bring their keys together to perform actions.

**Asset Register** is a detailed list compiled of all your business assets.

Conducting these regular table-tops discussions to evaluate different systems and environments is a great way to ensure that all teams know the [_Tactics, Techniques, and Procedures_](https://csrc.nist.gov/glossary/term/tactics_techniques_and_procedures) (TTPs) for handling various scenarios.

Table-top security sessions are part of [_Business Continuity Planning_](https://en.wikipedia.org/wiki/Business_continuity_planning) (BCP). BCP also includes many other aspects such as live drill responses to situations like ransomware and supply-chain compromise.

Utilizing a [_software bill of materials_](https://www.cisa.gov/sbom) (SBOM) as a way to track dependencies automatically in the application build process greatly helps us evaluate supply chain tampering.

The last control we'll explore is [_Chaos Testing_](https://www.ibm.com/garage/method/practices/manage/practice_chaotic_testing/). Chaos testing is a type of BCP or [_disaster recovery_](https://www.vmware.com/topics/glossary/content/disaster-recovery.html) (DR) practice that is often handled via automation. Chaos engineering includes a variety of different approaches, such as having red teams create chaos in the organization to test how well the organization can handle it, scheduling programmed machine shutdowns at various intervals, or having authenticated malicious platform API commands sent in.

### Cyber Laws, Regulations, Standards, Frameworks
The [_Health Insurance Portability and Accountability Act_](https://www.cdc.gov/phlp/publications/topic/hipaa.html) of 1996 (HIPAA) is a United States federal law regulating health care coverage and the privacy of patient health information.

The [_Family Educational Rights and Privacy Act of 1974_](https://studentprivacy.ed.gov/faq/what-ferpa) (FERPA) is a United States federal law regulating the privacy of learners' education records. This [law](https://www.cdc.gov/phlp/publications/topic/ferpa.html) sets limits upon the disclosure and use of these records without parents' or learners' consent.

The [_Gramm-Leach-Bliley Act_](https://www.fdic.gov/resources/bankers/affordable-mortgage-lending-center/glba.html) (GLBA), enacted by the United States Congress in 1999, establishes several requirements that financial institutions must follow to protect consumers' financial information.

The [_General Data Protection Regulation_](https://gdpr.eu/what-is-gdpr/) (GDPR) is a law adopted by the [_European Union_](https://eur-lex.europa.eu/legal-content/EN/LSU/?uri=uriserv:OJ.L_.2016.119.01.0001.01.ENG) in 2016 that regulates data privacy and security.

[**Key disclosure laws**](https://en.wikipedia.org/wiki/Key_disclosure_law) are laws that compel the disclosure of cryptographic keys or passwords under specific conditions. This is typically done as part of a criminal investigation when seeking evidence of a suspected crime.

The [_California Consumer Privacy Act of 2018_](https://oag.ca.gov/privacy/ccpa) (CCPA) is a Californian law granting residents of the state certain privacy rights concerning personal information held by for-profit businesses.

 The [_Payment Card Industry Data Security Standard_](https://docs-prv.pcisecuritystandards.org/PCI%20DSS/Supporting%20Document/PCI_DSS-QRG-v3_2_1.pdf) (PCI DSS) is an information security standard, first published in 2004, for organizations handling customer payment data for several major credit card companies.

The _Center for Internet Security_ (CIS) Critical Security Controls, also known as [_CIS Controls_](https://www.cisecurity.org/controls/cis-controls-list), is a set of 18 (previously 20) recommended controls intended to increase an organization's security posture. `IG1` -> `IG2` -> `IG3`

The _National Institute for Standards and Technology_ (NIST) [_Cybersecurity Framework_](https://www.nist.gov/industry-impacts/cybersecurity-framework) is a collection of standards and practices designed to help organizations understand and reduce cybersecurity risk. The NIST framework consists of three [_components_](https://www.nist.gov/cyberframework/online-learning/components-framework): Core, Implementation Tiers, and Profiles. The Framework Core is a set of cybersecurity activities and outcomes. It is divided into five high-level functions that encompass categories (for example, Asset Management and Risk Assessment).

**ATT&CK** and **D3FEND**: The [MITRE](https://www.mitre.org/) organization has tabulated and organized a framework for cataloging how groups of attackers work together to infiltrate systems and achieve their goals. This framework called the [_MITRE ATT&CK_](https://attack.mitre.org/) framework, is constantly updated to reflect the latest TTPs used by malicious groups across the globe.

**Cyber Kill Chain**: The [_Cyber Kill Chain_](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html) is a methodology developed by Lockheed Martin to help defenders identify and defend against cyber attacks. It outlines seven stages of the attack lifecycle: reconnaissance, weaponization, delivery, exploitation, installation, command and control, and [_actions on objectives_](https://www.crowdstrike.com/cybersecurity-101/cyber-kill-chain/).

The [_Federal Risk and Authorization Management Program_](https://www.fedramp.gov/program-basics/) (FedRAMP) is a [United States program](https://www.gsa.gov/technology/government-it-initiatives/fedramp) that provides a standardized security framework for cloud services used by the federal government.

---

### Careers
#### Attack
**Network Penetration Tester**: A [Network Penetration Tester](https://www.cloudflare.com/learning/security/glossary/what-is-penetration-testing/) is responsible for discovering and exploiting vulnerabilities that exist in a targeted network. 

**Web Application Testers**: A [Web Application Tester](https://www.rapid7.com/fundamentals/web-application-security-testing/) is responsible for testing web applications for security weaknesses. 

**Cloud Penetration Tester**: A [Cloud Penetration Tester](https://www.comptia.org/blog/your-next-move-cloud-penetration-tester) is responsible for performing penetration testing on cloud infrastructure. CLD-100 teaches learners how to test, attack, and exploit cloud technologies.

**Exploit Developer**: An [Exploit Developer](https://www.offsec.com/exp301-osed/) is responsible for discovering and developing exploits for software vulnerabilities. 

**Vulnerability Researcher**: A Vulnerability Researcher is responsible for researching new software vulnerabilities and exploitation techniques, determining their impact, developing Proofs of Concept (PoCs), and communicating their findings to different stakeholders. 

#### Defend
**SOC Analyst**: A [SOC Analyst](https://www.paloaltonetworks.com/cyberpedia/what-is-a-soc) is responsible for monitoring, triaging, and when necessary, escalating security alerts that arise from within monitored networks. 

**Malware Analyst**: A [Malware Analyst](https://www.crowdstrike.com/cybersecurity-101/malware/malware-analysis/) is responsible for analyzing suspected or confirmed malware samples to determine how they work and, ultimately, what their purpose is. 

**Digital Forensics Analyst**: A [Digital Forensics Analyst](https://www.eccouncil.org/cybersecurity-exchange/computer-forensics/what-is-digital-forensic-analyst/) is responsible for investigating Cybersecurity incidents by gathering and analyzing evidence of intrusions and recovering data. 

**Incident Responder**: An [Incident Responder](https://www.techtarget.com/searchsecurity/feature/How-to-become-an-incident-responder-Requirements-and-more) is responsible for reacting to cybersecurity events. This includes identifying the cause and scope of an incident and recommending measures to contain, eliminate, and recover from it.

**Threat Hunter**: A [Threat Hunter](https://en.wikipedia.org/wiki/Cyber_threat_hunting) is responsible for proactively searching networks and systems for Indicators of Compromise (IOCs) using the most up-to-date threat intelligence. 

#### Build
**Cloud Engineer**: A [Cloud Engineer](https://www.techtarget.com/searchcloudcomputing/definition/cloud-engineer) is responsible for building and maintaining the cloud infrastructure. 

**Cloud Architect**: A [Cloud Architect](https://www.techtarget.com/searchcloudcomputing/definition/cloud-architect) is responsible for designing and overseeing the implementation of a cloud-computing strategy aligned with the business's goals and needs.

**Developer**: A [Software Developer](https://en.wikipedia.org/wiki/Programmer) is responsible for writing computer programs which, depending on the precise role, may range from core operating system components to desktop, mobile, and web applications. 

**DevSecOps**: [DevSecOps](https://www.vmware.com/topics/glossary/content/devsecops.html) (an abbreviation for Development, Security, and Operations) is an approach to software development that integrates security into all stages of the software development lifecycle, rather than postponing it to the end. 

**Site Reliability Engineer**: A [Site Reliability Engineer](https://www.redhat.com/en/topics/devops/what-is-sre) is responsible for ensuring and improving the availability and performance of software systems. 

**System Hardener (System Administrator)**: A [System Hardener](https://en.wikipedia.org/wiki/Hardening_(computing)) is responsible for configuring systems to reduce their security risk. 