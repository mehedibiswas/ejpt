### ssh enumerations
ssh(secure shell) is a remote administration protocol that offers encryption and is the successor to Telnet.
- port 22
- ssh authenticatin can be key based or password based
#### lab environment
- service postgresql start [start the metasploit database]
- msfconsole [start metasploit]
- workspace -a ssh-enum [ add a workdspace into metasploit]

#### Procedures
- setg RHOSTS 192.30.120.3 [set global variable for remote host to make the tasks easy]
- search type:auxiliary name:ssh [narrow down the search in metasploit]
- use ssh_version module
- use ssh_login module when user use password or use ssh_login_pubkey when it is key based authentication
ssh_login creates a session.we can see the session using "sessions" command  and we can switch the session "sessions -i 1" using this command.The session is actually a shell.We can switch to bash shell using "/bin/bash -i" .
- we can also enumerate user using "ssh_enumusers" module.


#### metasploit wordlists
- user_name=/usr/share/metaspoit-framework/data/wordlists/common_users.txt
- password=/usr/share/metaspoit-framework/data/wordlists/unix_passwords.txt
