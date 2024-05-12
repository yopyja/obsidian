# Comparing Threats, Vulnerabilities, and Common Attacks

## Understanding Threat Actors 

 -  `Advanced Persistent Threat (APT)` - is a group of organized threat actors that engage in targeted attacks against organizations.
 -  `State Actors` - APTs that are typically sponsored by nation-states or governments, and usually have targets such as certain companies, organizations, or government agencies.

>Commonly known state actors:
><br/> China: `PLA Unit 61398`, `Buckeye`, & `Double Dragon`
><br/> Iran: `Elfin Team`, `Helix Team`, & `Charming Kitten`
><br/> North Korea: `Ricochet Chollima`, & `Lazarus Group`
><br/> Russia: `Fancy Bear`, `Cozy Bear`, `Voodoo Bear`, & 
`Venomous Bear`

 - `Criminal Syndicates` - are composed of a group of individuals working together in criminal activities. These groups are typically organized within a hierarchy composed of a leader and workers, like a normal business.
 - `Hacker` - was known as someone proficient with computers who wanted to share knowledge with others. The media commonly refers to hackers as malicious individuals who use their technical exp to target individuals, networks, orgs for personal gain.
 - `Script Kiddie` - is an attacker who is uses existing computer scripts or code to launch attacks.
 - `Hacktivist` - launches attacks as part of an activist movement or to further a cause.
 - `Black Hat` - An unauthorized hacker / performs criminal activities.
 - `White Hat` - An authorized hacker / works as within the law.
 - `Grey Hat` - A semi-authorized hacker / may attack or identify weak systems and provide reports.
 - `Insider Threat` - anyone who has legitimate access to an organization's internal resources. 
 - `Competitor` - is any organization engaged in economic or commercial competition with another organization.

### Attack Vectors

 - `Email`
 - `Social Media`

### Shadow IT
`Shadow IT` refers to any unauthorized systems or applications within an organization.

---

## Determining Malware Types
`Malware` includes a wide range of software that has malicious intent. Malware is not software that you would knowingly purchase or download and install. Instead, it is installed onto your system through devious means.

### Viruses
A `virus` is malicious code that attaches itself to a hose application. The host application must be executed to run, and the malicious code executes when the host application is executed. The virus tries to replicate by finding other host applications to infect with malicious code.

Typically the payload of a virus is damaging. It may delete files, cause random reboots, join the computer to a botnet, or enable backdoors that attackers can use to access systems remotely.

### Worms
A `worm` is a self-replicating malware that travels throughout a network without the assistance of a host application or user interaction. A worm resides in memory and can use different transport protocols to travel over the network.

One of the significant problems caused by worms is that they consume network bandwidth. Worms can replicate themselves hundreds of times and spread to all systems in th network.

### Logic Bombs
A `logic bomb` is a string of code embedded into an application or script that will execute in response to an event. The event might be a specific date or time, or a user action such as when a user launches a specific program

### Backdoors
A `backdoor` provides another way of accessing system, similar to how a backdoor in a house provides another method of entry. Malware often installs backdoors on systems to bypass normal authentication methods.

### Trojans
A `trojan` also called a Trojan horse, typically looks like something beneficial, but it's actually something malicious.

Here are the typical steps involved in a `drive-by download`:
 - Attackers compromise a website to gain control of it.
 - Attackers install a trojan embedded into the websites code
 - Attackers attempt to trick users into visiting the site. Sometimes they simply send the link to thousands of users via email, hoping that some of them click the link.
 - When users visit, the website attempts to download the trojan on to the users systems

`Rogueware` / `scareware` - masquerades as free antivirus software, telling the user it found a virus and that they must download and run the "cleaning software" (actually a virus/trojan).

### Remote Access Trojan
A `remote access trojan(rat)` is a type of malware that allows attackers to control systems from remote locations.

### Keyloggers
`Keyloggers` attempt to capture users keystrokes.

### Spyware
`Spyware` is software installed on users systems without their awareness or consent. Its intent is to often monitor the users computer and users activity.

### Rootkit
A `rootkit` is a group of programs that hides the fact that the system has been infected or compromised by malicious code.

### Bots and Botnets
Generically, `bots` are software robots. Bots in a botnet are often called zombies.

### Command and Control
Attackers use `command and control` resources to control infected computers.

### Ransomware and Cryptomalware
`Ransomeware` - Attackers control computers or networks locking the users out.
`Cryptomalware` - Attackers encrypt the data on computers within the network to prevent access.

Both demand a ransom from the target to get their data back.

### Potentially Unwanted Programs
 apps or extensions bundled into installers that may or may not be malicious. either way annoying

### Fileless Virus
Virus that runs in memory. Some attacks from this vector are:
 - `Memory code injection`
 - `Script-based techniques`
 - `Windows registry manipulation`

### Potential Indicators of Malware Attack

 - `Extra traffic`
 - `Data exfiltration`
 - `Encrypted traffic`
 - `Traffic to specific IPs`
 - `Outgoing spam`

---

## Recognizing Common Attacks

### Social Engineering
`Social engineering` is the practice of using social tactics to gain information. It's often low-tech and encourages individuals to do something they wouldn't normally do or cause them to reveal some piece of information, such as user credentials. Some of the individual methods and techniques include:
 - Using flattery and conning
 - Assuming a position of authority
 - Encouraging someone to perform a risky action
 - Encouraging someone to reveal sensitive information
 - Impersonating someone, such as an authorized technician
 - Tailgating or closely following authorized personnel without providing credentials

#### Impersonation
Attempts to impersonate others

#### Shoulder surfing
Simply looking over the shoulder of someone to gain information

#### Tricking Users with Hoaxes
A message often circulated through email, which tells them of impeding doom from a virus. encouraging them to change system files or configurations.

#### Tailgating and Access Control Vestibules
Is the practice of one person following closely behind another without showing credentials.

#### Dumpster Diving
The practice of searching through trash or recycling containers to gain information from discarded documents.

#### Zero-Day Vulnerabilities
A vulnerability or bug that is unknown to trusted sources

#### Watering Hole Attack
Attempts to discover which websites a group of people are likely to visit and then infect those websites with malware that can infect visitors.

#### Typo Squatting
Also called URL hijacking occurs when someone buys a domain name that is close to a legitimate one. Attackers might buy a similar domain for a variety of reasons, including:
 - Hosting a malicious website
 - Earning ad revenue
 - Reselling the domain

#### Eliciting Information
The act of getting information without asking for it directly.
 - `Active listening`
 - `Reflective questioning`
 - `False statements`
 - `Bracketing`

#### Pretexting and Prepending
Both are similar, and some people use the terms interchangeably. The difference being pretext = beginning & prepend = ending.

#### Identity Theft and Identity Fraud
When critical personal information is stolen and fraud is when someone impersonates you.

> Gaslight Girlboss & Influencer Campaigns

#### Invoice Scams
Some criminals use invoice scams trying to trick people or organizations into paying for goods or services that they don't need.

#### Credential Harvesting
the act of collecting usernames and passwords from users.

#### Reconnaissance
Refers to gathering as much information as possible on a target.they typically use open sources to gather information.

#### Influence Campaigns
Use a variety of sources to influence public perception such as hybrid warfare and social media. `Hybrid warfare` is a military strategy that blends conventional warfare with unconventional methods to influence people.

---

### Attacks Via Email and Phone

#### Spam
Unwanted or unsolicited emails.

#### Spam over Instant Messaging
Unwanted or unsolicited messages over instant messaging channels.

#### Phishing
The practice of sending email to users with the purpose of tricking them into revealing personal information or clicking on a link.

Beware of emails from friends
Phishing to install malware
Pishing to validate email addresses
Phishing to get money

#### Spear Phishing
Instead of sending phishing emails to everyone they go to sa specific group of users or even a single user.

#### Whaling
A form of spear phishing that attempts to target high-level executives.

#### Vishing
Voice phishing

#### Smishing
SMS phishing

---

### One Click Lets Them In
It's worth stressing that it only takes one click by an uneducated user to give an attacker almost unlimited access to an organizations network.

---

## Blocking Malware and Other Attacks

### Spam Filters
Filter out only and never filter out legitimate emails

---

### Antivirus and Anti-Malware Software

#### Signature-Based Detection
compares file signatures to a known list of viruses

#### Heuristic-Based Detection
runs questionable code in a sandbox to determine its behavior

#### Cuckoo Sandbox
an open sourced automated software analysis system. 

---

### Why Social Engineering Works

#### Authority

#### Intimidation

#### Consensus

#### Scarcity

#### Urgency

#### Familiarity

#### Trust

---

### Threat Intelligence Sources

