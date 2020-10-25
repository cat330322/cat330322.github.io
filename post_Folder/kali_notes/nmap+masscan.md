# nmap+masscan

---

Nmap

---
nmap -iflist //nmap网卡

nmap -e eth0 192.168.1.30 //指定特定网卡给目标主机发送数据包

nmap -D 192.168.1.33 192.168.1.30 //伪造或者掩盖攻击方主机IP地址进行渗透测试扫描,nmap -D 伪造的IP 目标主机IP

nmap -F -T4 192.168.1.30  快速扫描,-T:时序（1-5）;-F快速扫描;-Pn（端口扫描，不发现主机）

nmap -sS -T4 192.168.1.30 // SYN扫描（-sS）,又称为半开放扫描，SYN扫描不建立完全连接，判断端口状态

nmap -sF 192.168.1.30// FIN扫描（-sF）秘密扫描

nmap -sA 192.168.1.30// ACK扫描（-sA）

nmap -sW 192.168.1.30//  Windows扫描（-sW）

---

常见端口

21 ftp 文件传输协议（FTP）端口；有时被文件服务协议（FSP）使用

22 ssh 安全 Shell（SSH）服务

23 telnet Telnet 服务

25 smtp 简单邮件传输协议（SMTP）

42 nameserver 互联网名称服务

53 domain 域名服务（如 BIND）

80 http 用于万维网（WWW）服务的超文本传输协议（HTTP）

110 pop3 邮局协议版本3

123 ntp 网络时间协议（NTP）

143 imap 互联网消息存取协议（IMAP）

161 snmp 简单网络管理协议（SNMP）

389 ldap 轻型目录存取协议（LDAP）

443 https 安全超文本传输协议（HTTP）

873 rsync rsync 文件传输服务

3306 mysql MySQL 数据库服务

5044 logstash

5601 kibana

9200 elasticsearch

端口状态：

Open（开放的）意味着目标机器上的应用程序正在该端口监听连接 / 报文。

filtered（被过滤的） 意味着防火墙，过滤器或者其它网络障碍阻止了该端口被访问，Nmap 无法得知 它是 open（开放的） 还是 closed（关闭的）。 closed（关闭的） 端口没有应用程序在它上面监听，但是他们随时可能开放。

unfiltered（未被过滤的）当端口对 Nmap 的探测做出响应，但是 Nmap 无法确定它们是关闭还是开放时

open filtered 开放或者被过滤的

closed filtered 关闭或者被过滤的

–top-ports:后跟端口数量，表示扫描多少个常见的端口。

–top-ratio:后跟端口出现的概率，表示扫描在指定概率下出现的端口

nmap 192.168.1.30 //普通扫描

nmap -p 80 192.168.1.30// 指定端口扫描

nmap -p 80,22,8080 192.168.1.30//批量端口扫描

nmap -p 80-135 192.168.1.30 //分割端口号进行批量扫描

nmap -p 1-65535 192.168.1.30 扫描所有端口

UDP（简称U）

TCP（简称T）

-sU ：扫描UDP端口

-sT ：扫描TCP端口

U：后跟UDP端口号

T：后跟TCP端口号

nmap -sU -p U:445 192.168.130

nmap -sT -p T:455 192.168.1.30

nmap -sS -p T:135,U:445 192.168.1.30

nmap --top-ports 10 192.168.1.30 //根据端口的常见性进行扫描

nmap --port-ratio 0 192.168.1.30 //根据端口的出现的概率(0-1)进行扫描 –port-ratio 后跟概率（0-1）

---

nmap脚本 cd /usr/share/nmap/scripts

ls | wc -l //脚本总数

ls | grep 脚本模块名称

ls | grep auth

nmap --script=auth 192.168.1.30 //负责处理鉴权证书（绕开鉴权）的脚本,也可以作为检测部分应用弱口令

nmap --script=default 192.168.1.30或者 nmap -sC 192.168.1.30 //默认的脚本扫描，主要是搜集各种应用服务的信息，收集到后，可再针对具体服务进行攻击

nmap --script external 192.168.1.30 // 利用第三方的数据库或资源，例如进行whois解析，如下图所示。

nmap --script=realvnc-auth-bypass 192.168.1.30  检查vnc bypass

nmap -p3306 --script=mysql-empty-password.nse 192.168.1.30  //Mysql扫描，扫描root空口令

nmap -p3306 --script=mysql-users.nse --script-args=mysqluser=root 192.168.1.30** // Mysql扫描，列出所有mysql用户

nmap --script=broadcast-netbios-master-browser 192.168.1.30//发现网关

---
1、多种多样的参数，丰富的脚本库，满足用户的个人定制需求，其中脚本库还提供了很多强大的功能任你选择

2、强大的可移植性，基本上能在所有的主流系统上运行，而且代码是开源的

3、详细的文档说明，和强大的社区团队进行支持，方面新人上手

主机发现+端口扫描+版本侦测+操作系统侦测+



| **Open**             | **端口开启，数据有到达主机，有程序在端口上监控**             |
| -------------------- | ------------------------------------------------------------ |
| **Closed**           | **端口关闭，数据有到达主机，没有程序在端口上监控**           |
| **Filtered**         | **数据没有到达主机，返回的结果为空，数据被防火墙或者是IDS过滤** |
| **UnFiltered**       | **数据有到达主机，但是不能识别端口的当前状态**               |
| **Open\|Filtered**   | **端口没有返回值，主要发生在UDP、IP、FIN、NULL和Xmas扫描中** |
| **Closed\|Filtered** | **只发生在IP ID idle扫描**                                   |


基本使用：

进行ping扫描，打印出对扫描做出响应的主机,不做进一步测试(如端口扫描或者操作系统探测)：

nmap -sP 192.168.1.0/24

-sn 不扫描端口，只ping主机
-PE 通过ICMP echo判定主机是否存活
-n 不反向解析IP地址到域名
--min-hostgroup 1024 最小分组设置为1024个IP地址，当IP太多时，nmap需要分组，然后串行扫描
--min-parallelism 1024 这个参数非常关键，为了充分利用系统和网络资源，我们将探针的数目限定最小为1024
-oX nmap_output.xml 将结果以XML格式输出，文件名为nmap_output.xml
当需要对较少量量主机进行存活判断时，可以去掉–min-hostgroup 和 --min-parallelism参数来进行扫描。之后对nmap_output.xml用正则表达式进行整理即可得到存活主机及对应ip。

---

fping实战扫描存活主机 命令：fping -a -g 192.168.1.1/24

ettercap进行存活主机 命令：ettercap -G

---

**仅列出指定网络上的每台主机，不发送任何报文到目标主机：

**nmap -sL 192.168.1.0/24

**探测目标主机开放的端口，可以指定一个以逗号分隔的端口列表(如-PS22，23，25，80)：

**nmap -PS 192.168.1.234

**使用UDP ping探测主机：

**nmap -PU 192.168.1.0/24

**使用频率最高的扫描选项：SYN扫描,又称为半开放扫描，它不打开一个完全的TCP连接，执行得很快：

**nmap -sS 192.168.1.0/24

**当SYN扫描不能用时，TCP Connect()扫描就是默认的TCP扫描：

**nmap -sT 192.168.1.0/24

**UDP扫描用-sU选项,UDP扫描发送空的(没有数据)UDP报头到每个目标端口:

**nmap -sU 192.168.1.0/24

**确定目标机支持哪些IP协议 (TCP，ICMP，IGMP等):

**nmap -sO 192.168.1.19

**探测目标主机的操作系统：

**nmap -O 192.168.1.19
nmap -A 192.168.1.19



**nmap官方文档中的例子：

**nmap -v scanme.nmap.org

这个选项扫描主机scanme.nmap.org中 所有的保留TCP端口。选项-v启用细节模式。

nmap -sS -O scanme.nmap.org/24
进行秘密SYN扫描，对象为主机Saznme所在的“C类”网段 的255台主机。同时尝试确定每台工作主机的操作系统类型。因为进行SYN扫描 和操作系统检测，这个扫描需要有根权限。

nmap -sV -p 22，53，110，143，4564 198.116.0-255.1-127
进行主机列举和TCP扫描，对象为B类188.116网段中255个8位子网。这 个测试用于确定系统是否运行了sshd、DNS、imapd或4564端口。如果这些端口 打开，将使用版本检测来确定哪种应用在运行。

nmap -v -iR 100000 -P0 -p 80
随机选择100000台主机扫描是否运行Web服务器(80端口)。由起始阶段 发送探测报文来确定主机是否工作非常浪费时间，而且只需探测主机的一个端口，因 此使用-P0禁止对主机列表。

nmap -P0 -p80 -oX logs/pb-port80scan.xml -oG logs/pb-port80scan.gnmap 216.163.128.20/20
扫描4096个IP地址，查找Web服务器(不ping)，将结果以Grep和XML格式保存。

host -l company.com | cut -d -f 4 | nmap -v -iL -
进行DNS区域传输，以发现company.com中的主机，然后将IP地址提供给 Nmap。上述命令用于GNU/Linux -- 其它系统进行区域传输时有不同的命令。

其他选项：
-p <port ranges> (只扫描指定的端口)

单个端口和用连字符表示的端口范 围(如 1-1023)都可以。当既扫描TCP端口又扫描UDP端口时，可以通过在端口号前加上T: 或者U: 指定协议。 协议限定符一直有效直到指定另一个。 例如，参数 -p U:53，111，137，T:21-25，80，139，8080 将扫描 UDP 端口53，111，和137，同时扫描列出的TCP端口。

-F (快速 (有限的端口) 扫描)

 

**高级使用：**

**获取远程主机的系统类型及开放端口**

nmap -sS -P0 -sV -O <target>

这里的 < target > 可以是单一 IP, 或主机名，或域名，或子网

\1.   -sS TCP SYN 扫描 (又称半开放,或隐身扫描)

\2.   -P0 允许你关闭 ICMP pings.

\3.   -sV 打开系统版本检测

\4.   -O 尝试识别远程操作系统

其它选项:

-A 同时打开操作系统指纹和版本检测
-v 详细输出扫描情况.

nmap -sS -P0 -A -v < target >

 

**列出开放了指定端口的主机列表**

nmap -sT -p 80 -oG – 192.168.1.* | grep open

 

**在网络寻找所有在线主机**

nmap -sP 192.168.0.*

或者也可用以下命令:

nmap -sP 192.168.0.0/24

指定 subnet

 

**Ping 指定范围内的 IP 地址**

nmap -sP 192.168.1.100-254

 

**在某段子网上查找未占用的 IP**

nmap -T4 -sP 192.168.2.0/24 && egrep "00:00:00:00:00:00" /proc/net/arp

 

**在局域网上扫找 Conficker 蠕虫病毒**

nmap -PN -T4 -p139,445 -n -v --script=smb-check-vulns --script-args safe=1 192.168.0.1-254

 

**扫描网络上的恶意接入点 （rogue APs）.**

nmap -A -p1-85,113,443,8080-8100 -T4 --min-hostgroup 50 --max-rtt-timeout 2000 --initial-rtt-timeout 300 --max-retries 3 --host-timeout 20m --max-scan-delay 1000 -oA wapscan 10.0.0.0/8

 

**使用诱饵扫描方法来扫描主机端口**

sudo nmap -sS 192.168.0.10 -D 192.168.0.2

 

**为一个子网列出反向 DNS 记录**

nmap -R -sL 209.85.229.99/27 | awk '{if($3=="not")print"("$2") no PTR";else print$3" is "$2}' | grep '('

 

**显示网络上共有多少台 Linux 及 Win 设备?**

sudo nmap -F -O 192.168.0.1-255 | grep "Running: " > /tmp/os; echo "$(cat /tmp/os | grep Linux | wc -l) Linux device(s)"; echo "$(cat /tmp/os | grep Windows | wc -l) Window(s) device"


1. -iL filename：从文件读取输入。
2. ‐‐exclude filename：在命令行中排除网络。
3. ‐‐excludefile：从文件中排除网络。
4. -S：欺骗源IP。
5. -v interface：详细输出。
6. -vv interface：非常冗长的输出。
7. -e interface：使用指定的接口。
8. -e interface：使用指定的接口。



---


msscan

Masscan 10.11.0.0/16 -p443

Masscan 10.11.0.0/16 -p80,443

Masscan 10.11.0.0/16 -p22-25


快速扫描100个常见端口的B类子网，每秒100,000个数据包

Masscan 10.11.0.0/16 --top-ports 100 -rate 100000



扫描B类子网，但避免在exclude.txt中的

Masscan 10.11.0.0/16 --top-ports 100 --excludefile exclude.txt


Masscan 10.11.0.0/16 --top-ports 100 > results.txt 结果保存

-oX filename：输出到filename的XML。

-oG filename：输出到filename在的grepable格式。

-oJ filename：输出到filename在JSON格式。



扫描web端口的网络

masscan 10.11.0.0/16 -p80,443,8080 - 达 1000000

 扫描十大端口的网络

 masscan 10.11.0.0/16 - top-ten- rate 1000000

 扫描所有端口的网络
masscan 10.11.0.0/16 -p0-65535 - rate 1000000

 扫描一个端口的互联网

masscan 0.0.0.0/0 -p443 - rate 10000000

扫描所有端口的互联网

masscan 0.0.0.0/0 -p0-65535 -rate 10000000
