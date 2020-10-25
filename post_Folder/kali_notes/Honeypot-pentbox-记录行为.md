# Honeypot-pentbox-记录行为
---

蜜罐好比是情报收集系统。蜜罐好像是故意让人攻击的目标，引诱黑客前来攻击。所以攻击者入侵后，你就可以知道他是如何得逞的，随时了解针对服务器发动的最新的攻击和漏洞。还可以通过窃听黑客之间的联系，收集黑客所用的种种工具，并且掌握他们的社交网络。

pentbox下载相应软件

步骤：检索关键字“pentbox 下载”

pentbox-1.8.tar.gz下载完成

解压下载的pentbox压缩包

命令：tar -axvf pentbox-1.8.tar.gz

解压下载的pentbox压缩包后查询相关脚本文件

命令：ls -l

切换到pentbox-1.8文件夹

命令：cd pentbox-1.8

查看pentbox-1.8文件夹中的文件内容

命令：ls

执行pentbox.rb脚本文件

命令:./pentbox.rb


选择网络模块

命令：2

选择蜜罐模块

命令：3

选择自定义设置模块

命令：2

设置端口号，如下图所示

命令：22

入侵命令：hydra -l root -P /usr/share/wordlists/fern-wifi/common.txt ssh://172.18.31.185
