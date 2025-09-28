There are several techniques where os and version detections
- nmap -T4 -sS -sV -p- 192.31.214.3
- nmap -T4 -sS -sV -O -p- 192.31.214.3
- nmap -T4 -sS -sV -O --osscan-guess -p- 192.31.214.3 [guessing os ]
- nmap -T4 -sS -sV --version-intensity 8 -O --osscan-guess -p- 192.31.214.3 [ correctly detect service version]


