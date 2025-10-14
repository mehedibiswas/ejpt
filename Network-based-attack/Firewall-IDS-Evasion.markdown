### Firewall Detection and IDS Evasion
- nmap -Pn -sA -p445,3389 10.4.27.83 [-sA this options shows the port is filtered or not ]
- nmap -Pn -sV -sS -f 10.4.27.83 [ -f option fragments the packets for sending ]
- nmap -Pn -sV -sS -f --mtu 8 10.4.27.83 [ mtu specify maximum bytes it can transfer,in this case it is 8 ]
- nmap -Pn -sS -sV -p445,3389 -f --data-length 200 -D 10.10.23.1,10.10.23.2, 10.4.27.83 [ this will change the source ip from detection --data-length this will use to fix size ]
- nmap -Pn -sS -sV -p445,3389 -f --data-length 200 -g 53 -D 10.10.23.1,10.10.23.2, 10.4.27.83 [ -g flag is used to specify source port so that it can avoid soc utility ]
