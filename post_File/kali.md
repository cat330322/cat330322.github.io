# kali

---

docker pull kalilinux/kali-rolling

docker run -t -i kalilinux/kali-rolling /bin/bash

aliyun 阿里云 

deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib 

deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib 

ustc 中科大 

deb http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib 

deb-src http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib 

tsinghua 清华

deb http://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free

deb-src http://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free

浙大源

deb http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free

deb-src http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free

apt install hping3

apt-get install metasploit-framework

apt-get install kali-linux-all	

---

ceshi 

1、隐藏身份：VPN，国外代理池、Tor，肉鸡、docker、虚拟机、

2、信息收集：站长查询站点库、、备案站、社工库、谷歌、邮箱、手机、域名、注册信息、robots泄露、Shodan、工具（Nmap、Zmap、Webscan、Hackmall、Sqlmap、msf，whatweb，nikto，w3af，nc）、历史漏洞库exploitdb

3、系统漏洞（Systeminfo、uname -a），web漏洞、数据库漏洞、弱口令burp、

4、社会工程：

5、后渗透metasploit、empire、cobalt strike

6、清理痕迹

---
信息收集

nmap -Ss  -p 80-88 -v 1.1.1.1	扫描端口

nmap -sS 10.x.x.x //usually

nmap -A -O -sV -p 443  --script=vuln 10.x.x.x //vuln

Masscan 10.11.0.0/16 –top-ports 100 > results.txt

fping -a -g 192.168.169.0/24

hping3 172.28.1.1 -S -V -c 100 -p 80


