```
ftp 10.0.2.6 #连接到ftp

Connected to 10.0.2.6.
220 (vsFTPd 3.0.3)
Name (10.0.2.6:kali): anonymous  #看到可以匿名登录
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 
ftp> ls
229 Entering Extended Passive Mode (|||41106|)
150 Here comes the directory listing.
-rw-r--r--    1 0        0              21 Sep 21  2021 cred.txt
-rw-r--r--    1 0        0              86 Jun 11  2021 welcome
226 Directory send OK.
ftp> cat cred.txt
?Invalid command.
ftp> get cred.txt
local: cred.txt remote: cred.txt
229 Entering Extended Passive Mode (|||11122|)
150 Opening BINARY mode data connection for cred.txt (21 bytes).
100% |*********************************************************************************|    21       39.06 KiB/s    00:00 ETA
226 Transfer complete.
21 bytes received in 00:00 (17.14 KiB/s)
ftp> get welcome
local: welcome remote: welcome
229 Entering Extended Passive Mode (|||22320|)
150 Opening BINARY mode data connection for welcome (86 bytes).
100% |*********************************************************************************|    86      177.93 KiB/s    00:00 ETA
226 Transfer complete.
86 bytes received in 00:00 (125.53 KiB/s)
ftp> exit
221 Goodbye.

```
	