### Getting Started with PWK
In certain cases you are given: a question, a machine, and a flag. Once you have successfully completed the objective, you will receive a flag in the form `OS{random-hash}`. Since flags are dynamically generated at machine boot *be sure to submit the flag before shutting down the instance.*

On Module Exercise VMs that require an SSH connection, they suggest issuing the SSH command as follows:
```sh
ssh -o "UserKnownHostsFile=/dev/null" -o "StrictHostKeyChecking=no" learner@192.168.50.52
```

The `UserKnownHostsFile=/dev/null` and `StrictHostKeyChecking=no` options have been added to prevent the **known-hosts** file on our local Kali machine from being corrupted. 🎉

Setting up our Kali Box will require the following:
- Your Kali Linux VM
- The [OffSec Learning Portal](https://portal.offsec.com)
- A lab containing deployable target machines
- A VPN connection between your Kali VM and the lab
	- Download the `universal.ovpn` from the Learning Portal
		- Run the following `sudo openvpn /Downloads/universal.ovpn`
			- *Ensure no other VPN is running* (I had to turn my host VPN off) 🙃
### How to Approach the Course
Penetration testing and information security in general is fundamentally about *reasoning under uncertainty*. You must widen your scope to look at posture from every angle. 🦐

> - Enumerate 
> - Don't Settle on One Tool
> - Skip Easy Wins
> - Be Specific / Google-Fu
> - Spray Spray Spray
> - Default Credentials
> - Be Flexible / Be Persistent
> - Practice Machines
> - Know What Your Doing
> 	- Tools / GitHub Alts
> 	- Methods
> 	- Documentation
> - Learn Metasploit Suite
> - Try Multiple Tools on Same Lab
> - Grep All Results
> - Work on Your Weakness
> - Revert Slow Machines 
> - Manage Your Time
> 	- Sleep well
> 	- Set time limits
> 	- Take short breaks
> - Nothing Replaces Practice
> - Get the 10% Bonus Points
> - Stay Calm Don't Lose Hope
> - **Don't Give Up** 🚀

### PWK Modules
#### Enumeration 🛰️
One of the most important aspects of penetration testing: information gathering (often called by its synonym *enumeration*). This module is specifically about how to approach a network and detect some common signatures.
#### Web App & Client Side Attacks
There are two primary reasons for starting here:
1. Web vulnerabilities are among the most common attack vectors available to us, since modern web apps usually allow users to submit data to them.
2. Web applications are inherently visual and therefore provide us with a nice interface for understanding why our attacks work in the way that they do.

Intro to web apps begins with covering methodology, toolset, and enumeration frameworks. *Cross-Site Scripting* (XSS) is an excellent vulnerability to start with because it targets the user of a web application as opposed to the server running it.

> Due to the fact that XSS targets users, it can be considered both a web app attack and a client side attack.

We continue into other attack methods such as:
- *Directory Traversal* - provides us with direct server file access
- *File Inclusion* - shows us what can happen when certain configs are not setup properly
- *File Upload Vulns* - demonstrate how we can take advantage of the ability to upload our on files to a web server
- *Command Injection* - allows us to run code of our choice on the web server itself
#### Perimeter Attacks
Being able to *locate public exploits* and *fixing exploits* will help us adapt these tools to our needs. *Antivirus Evasion* isn't itself a perimeter attack, but having some knowledge of how to avoid AV will be helpful since most modern day enterprises do deploy AV solutions. Finally to complete the review of perimeter attacks we will look at analysis of cryptography and *Password Attacks*. Weak or predictable passwords are extremely common in most orgs.
#### Privilege Escalation Attacks
Once access is gained to a machine, we suddenly have a whole set of new actions and activities open to us. We may want to *increase our privileges* on the machine so that we can fully control it, or we might want to use it to gain access to other machines on the network.

*Windows Privilege Escalation* demonstrates how after compromising a Windows target, we can use our new legitimate permissions to become an administrator. We  will learn how to gather information, exploit various types of services, and attack different Windows components.

*Linux Privilege Escalation*
#### Active Directory


#### Challenge Lab Preparation