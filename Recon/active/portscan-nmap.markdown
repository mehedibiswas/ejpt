Different nmap scan techniques
- nmap 192.168.50.52[default scan]
- nmap -Pn 192.168.50.52
- nmap -Pn -p- 192.168.50.52
- nmap -Pn -p80 192.168.50.52
- nmap -Pn -p 80,443,139,145 192.168.50.52
- nmap -Pn -p- 192.168.50.52
- nmap -Pn -F 192.168.50.52 [only 100 ports]
- nmap -Pn -sU 192.168.50.52 [udp scan]
- nmap -Pn -p- -v 192.168.50.52 [verposity]
- nmap -Pn -p- -sV 192.168.50.52 [with service version]
- nmap -Pn -p- -sV -O 192.168.50.52 [operating system]

- nmap -Pn -p- -sV -O  -sC 192.168.50.52 [nmap script]

- nmap -Pn -p- -A 192.168.50.52 [aggressive mode,include os,nmap script,service version]

- nmap -Pn -p- -sV -O 192.168.50.52 -oN nmap-scan.txt [save the nmap scan result as it shows in terminal]

