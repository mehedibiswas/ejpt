### SMB Enumeration
Server Message Block is a network file sharing protocol that is used to facilate sharing files and peripherals
between computers on local network.
- ports -139,445
- Samba is name for linux who is same as smb
- Focus of enumeration is smb shares,users,bruteforce attack 

#### lab environments
- service postgresql start
- msfconsole
- workspace -a smb_enum [create a workspace]
- setg RHOSTS 192.91.46.3 [setting a global variable for RHOST]
#### msf auxiliary module
- search smb 
- search smb type:auxiliary name:smb [more advance and specific search]
- first choose version module to detect version and use it,In this case we don't need to set RHOSTS as
   we earlier set it as global variable
- now choose scanner/smb/smb_enumusers for find users for his module it not requires pass or usr file.
   Just run the auxiliary
- now choose scanner/smb/smb_enumshares to find the shares assoicate with user 
- Now it's time to bruteforce a user so choose scanner/smb/smb_login auxiliary,use the auxiliary to find password
#### Access the smb server
- smbclient -L \\\\192.91.46.3\\ -U admin [this will list all the shares]
- smbclient \\\\192.91.46.3\\public -U admin [this will access the share whose name is public]
- get flag.txt [download file into attacker machine]

#### Note
- smbclient is a kali linux tool
- rpcclient [another tool suit for talking to windows]

