There are several techniques to discover hosts
- host discovery techniques:
- ping sweeps
- ARP Scanning
- TCP SYN Ping(Half-Open Scan)
- udp ping 
- TCP ACK Ping
- SYN-ACK ping
#### Usages
- Ping sweep: ping 10.10.12.72 [not reliable for windows hosts]
- fping 10.10.12.72
- nmap -Pn 10.10.12.72 [useful for windows]
- nmap -sn 10.10.12.72
- nmap -sn 10.10.12.72 10.10.12.75 
- nmap -sn -iL targets.txt [for a list of ips]
- nmap -sn -PS 10.10.12.72 [used for hosts discovery not ports]
- nmap -sn -Pn 10.1.0.8/24 [use this for windows as well others hosts]
