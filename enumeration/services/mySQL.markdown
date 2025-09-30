### mySQL enumeration
It is an open source relational database management system.
- ports 3306
- auxiliary modules for MySQL,bruteforce,identify passwords,execute SQL queries
#### lab invironment
- service postgresql start
- msfconsole
- workspace -a mysql-enum
#### enumeration procedures
- setq RHOSTS 192.194.172.3 [global remote  hosts setting]
- search type:auxiliary name:mysql [advance search to narrow down result for mysql]
- Use port scan for confirmation port using "scanner/portscan/tcp" module
- Use "scanner/mysql/mysql_version" to find version of mysql
- Use "scanner/mysql/mysql_login" to perform brute force for user and password [use root as username and metaspoit password list for passwrod]
- Use "admin/mysql/mysql_enum" for myqli enumerations its requires credentials which is found by bruteforcing
- Use "admin/mysql/mysql_sql" module, this interact with the database it's requires credentials which can obtain login bruteforce module
- Use "scanner/mysql/mysqli_schemadump" to learn about the schema of the database
#### mysql commands
- mysql -h 192.194.172.3 -u root -p [need passwords]
- show databases;
- use database_name;
- show tables;
  

#### some useful commands for postgresql to show data saved in workspace
- hosts
- services
- loot
- creds
