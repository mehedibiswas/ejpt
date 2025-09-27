#### Termology
- A- resolves a hostname or domain to an IPv4 address
- AAAA -resoves a hostname or domain to an IPv6 address
- NS-Reference to the domains nameserver
- MX-Resloves a domain to a mail server
- CNAME- Used for domain aliases
- TXT-Text record
- HINFO- Host information
- SOA- Domain authority
- SRV-Service record
- PTR- Resolves an IP address to a hostname

#### /etc/hosts
This is the file where IP address asign domain name.
#### dns zone transfer
Zone transfer mean transfer the zone files(A,AAAA,NS,MX) to another secondary dns server.
- dnsenum zonetransfer.me [here zonetransfer is the domain name].
- zonetransfer.me is website which shows the process of zone transfer.
#### command
  ##### dig axfr @nsztm1.digi.ninja zonetransfer.me
  - dig -> tool
  - axfr -> Specifies a zone transfer request (AXFR = full zone transfer)
  - @nsztm1.digi.ninja -> The authoritative DNS server you’re querying directly [we can fine it dig NS example.com this command]
  - zonetransfer.me -> The target domain whose zone data you’re trying to transfer.
