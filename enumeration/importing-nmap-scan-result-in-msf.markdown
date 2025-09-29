we can use the following command to import a nmap scan result into metasploit.We must save the nmap scan result in xml 
format to export it into metasploit.
- service postgresql start
- msfconsole
- db_status
- workspace
- workspace -a myworkspace
- db_import /path of the nmap scan result
- we can confirm if it imported correctly by using hosts,services,check vulnerability by vulns

- db_nmap -Pn -sV -O 10.4.22.173 [msfconsole command automatically save the scan result in current work space]
