# dns-query-DMitry
---

DMitry 工具是用来查询 IP 或域名 WHOIS 信息的。WHIOS 是用来查询域名是否已经被注册及已经注册域名的详情大的数据库（如域名所有人和域名注册商）。使用该工具可以查询到域名的注册商和过期时间等。

3.1 查看dmitry域名检测工具的使用方法

dmitry

dmitry [-winsepfb] [-t 0-9] [-o %host.txt] host

dmitry域名检测工具-o参数的

-o :导出扫描结果到文档中。

-i ：后跟扫描的目标ip地址。

-w :表示进行whois查询。

-n ：在主机上检索Netcraft.com信息。

-s : 执行搜索可能的子域,子域名检索。

-e ： 执行搜索可能的电子邮件地址。

-p： 在主机上执行TCP端口扫描。

-b：读取从扫描端口接收的banner。

-t： 0-9扫描TCP端口时设置TTL（默认为2）。

dmitry -wnpb baidu.com


