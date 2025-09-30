#### port scanning with auxiliary module
- auxiliary module is used to scanning,discovery,fuzzing,
- auxiliary module can use info gathering,post exploitation also

Suppose  I'm  given a task to pentest a specific target and pivot into internal targets.
#### lab setup
- as a attacker i will first set up my lab
- first I start my metasploit database to keep save everything."service postgresql start".
- Then make sure the database is connect "db_status" in msfconsole.Then create a workspace "workspace -a myworkspace"
#### port-scan
- As I  know the target ip.I will scan the port using auxiliary module. "search portscan"
- then select the exploits " use 5"
- we see the all the options which is required using "show options" command
- set  all the options
- then "run"
This will show the available ports in the target systems
#### Going deeper
- (In this lab) the port is 80 which means it's a web server.We can ensure it by using browser but unfortunately
the lab has no browser.So I use curl "curl ip".In title I found xoda.
- "search xoda" find exploits in metaspoite.
- Again use it like the previous one and get metapreter shell.
- As I am get meterpreter shell that's mean I'm in victim computer.
- In meterpreter session I write "shell" to get better shell. and then write "/bin/bash -i" to get bash shell.
- Using "ifconfig" command in bash shell I find new interface "eth1" which is different ip range.
- Using "ctrl +c" come back to meterpreter shell again
- "run autoroute -s 192.113.124.2(new ip)"
- Make the meterpreter shell in background "background"
- If required we can again back in meterpreter using "sessions" command
- Again we search in msf "search portscan".This time it for new ip (target 2).
- Use a module for new target that is found by the first target. As we add the route we can perfom scan it from my (attacker) machine to victim2 machine via first victim.


