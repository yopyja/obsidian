### Penetration Testing Lifecycle
A typical penetration test comprises the following stages:
- Defining the Scope
- Information Gathering
- Vulnerability Detection
- Initial Foothold
- Privilege Escalation 
- Lateral Movement
- Reporting/Analysis
- Lessons Learned/Remediation

The scope of a penetration test engagement defines which IP ranges, hosts, and application should be test, information gathering. 

### Passive Information Gathering

#### WHOIS
`whois` is a TCP service, tool, and type of database that can provide information about a domain name, such as the *name server* and *registrar*. This information is often public since registrars charge a fee for private registration. www.who.is is one of my favorite websites for these types of lookups but it can also be accomplished in the terminal like so! 

```sh
whois megacorpone.com -h 192.168.50.251
```

Providing many details like a phone book of public registrars! It can also be used for private IP's as well. Lets go through the WHOIS boxes now.
```sh
# Box one:
# Question one:
whois megacorpone.com -h xxx.xxx.xxx.xxx | grep 'Name Server: '
# Question two: 
whois megacorpone.com -h xxx.xxx.xxx.xxx | grep 'WHOIS Server: '
# Box two:
whois offensive-security -h xxx.xxx.xxx.xxx | grep 'OS'
# Box three:
whois offensive-security -h xxx.xxx.xxx.xxx | grep 'Tech Email: '
```

#### Google Hacking
The term *Google Hacking* was popularized by Johnny Long in 2001. Through several talks and extremely popular book (*Google Hacking for Penetration Testers*), he outlined how search engines like google could be used to uncover critical information, vulnerabilities, and misconfigured websites.

**Site Operator:**
`site:megacorpone.com`
**Filetype Operator:**
`site:megacorpone.com filetype:txt`
**Extension Operator:**
`site:megacorpone.com ext:txt`
**Exclusion Operator:**
`site:megacorpone.com -filetype:html` 
**Intitle Operator:**
`intitle: "index of" "parent directory"`

For more operators and google-fu knowledge we can utilize the [Google Hacking Database (GHDB)](https://www.exploit-db.com/google-hacking-database) or we can utilize [DorkSearch](https://dorksearch.com) 

#### OSINT
[Netcraft](www.netcraft.com) is an internet service company, based in England, offering a free web portal that performs various info gathering functions such as discovering which technologies are running on a given website and finding which other hosts share the same IP netblock.

[VirusTotal](https://www.virustotal.com) Analyse suspicious files, domains, IPs and URLs to detect malware and other breaches, automatically share them with the security community. 

- GitHub
- GitHub Gist
- GitLab
- SourceForge

You can manually look through commits, branches, code but to speed up checking these repository sites we can use tools like *gitleaks* found on github. 

```
./gitleaks-linux-amd64 -v -r=https://github.com/sillyuser/repository
```

[Shodan](https://www.shodan.io) is a search engine that crawls devices connected to the internet, including the servers that run websites, but also devices like routers and IoT devices. Lets use shodan to search for `hostname:megacorpone.com`. Next we can narrow searches with ports like `hostname:megacorpone.com port:"22"` which will show all SSH servers and if we click on each one we can see details like version and current known vulnerabilities!

[SecurityHeaders](https://securityheaders.com) we can analyze HTTP response headers and provide basic analysis of the target site's security posture. For example our current test site www.megacorpone.com is missing a few common hardening headers such as *Content-Security-Policy* and *X-Frame-Options*. These missing headers are not necessarily vulnerabilities in and of themselves, but they could indicate web developers or server admins that are not familiar with *Server Hardening*. A similar tool is found at www.ssllabs.com/ssltest/ which compares current SSL/TLS configuration to best practices. It will also identify SSL/TLS vulnerabilities, such as *Poodle* or *Heartbleed*.
### Active Information Gathering
This learning unit will cover the following topics:
- Learn to perform Netcat and Nmap port scanning
- Conduct DNS, SMB, SMTP, and SNMP Enumeration
- Understand Living off the Land Techniques (LoL-Bin)

#### DNS Enumeration

The [_Domain Name System_](https://www.cloudflare.com/learning/dns/what-is-dns/) (DNS) is a distributed database responsible for translating user-friendly domain names into IP addresses. It's one of the most critical systems on the internet. This is facilitated by a hierarchical structure that is divided into several zones, starting with the top-level root zone.

Each domain can use different types of DNS records. Some of the most common types of DNS records include:

- **NS**: Nameserver records contain the name of the authoritative servers hosting the DNS records for a domain. Like Name.com 
- **A**: Also known as a host record, the "_a record_" contains the IPv4 address of a hostname (such as www.megacorpone.com).
- **AAAA**: Also known as a quad A host record, the "_aaaa record_" contains the IPv6 address of a hostname (such as www.megacorpone.com).
- **MX**: Mail Exchange records contain the names of the servers responsible for handling email for the domain. A domain can contain multiple MX records. Like Titan Mail.
- **PTR**: Pointer Records are used in reverse lookup zones and can find the records associated with an IP address.
- **CNAME**: Canonical Name Records are used to create aliases for other host records.
- **TXT**: Text records can contain any arbitrary data and be used for various purposes, such as domain ownership verification.

Lets get started:
```sh
# Default will check only A record
host www.pj.dev
# Specify type with the -t {record-type}
host -t mx pj.dev
# Check something that doesn't exist
host idontexist.pj.dev
```

Lets automate this enumeration with a file!
```
pj@kalifornia$ cat list.txt
www
ftp
mail
owa
proxy
router
```

https://github.com/danielmiessler/SecLists
`sudo apt install seclists`

```
for ip in $(cat list.txt); do host $ip.megacorpone.com; done

for ip in $(seq 200 254); do host 51.222.169.$ip; done | grep -v "not found"
```

[_DNSRecon_](https://github.com/darkoperator/dnsrecon) is an advanced DNS enumeration script written in Python. Let's run **dnsrecon** against megacorpone.com, using the **-d** option to specify a domain name and **-t** to specify the type of enumeration to perform (in this case, a standard scan).

```
# -d for domain name
dnsrecon -d megacorpone.com -t std
# Utilize our file from before!
dnsrecon -d megacorpone.com -D ~/list.txt -t brt
# Another good tool
dnsenum megacorpone.com
```

https://lolbas-project.github.io

#### TCP / UDP Port Scanning

It is essential to understand the implications of port scanning, as well as the impact that specific port scans can have. Due to the amount of traffic some scans can generate, along with their intrusive nature, running port scans blindly can have adverse effects on target systems or the client network such as overloading servers and network links or triggering an [_IDS/IPS_](https://www.barracuda.com/support/glossary/intrusion-detection-system). Running the wrong scan could result in downtime for the customer.

The `nc` command, short for netcat, is a versatile networking utility for reading from and writing to network connections using TCP or UDP.

### Command Summary:
```bash
nc -nvv -w 1 -z 192.168.50.152 3388-339
```

This command will perform a verbose port scan on the IP address `192.168.50.152`, checking ports from `3388` to `339` inclusively, with a timeout of `1` second for each port.

##### Flags Used:
- `-n` : This flag suppresses DNS resolution, meaning IP addresses will be displayed rather than domain names.
- `-vv` : This flag increases the verbosity level of the output. In this case, it sets it to a very high level, providing detailed information about the connection attempt.
- `-w 1` : This flag sets a timeout for the connection attempt. In this case, it sets the timeout to 1 second. If the connection is not established within this time, the attempt will be abandoned.
- `-z` : This flag performs a port scanning operation instead of initiating a connection. It checks whether a connection can be established to the specified target (IP address or hostname) on the specified port(s) without actually sending any data.
- `192.168.50.152` : This is the target IP address to which the connection attempt or port scanning operation is directed.
- `3388-339` : This specifies a range of ports to scan. In this case, it will scan ports from 3388 to 339 on the target IP address.

---

```bash
nc -nv -u -z -w 1 192.168.50.149 120-123
```

This command will perform a verbose UDP port scan on the IP address `192.168.50.149`, checking ports from `120` to `123` inclusively, with a timeout of `1` second for each port.

##### Flags Used:
- `-n` : This flag suppresses DNS resolution, displaying IP addresses instead of domain names.
- `-nv` : These flags increase the verbosity level of the output, providing more detailed information about the connection attempt.
- `-u` : This flag specifies the use of UDP (User Datagram Protocol) instead of the default TCP (Transmission Control Protocol). UDP is a connectionless protocol.
- `-z` : This flag instructs `nc` to perform port scanning without initiating any data transmission.
- `-w 1` : This flag sets a timeout for the connection attempt. In this case, it sets the timeout to 1 second. If the connection is not established within this time, the attempt will be abandoned.
- `192.168.50.149` : This is the target IP address for the connection attempt or port scanning operation.
- `120-123` : This specifies a range of ports to scan. In this case, it will scan ports from 120 to 123 on the target IP address.

[_Nmap_](http://nmap.org/) (written by Gordon Lyon, aka Fyodor) is one of the most popular, versatile, and robust port scanners available. It has been actively developed for over two decades and offers numerous features beyond port scanning.







---

## pj notes

