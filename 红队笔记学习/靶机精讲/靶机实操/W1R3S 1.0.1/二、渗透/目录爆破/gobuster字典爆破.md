```bash
┌──(kali㉿kali)-[~/Desktop/w1r3s]
└─$ sudo gobuster dir -u http://192.168.1.9 --wordlist=/usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt 
[sudo] password for kali: 
===============================================================
Gobuster v3.8.2
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://192.168.1.9
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.8.2
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
wordpress            (Status: 301) [Size: 314] [--> http://192.168.1.9/wordpress/]                                                                
javascript           (Status: 301) [Size: 315] [--> http://192.168.1.9/javascript/]                                                               
administrator        (Status: 301) [Size: 318] [--> http://192.168.1.9/administrator/]                                                            
server-status        (Status: 403) [Size: 299]
Progress: 220558 / 220558 (100.00%)
===============================================================
Finished
===============================================================

```
wordpress访问不进去，返回localhost
![[Pasted image 20260927075212.png]]

jacascript需要权限
![[Pasted image 20260927075306.png]]
administrator可以访问，但没有后续信息
![[Pasted image 20260927075326.png]]
