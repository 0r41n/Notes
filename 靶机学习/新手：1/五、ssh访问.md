```
┌──(kali㉿kali)-[~/Desktop/vulnhub/downloads]
└─$ ssh wtf@10.0.2.6 -p 55077
```

```
wtf@wtf:~$ id
uid=1000(wtf) gid=1000(wtf) groups=1000(wtf),4(adm),24(cdrom),
```
	看自己是谁以及所在的组、

```
wtf@wtf:~$ sudo -l
[sudo] password for wtf: 
Matching Defaults entries for wtf on wtf:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User wtf may run the following commands on wtf:
    (ALL : ALL) ALL
wtf@wtf:~$ sudo -i
```
	查看当前账户的sudo权限
	-l 查看当前用户的权限
	-i 交互执行
		非交互式相当于指令/交互式相当于对话
	-u 以……用户执行


```
env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin
```
![[Pasted image 20260715044133.png]]

```
User wtf may run the following commands on wtf:
		(ALL : ALL) ALL
```
![[Pasted image 20260715044408.png]]
![[Pasted image 20260715044357.png]]