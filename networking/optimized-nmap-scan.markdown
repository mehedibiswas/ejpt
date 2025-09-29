### optimization nmap scan
-timing and perfomance section from nmap help
#### nmap -sS -sV -F --host-timeout 5s 10.10.23.0/24
- it takes only 5 seconds for each hosts to scan
- most 100 used ports[-F] scan only

#### nmap -sS -sV -F --scan-delay 5s 10.10.23.0/24
- differences between each packets is 5 scecond

#### nmap -sS -sV -F -T1 10.10.23.0/24
