#osscan-Dmitry

---

深度信息挖掘工具Dmitry使用技巧

一、Dmitry是什么？ DMitry是黑客渗透流程中进行深度信息收集的利器,它是一个由C语言编写的UNIX/(GNU)Linux命令行工具，无GUI操作界面，需掌握其常用使用参数。

二、Dmitry可以用来做什么？

1、进行TCP端口扫描，收集端口相关状态或其他信息 如可探测目标主机上打开的端口、被屏蔽的端口和关闭的端口

2、从Netcraft.com获取主机信息，子域名，域名中包含的邮件地址 注：www.netcraft.com可用来查看站点服务器使用的操作系统信息 3、收集Whois主机IP和域名等信息 值得主要的是，Dmitry还支持将收集的信息保存在一个文件中，方便查看和再利用，很友好！

三、Dmitry支持使用参数有哪些？

四、英文参数看不懂，能否来篇中文解释？安排！ dmitry [-winsepfb] [-t 0-9] [-o %host.txt] host -o 将输出保存到％host.txt或由-o文件指定的文件 -i 对主机的IP地址执行whois查找 -w 对主机的域名执行whois查找 -n 在主机上检索Netcraft.com信息 -s 执行搜索可能的子域 -e 执行搜索可能的电子邮件地址 -p 在主机上执行TCP端口扫描 -f 在显示输出报告过滤端口的主机上执行TCP端口扫描 -b 读取从扫描端口接收的banner -t 0-9扫描TCP端口时设置TTL（默认为2）

五、Dmitry怎么用，能否举个实例? dmitry会创建名为test.out的报告，并进行参数指定的动作扫描 dmitry -iwns -o test.out toutiao.com  更多参数的组合，可以实现不同信息收集效果，留给大家去做尝试！
