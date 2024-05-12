# Implementing Controls to Protect Assets

## Comparing Physical Security Controls
A physical security control is something you can physically touch, such as a hardware lock, a fence, an identification badge, and a security camera.

 - Perimeter
 - Buildings
 - Secure work areas
 - Sever rooms
 - Hardware

### Securing Door Access with Cards
It's possible to secure access to areas with proximity cards or smart cards. `Proximity Cards` are small credit card-sized cards that activate when they are close to a proximity card reader.

---

### Comparing Locks

#### Physical Locks
Cheap & better than nothing

#### Physical Cipher Locks
Physical cipher locks often have four or five buttons labeled with numbers. Like ARMS PMO doors.

#### Biometric Locks
Like fingerprint or retina scanners.

#### Cable Locks
Cable locks are great theft deterrent for mobile computers.

---

### Increasing Security with Personnel
`Two-person integrity`

### Monitoring Areas with Cameras
Used for high security areas

### Sensors
 - Motion Detection
 - Noise Detection
 - Temperature
 - Moisture Detection
 - Proximity Reader
 - Cards

### Fencing, Lighting, and Alarms
 - `Fencing` - around the property
 - `Lighting` - Proper lighting ensures good visibility and will deter attackers
 - `Alarms` - provide additional physical security protection.

### Securing Access with Barricades
`bollards` - which are short vertical posts composed of reinforced concrete and/or steel.

### Using Signage
"Authorized Personnel Only" will deter many people from enter a restricted area.

### Drones
`Drones` are small flying vehicles, sometimes called unmanned aerial vehicles (UAVs).

### Asset Management
`Asset management` is the process of tracking valuable assets throughout their life cycles.
 - `Architecture and design weaknesses`
 - `System sprawl and undocumented assets`

### Implementing Diversity
`Defense in depth` (AKA layered security) refers to the security practice of implementing several layers of protection.

`Vendor diversity` - different security controls from different security vendors

`Technology diversity` - using different tech for security 

`Control diversity` - is the use of different security control types, such as technical controls, physical controls, and administrative controls.

---

### Creating Secure Areas

#### Air Gaps
An `air gap` is a physical security control that ensures that a computer or network is physically isolated from another computer or network.

#### Vaults
A `vault` is a large room or large compartment used to store valuables.

#### Faraday Cage
A `Faraday cage` is typically a room that prevents radio frequencies(RF) signals from entering into or emanating beyond a room.

#### Safes
Locking file cabinets or safes used in many offices help prevent the theft of smaller devices.

---

### Hot and Cold Aisles
Help regulate cooling in data centers with multiple rows of cabinets.

---

### Physical Attacks

#### Malicious Universal Serial Bus (USB) Cable
A `malicious Universal Serial Bus(USB)` cable has an embedded Wi-Fi controller capable of receiving commands from nearby wireless devices, such as a smartphone.

#### Malicious Flash Drive
Configured to infect a computer when the drive is plugged in.

#### Card Skimming and Card Cloning
Credit card skimming is the practice of capturing credit card data at the point of sale.

---

### Fire Suppression
 - Remove the heat
 - Remove the oxygen
 - Remove the fuel
 - Disrupt the chain reaction

### Protected Cable Distribution
Physical security includes planning where you route cables and how you route them. Skilled network administrators can cut a twisted-pair cable, attach an RJ-45 to each end and connect them back together in 5min. Same for fiber-optic cable in about 10min time.

---

## Adding Redundancy and Fault Tolerance
`Redundancy` adds duplication to critical system components and networks and provides fault tolerance.

 - Disk redundancies using RAID
 - NIC redundancy with NIC teaming
 - Server redundancies by adding load balancers
 - Power redundancies by adding generators or an UPS
 - Site redundancies by adding hot, cold, warm sites.

### Single Point of Failure
A `single point of failure` is a component within a system that can cause the entire system to fail if the component fails.

 - Disk
 - Server
 - Power
 - Personnel

---

### Disk Redundancies
A `redundant array of inexpensive disks (RAID)` subsystem provides fault tolerance for disks and increases system availability.

#### RAID-0
Doesn't provide any redundancy or fault tolerance. Just means you're spreading files across multiple disks.

#### RAID-1
Mirroring

#### RAID-5 & RAID-6
3 or more disks pared together like RAID-0 but are encoded in a way that if 1 drive goes out the other two can fill in the gaps.

Raid 6 can have 1 more block (4 drives+) and experience up to two drive loses.

#### RAID-10
RAID 1 + 0 combined

#### Disk Multipath
`Multipath input/output` is another fault tolerance method for disks. In simple terms, it uses a separate data transfer path to and from the storage hardware. If one path fails, the second path handles the transfer.

---

### Server Redundancy and High Availability
`High availability` refers to system or service that needs to remain operational with almost zero downtime. It's possible to achieve 99.999 percent uptime, commonly called five nines by implementing redundancy and fault tolerance methods. This equates to less than 6 minutes of downtime a year: 60min * 24hours * 365days * .00001 = 5.256min

#### Active/Active Load Balancers
An `active/active load balancer` can optimize and distribute data loads across multiple computers or networks.

The term `load balancer` makes it sound like it's a piece of hardware, but a load balancer can be hardware or software.

#### Active/Passive Load Balancers
An `active/passive configuration`, one server is active, and the other server is inactive. When the active one goes down, the passive one comes online and takes over.

---

### NIC Teaming
`NIC teaming` allows you to group two or more physical network adapters into a single software-based virtual network adapter. 

This provides increased performance because the NIC team handles all the individual NICs' bandwidth as if the NIC team is a single physical network adapter.

### Power Redundancies
 - `Uninterruptible power supplies`
 - `Dual supply`
 - `Generators`
 - `Managed power distribution units`

---

## Protecting Data with Backups

### Backup Media
 - Disks
 - Network-attached storage (NAS)
 - Storage area network (SAN)
 - Cloud

---

### Online Versus Offline Backups
Cloud vs disk

### Comparing Backup Types
 - Full backup
 - Differential backup
 - Incremental backup
 - Snapshot and image backup

#### Full Backups
EVERYTHING
TIME++
MONEY++

#### Restoring a Full Backup
A full backup is the easiest and quickest to restore. However most organizations need to balance time and money and use either a full/differential or a full/incremental backup strategy.

#### Differential Backups
A `differential` backup strategy starts with a full backup. After the full backup, differential backups back up data that has changed or is different since the last full backup.

#### Order of Restoration for a Full/Differential Backup Set
Assume for the moment that administrators store each of the backups on different tapes. If the system crashes on Wednesday morning, how many tapes would they need to recover the data.

The answer is two. They would first recover the full backup from Sunday. Because the differential backup on Tuesday night includes all the files that changed after the last full backup, they would then restore that tape to restore all the changes up to Tuesday night.

#### Incremental Backups
An `incremental backup` strategy also starts with a full backup. After the full backup, incremental backups then back up data that has changed since the last backup. This includes either the last full backup or the last incremental backup.

#### Order of Restoration for Full/Incremental Backup Set
Assume for a moment that administrators store each of the backups on different tapes. If the system crashes on thursday morning, how many tapes would they need to recover the data?

The answer is four. and they must be done in order (Full > Mon > Tues > Wed)

#### Choosing Full/Incremental or Full/Differential
Full/Incremental - Faster backups
Full/Differential - Quick restoration

#### Snapshot and Image Backups
A `snapshot backup` (aka an `image backup`) captures data at a moment in time. It is commonly used with virtual machines.

#### Copy Backup
Copying to usb drives

#### Testing Backups
 - The test succeeds
 - The test fails

---

### Backups and Geographic Consideration
 - Off-site storages
 - Distance
 - Location Selection
 - Legal implications
 - Data Sovereignty

Disasters and outages can come from many sources, including:
 - Environmental
 - Person-made
 - Internal vs external

---

## Comparing Business Continuity Elements

### Business Impact Analysis Concepts
A `business impact analysis(BIA)` is an important concept of BCP. It helps an organization identify critical systems and components that are essential to the organization's success. These critical systems support `mission-essential functions`. Mission-essential functions are the activities that must continue or be restored quickly after a disaster. The BIA also helps identify vulnerable business processes, which that support mission-essential functions.

It helps them address some of the following questions:
 - What are the critical systems and functions?
 - Are there any dependencies related to these critical systems and functions?
 - What is the maximum downtime limit of these critical systems and functions?
 - What scenarios are most likely to impact these critical systems and functions?
 - What is the potential loss from these scenarios?

#### Site Risk Assessment
Covers qualitative and quantitative risk assessments but for specific sites.

#### Impact
The BIA evaluates various scenarios, such as natural disasters, fires, attacks, power outages, data loss, and hardware and software failures. Additionally, the BIA attempts to identify the impact of these scenarios. When evaluating the impact, BIA looks at multiple items:
 - Will a disaster result in loss of life?
 - Will a disaster result in loss of property?
 - Is there a way to minimize the risk to personnel?
 - WIll a disaster reduce safety for personnel or property?
 - What are the potential financial losses to the organization?
 - What are the potential losses to the organizations reputation?

#### Recovery Time Objective
maximum amount of time it can take to restore a system after an outage.

#### Recovery Point Objective
A `recovery point objective(RPO)` identifies a point in time where data loss is acceptable. 

Imagine a server hosting archived data that has very few changes weekly. Management might decide that some data loss is acceptable, but they always want to recover data from at least the previous week. The RPO is one week.

#### Comparing MTBF & MTTR
Mean time between failures

Mean time to repair

---

### Continuity of Operations Planning

#### Site Resiliency
A `recovery site` is an alternate processing site that an organization uses for `site resiliency`.

Site types:
 - `Hot site` - up 24 hours a day
 - `Cold site` - requires power and connectivity but not much else. just bring the equipment and you're ready to go
 - `warm site` - cold site with some equipment basically as contingency.
 - `mobile site` - outfit a semitrailer (server on wheels)
 - `mirrored site` - two identical hot sites

#### Restoration Order
After the disaster has passed, you will want to return all the functions to the primary site. As a best practice, organizations return the least critical functions to the primary site first.

---

### Disaster Recovery (DRP)
 - Activate the disaster recovery plan
 - Implement contingencies
 - Recover critical systems
 - Test recovered systems
 - After-action report

### Testing Plans with Exercises
 - Walk-throughs
 - A tabletop exercise
 - Simulations
 - Backups
 - Server restoration
 - Server redundancy
 - Site resiliency