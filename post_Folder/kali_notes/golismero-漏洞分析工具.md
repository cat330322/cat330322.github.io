# golismero-漏洞分析工具

---

一、Golismero是什么？ GoLismero是一款开源的安全测试框架，它是由Python编写的，主要测试对象为WEB网站。该框架采用插件模式，实现用户所需要的功能。GoLismero默认自带了导入、侦测、扫描、攻击、报告、UI六大类插件。通过这些插件，用户可以对目标网站进行DNS检测、服务识别、GEOIP扫描、Robots文件扫描、目录暴力枚举等几十项功能。通过插件方式，GoLismero还可以调用其他工具，如Exploit-DB、PunkSPIDER、Shodan、SpiderFoot、theHarvester。特别需要注意的是，GoLismero的很多插件需要访问外国网站，需要架设梯子才能更好使用！！

二、Golismero主要特征是什么？

 1、能收集、整理多款著名测试程序（例如sqlmap、xsser、openvas、dnsrecon和theharvester）的扫描结果。

 2、整合了CWE、CVE 和OWASP 的数据库。

看不懂，有没有中文翻译的呢？呈现如下： 扫描：对给定目标执行漏洞扫描。也可以从其他工具导入结果并编写报告。后面的参数可能是域名、IP地址或网页。 RESCAN：与扫描相同，但重复先前运行的测试。如果数据库是新的，则此命令与scan相同。 简介：显示可用配置文件列表。此命令不接受任何参数。 插件：显示可用插件的列表。此命令不接受任何参数。 信息：显示给定插件的详细信息。后面的参数是插件ID。您可以使用全局样式的通配符。 报告：写一份早期扫描的报告。此命令不接受任何参数。要指定输出文件，请使用 -o 开关。 进口：从其他工具导入结果并可选地编写报告，但不扫描目标。此命令不接受任何参数。要指定输入文件，请使用-i 切换。  转储：以SQL格式从早期扫描中转储数据库。此命令不接受任何参数。要指定输出文件，请使用 -o 开关。 负载：以SQL格式从早期扫描中加载数据库转储。此命令不接受任何参数。要指定输入文件，请使用 -i 开关。 更新：将golismero更新至最新版本。要求在路径中安装和可用Git。此命令不接受任何参数。 四、Golismero的具体使用举例？ 

1、扫描网站并在屏幕上显示结果 golismero.py scan http://www.toutiao.com 

2、获取nmap结果，扫描找到的所有主机并编写HTML报告 golismero.py scan -i nmap_output.xml -o out.html

3、从OpenVas中获取结果并在屏幕上显示，但不要扫描任何内容： golismero.py import -i openvas_output.xml

