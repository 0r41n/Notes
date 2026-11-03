目录扫描
```bash
dirsearch -u http://192.168.130.129 --exclude-status 403
```
	`--exclude-status`：意思是排除特定的 HTTP 状态码。
    `403`：在网页服务器里代表 Forbidden（禁止访问）

主要特点
	快速扫描目录
	支持自定义字典，针对特定目标深度扫描
	支持多种请求方式，GET和POST
	支持多线程
	支持根据HTTP响应码(200、400等)过滤和分析结果
	支持JsON、标准输出、CsV等多格式输出
	支持代理
常用命令
	# 使用默认字典进行扫描
	 dirsearch -u http://example.com  
	# 使用自定义字典
	dirsearch -u http://example.com -w /path/to/custom_wordlist.txt  
	# 指定请求方法
	dirsearch -u http://example.com -m POST
	# 输出结果到文件中
	dirsearch -u http://example.com -o output.txt
	# 设置线程数为20
	dirsearch -u http://example.com -t 20
	# 指定只包含什么响应码的结果, -i 只包含 -e 排除
	dirsearch -u http://example.com -t 20 -i 200,403