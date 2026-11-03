```bash
┌──(kali㉿kali)-[~/Desktop]
└─$ ftp 192.168.1.9
Connected to 192.168.1.9.
220 Welcome to W1R3S.inc FTP service.
Name (192.168.1.9:kali): anonymous#匿名登陆的用户名
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> binary#切换为二进制
ftp> ls
229 Entering Extended Passive Mode (|||47756|)
150 Here comes the directory listing.
drwxr-xr-x    2 ftp      ftp          4096 Jan 23  2018 content
drwxr-xr-x    2 ftp      ftp          4096 Jan 23  2018 docs
drwxr-xr-x    2 ftp      ftp          4096 Jan 28  2018 new-employees
226 Directory send OK.
ftp> cd content
250 Directory successfully changed.
ftp> ls
229 Entering Extended Passive Mode (|||44167|)
150 Here comes the directory listing.
-rw-r--r--    1 ftp      ftp            29 Jan 23  2018 01.txt
-rw-r--r--    1 ftp      ftp           165 Jan 23  2018 02.txt
-rw-r--r--    1 ftp      ftp           582 Jan 23  2018 03.txt
226 Directory send OK.
ftp> pro
progress        prompt          proxy
ftp> prompt#关闭交互式确认
Interactive mode off.
ftp> mget *.txt#批量下载
``` 
