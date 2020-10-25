# nikto

---

1.普通扫描
nikto -h <IP or hostname>
Nikto能够进行扫描SSL和端口443（HTTPS网站使用的端口）（HTTP默认使用端口80）。因此，我们可以扫描使用了SSL的网站。

nikto -h <IP or hostname> -ssl
其实不必指定443端口使用ssl，nikto首先使用HTTP规则，如果失败，接着尝试HTTPS规则。当然，指定-ssl能省去不必要的步骤，节省扫描时间。
同时，nikto也支持多域名/IP扫描，写入到txt文件中，一行一个。

nikto -h host.txt
2.扫描指定端口
nikto -h xx.xx.xx.xx -p 80       #对80端口的扫描
3.与Metasploit配对扫描
Nikto可以将信息导出为Metasploit在执行扫描时可以读取的格式。只需使用上面的命令来执行扫描，但将-Format msf +附加到它的末尾。该格式可以帮助我们使用漏洞库快速配检索数据。

nikto -h -Format msf+

4.目录猜解
-C 扫描CGI目录

nikto -h 192.168.3.111 -C all     # all表示猜解CGI目录
5.漏洞扫描
-T选项包含的小选项解释：
0 检查文件上传页面
1 检查web日志
2 检查错误配置或默认文件
3 检查信息泄露问题
4 检查XSS/Script/HTML问题
5 从根目录检查是否存在可访问的文件
6 检查拒绝服务问题
7 从任意文件检索是否存在可访问文件
8 检查是否存在系统命令执行漏洞
9 检查SQL注入漏洞
a 检查认证绕过问题
b 识别安装的软件版本
c 检查源代码泄露问题
x 反向链接选项

6.使用指定代理扫描
nikto -h localhost -useproxy
代理在nikto.conf文件中配置，也可以在命令行设置

nikto -h localhost -useproxy http://localhost:8080/
7.查看插件
nikto -list-plugins     #列出可运行的插件
8.选择插件运行
nikto -Plugins
9.更新插件和数据库
nikto -update
10.仅用来发现HTTP和HTTPS端口，而不执行检测规则
nikto -findonly
11.控制nikto的输出显示
nikto -Display 3
1 显示重定向
2 显示收到的cookie
3 显示200/OK响应
4 显示需要认证的URLs
D debug信息
E 所有的HTTP ERROR
P 打印进度到stdout
V verbose output

12.IDS逃避技术
nikto -evasion
常用的参数：
1 随机的URI编码（no-UTF8）
2 Directory self-reference (/./)
3 Premature URL ending
4 Prepend long random string
5 Fake parameter
6 TAB as request spacer
7 Change the case of the URL
8 Use Windows directory separator ()
A Use a carriage return (0x0d) as a request spacer
B Use binary value 0x0b as a request spacer

13.指定检测报告输出文件的格式
nikto -Format <csv/txt/html/msf/xml>   #默认是txt文件格式
