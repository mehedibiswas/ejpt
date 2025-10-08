SMB with PsExec
#### SMB
- a network file sharing protocol that is used to facilitate the sharing files and peripherals between computer and networks
- port 445.However smb ranot top of NetBIOS using port 139
- SAMBA is the open source linux implementation of SMB,and allows Windows systems to access Linux shares and devices
- smb uses two level of authentication namely user authentication and share authentication
#### PsExec
- PsExec is a lightweight telnet-replacecement developed by Microsoft that allows you execute processes on remote windows systems using any user's credentials
- PsExec authentication is performed via SMB
- We can use the PsExec utility to authenticate with the target system legitimately and run arbitrary commands or launch a remote command prompt
- It is very similar to RDP, however, instead of controlling the remote system via GUI, commands are sent via CMD.
