# info_collect

---
nmap -e eth0 192.168.1.30 //指定网卡

nmap -D 192.168.1.33 192.168.1.30 //伪造

nmap --script=default 192.168.1.30 //default

nmap脚本 /usr/share/nmap/scripts 

---

fping -a -g 192.168.1.1/24

---

Masscan 10.11.0.0/16 --top-ports 100 -rate 100000

masscan 0.0.0.0/0 -p0-65535 -rate 10000000

---

nikto -h <IP or hostname>

