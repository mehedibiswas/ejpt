#### Firewall detection 
- -sA [detects filter sending ack ping]
###### nmap -Pn -sA -p445,3389 10.4.27.93
- -Pn [disable host discovery telling the nmap that host is already up don't need to discover]

####  IDS evasion
- nmap -Pn -sS -sV -F -f 10.4.27.93
- nmap -Pn -sS -sV -F -f --mtu 32 10.4.27.93
- nmap -Pn -sS -p445,3389,-f --data-length 200 -D 10.10.23.1,10.10.23.2,10.10.23.4 [here 10.10.23.4 is attacker ip,
  it sends requests as different sources]
- nmap -Pn -sS -p445,3389,-f --data-length 200 -g 53 -D 10.10.23.1,10.10.23.2,10.10.23.4 [ like the previous payloads
   but set a default sources port 53, so that the soc treat it as dns request]
