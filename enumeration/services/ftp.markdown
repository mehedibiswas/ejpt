#### FTP Enumeration(metasploit)
Focus of ftp enumeration is version and user detection
#### metasploit setup
- service postgresql start
- Add workspace [workspace -a ftp-enum]
#### procedures
- search portscan [to ensure ftp is running]
- set up hosts and every thing requires to  run.
- Now search ftp which produce huge result and minimize result we can use "search type:auxiliary name:ftp" 
##### Version module select
- we select for version type so that using this module we can detect the ftp version and
then search a module for that version.

##### Bruteforce module selects
- metaspoit built wordlists
- user_name=/usr/share/metaspoit-framework/data/wordlists/common_users.txt
- password=/usr/share/metaspoit-framework/data/wordlists/unix_passwords.txt
#### FTP usages (local machine)
- ftp 10.12.23.72 [Try anonymous usrname and blank password first]
- get file.txt [download a file from server to attacker machine]
- put file.txt [uplaod a file attacker machine to server]
