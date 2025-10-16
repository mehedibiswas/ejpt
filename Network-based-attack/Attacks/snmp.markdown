#### snmp enumeration
- snmp (Simple Network Management Protocol) is a widely used protocol for monitoring and managing networked devices,such as router switches,printer,servers and more.
- It allows network administrators to query devices for status information,configure certain setting,and receive alerts or trap when specific events occur.

- SNMP is an application layer protocol that typically uses UDP for transport.It involves three primary components
 + SNMP Manager: The system responisble for quering and interacting with SNMP agents on network devices.
 + SNMP Agent: Software running on network devices that responds to SNMP queries and send traps.
 + Management Information Base (MIB): A hierarchical database  that defines the structure of data available through SNMP.Each piece of data has a unique Object Identifier (OID).
 - Versions of SNMP: 
  + SNMPv1: The earliest version,using community strings (essentially passwords ) for authentication.
  + SNMPv2c: An improved version with support for bulk transfer but still relying on community strings for authentication
  + SNMPv3:Introduced security features,including encryption message integrity,and user-based authentication
 - Ports:
  + port 161(udp): used for snmp queries
  + port 162(udp): used for snmp traps (notifications).
  
  
  #### Snmp enumeration
  - identify snmp-enable devices: Determine which devices on hte network have snmp enabled and whether they are vulnerable to information leakage or attacks.
  - Extract System Information: Collect system-related data like device names,operating systems,software versions,network interfaces and more.
  - Identify SNMP Community Strings: Test for default or weak community strings,which can grant unauthorized access to device information.
  - Retrieve Network Configurations: Gather information about routing tables,network interfaces,IP addresses and other network-specific details.
  - Collect user and group informaion: In some cases,SNMP can reveal user account information and access permissions.
  - Identiy Services and Applications:Find out which services and applications are running on the target devices,potentially leading to futher attack vectors.
  
#### lab
- nmap -sU -p 161 demo.ine.local
- nmap -sU  -sV -p  161 --script=snmp-brute demo.ine.local  [ this will give us community strings ]
- snmpwalk -v 1 -c public demo.ine.local [ this give us tedious and huge result ]
- nmap -sU -p 161 --script snmp-* demo.ine.local >snmp_info [this run all the snmp script and save the result as snmp_info file ]
- hydra -l administrator -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt demo.ine.local smb
