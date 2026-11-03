## 产品和工具文档
每个主流安全工具或平台都提供自己的文档，这些文档比任何第三方教程都更可靠、更及时。

当您排查意外行为或试图了解如何以某种方式使用工具时，官方文档应该始终是您的首选，而不是最后才考虑的。

## Linux手册页

你是否曾经遇到过不熟悉的命令行工具或命令？Linux **男人**ual页面为你提供帮助。这些页面就像文档一样，你可以在终端中阅读它们，了解任何命令的相关信息。Linux以及大多数网络安全工具 

要查看手册页，请运行以下命令`man <command>`。例如：
```
user@thm$ man nc 
NC 

NAME 
	nc — arbitrary TCP and UDP connections and listens 
	
SYNOPSIS 
	nc [-46bCDdFhklNnrStUuvZz] [-I length] [-i interval] [-M ttl] [-m minttl] [-O length] [-P proxy_username] [-p source_port] [-q seconds] [-s sourceaddr] [-T keyword] [-V rtable] [-W recvlimit] [-w timeout] [-X proxy_protocol] [-x proxy_address[:port]] [destination] [port]
```