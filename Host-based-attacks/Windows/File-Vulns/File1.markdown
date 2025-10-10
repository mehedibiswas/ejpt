Windows file system vulnerbilities
#### Alternate Data Streams (ADS)
- Alternate Data streams(ADS) is an NTFS (New Technology File sytem) file attribute and was design to provide compatibility wit the MacOS HFS(Hierarcchical File System).
- Any file created on an NTFS formatted drive will have two different forks/streams:
- - Data stream - Default stream that contains the data of the file.
- - Resources stream - Typically contains the metadata of the file.
- Attacker can use ADS to hide malicious code or executables in legitimate files in order to evade detection
- This can be done by storing the malicious code or executables in the file attribute resource stream (metadata) of a legitimate file.
- This technique is usually used to evade basic signature based AVs and static scanning tools.

#### Procedure
- open a c drive
- open cmd in c drive
- notepad test.txt [ this show file is not exit,click yes to create ]
- notepad test.txt:secret.txt [ again create the file like previous ]
- now write any thing for secret file
- notepad test.txt  [ write the content for test.txt file ]
- now take a malicious exe file 
- type payload.exe > windowslog.txt:winpeas.exe
- now we can delete payload.exe and add any random content in windowslog.txt
- start windowslog.txt:winpeas.exe [ this will fail]
- now we make a sybolic link
- now move to C:\Windows\System32
- mklink update.exe C:\Temp\windowslog.txt:winpeas.exe [ this will create a symbolic link,we need administrative privileges to run this,we can run cmd as administrator]
- when we run the update.exe the  winpeas.exe will run automatically
