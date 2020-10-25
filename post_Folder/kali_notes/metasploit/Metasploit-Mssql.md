# Metasploit-Mssql
---

nmap -sV 192.168.0.101 利用Kali中的“nmap”工具进行信息收集

扫描结果：Port:49156 协议：TCP 服务：ms-sql-s 版本：Server 2008 R2

msfconsole

search mssql_ping

利用检索到的漏洞利用模块

set rhosts 192.168.0.101

run



