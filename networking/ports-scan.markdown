port scanning techniques
- nmap -Pn -F 10.4.10.33 [first ports scan for 100 ports]
- nmap -Pn -p80,445,3389 10.4.10.33 
- nmap -Pn -p1-1000 10.4.10.33
- nmap -Pn -p- T4 10.4.10.33
- nmap -Pn -sT 10.4.10.33
- nmap -sU 10.4.10.33 [udp port scan]
