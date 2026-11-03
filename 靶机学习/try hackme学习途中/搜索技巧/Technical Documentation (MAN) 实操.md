## 你需要……

**1.**在工具`nc`（netcat）的手册页中查找相关信息。

**2.**找到允许您打开连接的示例命令`host.example.com on port 42`（**该命令位于**输出的底部）。

3. 复制并粘贴命令以回答以下问题。
```
user@thm:~$ man nc
NC(1)User CommandsNC(1)

## NAME

nc - arbitrary TCP and UDP connections and listens

## SYNOPSIS

nc [-46DdhklnrStUuvz] [-i _interval_] [-p _source_port_] [-s _source_ip_address_]  
[-T _ToS_] [-w _timeout_] [-X _proxy_protocol_] [-x _proxy_address_[:_port_]]  
[_hostname_] [_port_[s]]

## DESCRIPTION

The nc (or netcat) utility is used for just about anything under the sun involving TCP or UDP. It can open TCP connections, send UDP packets, listen on arbitrary TCP and UDP ports, do port scanning, and deal with both IPv4 and IPv6. Unlike telnet(1), nc scripts nicely, and separates error messages onto standard error instead of sending them to standard output, as telnet(1) does with some.

Common uses include:

- ·simple TCP proxies
- ·shell-script based HTTP clients and servers
- ·network daemon testing
- ·a SOCKS or HTTP ProxyCommand for ssh(1)
- ·and much, much more

## OPTIONS

-4

Forces nc to use IPv4 addresses only.

-6

Forces nc to use IPv6 addresses only.

-D

Enable debugging on the socket.

-d

Do not attempt to read from stdin.

-h

Prints out nc help.

-i interval

Specifies a delay time interval between lines of text sent and received. Also causes a delay time between connections to multiple ports.

-k

Forces nc to stay listening for another connection after its current connection is completed. It is an error to use this option without the -l option.

-l

Used to specify that nc should listen for an incoming connection rather than initiate a connection to a remote host. It is an error to use this option in conjunction with the -p, -s, or -z options. Additionally, any timeouts specified with the -w option are ignored.

-n

Do not do any DNS or service lookups on any specified addresses, hostnames or ports.

-p source_port

Specifies the source port nc should use, subject to privilege restrictions and availability.

-r

Specifies that source and/or destination ports should be chosen randomly instead of sequentially within a range or in the order that the system assigns them.

-s source_ip_address

Specifies the IP of the interface which is used to send the packets. For UNIX-domain datagram sockets, specifies the local temporary socket file to create and use so that datagrams can be received. It is an error to use this option in conjunction with the -l option.

-T ToS

Specifies IP Type of Service (ToS) for the connection. Valid values are the tokens "lowdelay", "throughput", "reliability", or an 8-bit hexadecimal value preceded by "0x".

-t

Causes nc to send RFC 854 DON'T and WON'T responses to RFC 854 DO and WILL requests. This makes it possible to use nc to script telnet sessions.

-U

Specifies to use UNIX-domain sockets.

-u

Use UDP instead of the default option of TCP.

-v

Have nc give more verbose output.

-w timeout

If a connection and stdin are idle for more than timeout seconds, then the connection is silently closed. The -w flag has no effect on the -l option, i.e. nc will listen forever for a connection, with or without the -w flag. The default is no timeout.

-X proxy_protocol

Requests that nc should use the specified protocol when talking to the proxy server. Supported protocols are "4" (SOCKS v.4), "5" (SOCKS v.5) and "connect" (HTTPS proxy). If the protocol is not specified, SOCKS version 5 is used.

-x proxy_address[:port]

Requests that nc should connect to hostname using a proxy at proxy_address and port. If port is not specified, the well-known port for the proxy protocol is used (1080 for SOCKS, 3128 for HTTPS).

-z

Specifies that nc should just scan for listening daemons, without sending any data to them. It is an error to use this option in conjunction with the -l option.

## EXAMPLES

Open a TCP connection to port 42 of host.example.com:

$ nc host.example.com 42

Open a UDP connection to port 53 of host.example.com:

$ nc -u host.example.com 53

BSDNC(1)
```

示例命令是什么？
nc host.example.com 42