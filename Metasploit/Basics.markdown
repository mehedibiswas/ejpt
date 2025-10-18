#### starting metasploit
- service postgresql start [ start the postgresql ]
-  msfconsole -q [ start the metasploit without banner]
#### Workspace
-  workspace -a mehedi [ create a workspace who's name mehedi]
-  workspace [ listing all available workspace ]
-  workspace mehedi [ switching between workspace ]
-  workspace -d mehedi [ deleting workspace ]
#### nmap
- db_import /root/nmap_result.txt [ importing nmap scan result into metasploit ]
- db_nmap -sS -sV -sC 10.10.12.3 [ run nmap in metasploit ]
#### Database
Interacting with database
- hosts [ list all the hosts ]
- services [ list all the services ]
- vulns [ find  the vulnerability
- creds [ list all the credentials ]
- analyse
#### searching
- search ftp [ general searching in msfconsole]
- search type:auxiliary name:ftp [ narrow down the searching ]
- search type:auxiliary name:ftp platform:windows [more advance search]
#### using module
- use  auxiliary/dos/windows/ftp/xmeasy560_nlst [ use module]
- use 0 [ use module with index ]
- set RHOSTS 10.12.13.22 [ setting variables ]
  

