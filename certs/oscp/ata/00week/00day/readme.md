### Course Overview 🛰️
- [ ] Bash Scripting  
- [ ] Passive Information Gathering  
- [ ] Active Information Gathering  
- [ ] Vulnerability Scanning  
- [ ] Web Application Attacks  
- [ ] Windows Buffer Overflows  
- [ ] Linux Buffer Overflows  
- [ ] Client-Side Attacks  
- [ ] Locating Public Exploits  
- [ ] Active Directory Attacks  
- [ ] Privilege Escalation  
- [ ] Report writing
### Kali Setup 🐉
**OffSec Lab Machines**
 - [ ] [OpenVPN Installer](https://openvpn.net/client/client-connect-vpn-for-windows/)
	 - [ ] Download `universal.ovpn` from [OffSec Portal](portal.offsec.com)
**Local Kali Setup**
 - [ ] [VMWare Player Installer](https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html.html)
 - [ ] [Kali VM Image](https://www.kali.org/get-kali/#kali-virtual-machines)
	 - [ ] `kali` / `kali`

### Methodology 📜
[MITRE Attack Techniques](https://attack.mitre.org/techniques/T1040/) 
`Attack` -> `Assess` -> `Learn` -> `Exploit` -> `Attack`
**Mitre Attack**
 - Recon
 - Init Access
 - Exec
 - Priv Esc
 - Cred Access
 - Discovery
 - Lateral Move
 - Collection
 - C2
 - Exfil

### Notetaking ✒️
- Admin info 
- Scope
- Targets
- Rules of engagement (ROE)
- Attack paths
- Credentials found or cracked
- Findings
- Vulnerability scans & research
- Service enumeration
- Web info
- [Active directory](https://www.hackthebox.com/blog/introduction-to-active-directory#where_to_start_learning_about_ad_) info
- Open source intelligence ([OSINT](https://www.hackthebox.com/blog/what-is-OSINT))
- Logs
- Activity
- Artifacts
- Cleanup
### Nmap 👁️
- Prep - Configure firewall / `iptables` to be clean for proper tracing `input` / `output`

```sh
sudo iptables -I INPUT 1 -s 192.168.50.149 -j ACCEPT
```

This command adds a rule to the iptables firewall configuration:
1. `sudo`: Execute command with superuser privileges. 
2. `iptables`: Manage Linux kernel firewall rules. 
3. `-I INPUT 1`: Insert rule at the top of the INPUT chain. 
4. `-s 192.168.50.149`: Source IP address the rule applies to. 
5. `-j ACCEPT`: Allow traffic from specified IP address.

- Network Scanning
	- Host Discovery
		- ARP
		- SYN/ACK
	- Service Enumeration
	- DNS
	- TCP/UDP
- Port Scanning
	- SMB
	- SMTP
	- SNMP

```sh
sudo nmap 192.168.179.0/24 -sS -v --reason -T5
```

1. `sudo`: Execute command with elevated privileges. 
2. `nmap`: Network scanning tool for discovering hosts and services. 
3. `192.168.179.0/24`: Target IP range (subnet) to scan. 
4. `-sS`: Perform a TCP SYN scan. 
5. `-v`: Verbose mode for detailed output. 
6. `--reason`: Include the reason for port state in output. 
7. `-T5`: Use aggressive timing template for faster scan.k

```sh
sudo nmap -iL scope.txt -sV -sT -T5 -v --reason -Pn -n -p 22,2222
```

Manual enumeration -> `0recon`

### Challenge Guide 📦
- Recon & Enumeration
- Initial Access
- Discovery
	- Script Results
		- LinPeas
		- WinPeas
- Priv Escalation
	- Service Exploited
	- Vulnerability Type
	- Exploit POC
	- Description
- Loot & Flag
	- Hashes
	- Passwords
	- Proof
	- Flags
	- Etc.
### Resources 📚
 - https://tmuxcheatsheet.com
 - https://www.linkedin.com/learning/topics/nmap