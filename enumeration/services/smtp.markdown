smtp Enumeration simple mail transfer protocol
- port 25,465,587
#### Lab environment
- service postgresql start
- msfconsole
- workspace -a smtp-enum
#### Procedures
- setg RHOSTS 192.130.88.2
- porstcan to identify ports for smtp 
- search type:auxiliary name:smtp
- first choose smtp version module
- 2nd choose smtp user enumeration
##### Tools

-  smtp-user-enum

#### Sending mail
- "telnet demo.ine.local 25
HELO attacker.xyz
mail from: admin@attacker.xyz
rcpt to:root@openmailbox.xyz
data
Subject: Hi Root
Hello,
This is a fake mail sent using telnet command.
From,
Admin
.
"
- "sendemail -f admin@attacker.xyz -t root@openmailbox.xyz -s demo.ine.local -u Fakemail -m "Hi root, a fake from admin" -o tls=no"
