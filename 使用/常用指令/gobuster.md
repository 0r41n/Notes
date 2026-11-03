强制扫描工具
扫描网址内文件
实际应用
```bash
gobuster dir -u http://192.168.134.129/~myfiles/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt,zip,rar,bak,sql,log -t 50
```
	-u