#### Default path for nmap scripts
-/usr/share/nmap/scripts/
#### Finding specific service scripts
- ls -al /usr/share/nmap/scripts/ | grep "http"
#### Some payloads
- nmap -sS -sV -sC -p- -T4 192.224.77.3[default script scan based on service and version it detects]
- nmap --script-help=mongodb-databases [help for specific scripts]
- nmap -sS -sV --script=mongodb-info -p- -T4 192.224.77.3 [run specific scripts]
- nmap -sS -sV --script=mongodb-info,ftp-anon -p- -T4 192.224.77.3 [run multiple scripts at a time]
- nmap -sS -sV --script=ftp-* -p- -T4 192.224.77.3 [run all the ftp scripts using wildcards]
- nmap -sS -A -p- -T4 192.224.77.4 [Aggressive scan]
- nmap -p445 --script smb-enum-users --script-args smbusername=administrator,smbpassword=smbserver_771 demo.ine.local[how to pass agruments in scripts]



