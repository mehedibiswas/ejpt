#### nmap output formats
- -oN save the output a normal text file as the result shown in terminal
- oX xml format,it can exported into metasploit
- oG grepable formmat

#### Exporting nmap scan result into metasploit:
- 1.service postgresql start
- 2.workspace
- 3.workspace -h
- 4.workspace -a pentest_1
- 5.db_import nmap_scan_result.xml
  --->Now we can see the the hosts using "hosts",services using "services" and we can  also run nmap scan using the xml file following by the required flags.

- db_nmap -sS -sV  -p445 10.4.19.132
  --->this save the output into database into the previous imported file if it was in same workspace.


