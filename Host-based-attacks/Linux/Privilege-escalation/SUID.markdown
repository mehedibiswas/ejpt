#### SUID 
- In addition to the three main file access permissons (read,write and execute),Linux also provides users with specialized permissions that can be utilize in specific situations.One of these access permissions is the SUID (set owner user id ) permission.
- when applied,this permission provides users with the ability to execute a script or binary with the permissions of the file ownner as opposed to the user that is running the script or binary.
- SUID permissions are typically used to provide unprivileged users with the ability to run specific scripts or binaries with root permissions.It is to be noted,however that the provision of elevate privileges is limited to the execution of the script and does not translate to elevation of privileges,however,if improperly configured unprivileged users can exploit misconfigurations or vulnerabilities within the binary or scriptto obtain an elevated sessions
- This is the function that we will be attempting to exploit in order to elevate our privileges,however ,the success of our attack will depend on the following factors:
- + Owner of the SUID binary - Given that we are attempting to elevate our privileges,we will only be exploiting SUID binaries that are owned by the root user or other privileged users.
- + Access permissions -We will require executable permissions in order to execute the SUID binary.

#### Exploit
- ls -al [ checking all the permissions ]
- here we find two files
- welcome file has the suid set and executable permisions but greetings file don't.
- file welcome [ info about file ]
- strings welcome [ it shows all the strings,here we will see other file ]
- that's mean welcome file execute the greetings file
- rm greetings [ remove the greetings file]
- create a file greetings
- cp /bin/bash greetings [ copy the /bin/bash into greetings ]
- ./welcome [ this will give us root shell]
