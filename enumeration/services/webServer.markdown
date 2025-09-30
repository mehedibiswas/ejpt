#### webserver enumeration:
### Lab enivronments
- service postgresql start
- msfconsole
- workspace -a webserver_enum
- setg RHOSTS 192.194.50.3
### msf auxiliary module
- search http
- search type:auxiliary name:http [advance and more specific search to narrow down result]
- First we use /scanner/http/http_version module to see the version
- Secondly we use scanner/http/http_header module
- Thirdly we use "scanner/http/robots_txt",then we use "curl 192.194.50.3/path" which is disallow for search eninge
- Then we use "scanner/http/dir_scanner" for directory listing,then we will analyze the directory using curl tool
- Then we use "scanner/http/files_dir"  moules to lists all the files
- Then we use "scanner/http/apache_userdir_enum"  to find user on the server.
- Then we use "scanner/http/http_login" for bruteforcing password
