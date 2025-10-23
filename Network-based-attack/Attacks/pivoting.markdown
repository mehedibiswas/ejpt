Read this after reading NetBIOS-SMB  file  
#### To access target2 via target1(compromised target) from attacker machine.
- We need to set pivot point as target1
- we can do that via (run autoroute -s target2_ip) in compromised target1's meterpreter session
- as we set pivot point through meterpreter now metasploit know about the routing path of target2 but our attacker machine don't know about the target2 routing path.
- Now if we want to access the target2 from our attacker machine we need to use auxiliary/server/socks_proxy module of metasploit which will inform our attacker  machine the routing path of target2 via target1.
- We need to configure the uxiliary/server/socks_proxy setting  same as a /etc/proxychains4.conf like rsvrhost,srvport etc.
- proxychains nmap -sT -sV -p 445 -Pn 10.5.17.251 [ run from attacker machine ]
- migrate -N explorer.exe  [ a meterpreter command for migrating to explorer ]
- net view 10.0.28.125 [ a windows command that is used for listing shares ]
- net use D: \\10.0.28.125\Documents [ mapping the remote share to local ]
- after mapping the shares we can access it like local file


#### port forwarding
- after auto route
- find the open ports in target2 using metasploit module
- portfwd add -l 1234 -p 80 -r target2.test.local [ for portforwing ]
- nmap -sV -p 1234 localhost [ use the same command for accessing target2 from our attacking machine ]
#### Resources 
- https://medium.com/@sam_sepiol_/pivoting-deep-into-networks-proxychains-and-metasploit-autoroute-in-action-56339d66e466
