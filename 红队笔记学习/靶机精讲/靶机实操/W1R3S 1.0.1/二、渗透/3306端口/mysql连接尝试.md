```bash
┌──(kali㉿kali)-[~/Desktop/w1r3s]
└─$ mysql -h 192.168.1.9 -u root -p
Enter password: 
ERROR 2002 (HY000): Received error packet before completion of TLS handshake. The authenticity of the following error cannot be verified: 1130 - Host '192.168.1.6' is not allowed to connect to this MySQL server
	意思不是密码错，而是 MySQL 不允许你的 Kali IP（192.168.1.6）远程连接。  
MySQL 的 `root` 用户通常只允许从 `localhost` 登录，也就是只能在靶机本机连。


```