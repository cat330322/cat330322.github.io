# webscan-dirsearch 

---
dirsearch是一个基于python的命令行工具，旨在暴力扫描页面结构，包括网页中的目录和文件。

网站敏感信息包括如下：

后台目录：弱口令，万能密码，爆破

安装包：获取数据库信息，甚至是网站源码

上传目录：截断、上传图片马等

mysql管理接口：弱口令、爆破，万能密码，然后脱裤，甚至是拿到shell

安装页面 ：可以二次安装进而绕过

phpinfo：会把你配置的各种信息暴露出来

编辑器：fck、ke、等

iis短文件利用：条件比较苛刻 windows、apache等

提到了网站敏感目录我们就不得不提 robots.txt 文件了

robots.txt 文件是专门针对搜索引擎机器人robot 编写的一个纯文本文件。我们可以在这个文件中指定网站中不想被robot访问的目录。这样，我们网站的部分或全部内容就可以不被搜索引擎收录了，或者让搜索引擎只收录指定的内容。因此我们可以利用robots.txt让Google的机器人访问不了我们网站上的重要文件，GoogleHack的威胁也就不存在了。


git clone https://github.com/maurosoria/dirsearch

ls -l  查看python脚本文件（dirsearch.py），

用dirsearch.py脚本对3.1提供的测试网站进行测试，

python3 dirsearch.py -u testphp.vulnweb.com -e *

---

-h, --help 查看帮助-u URL, 

--url=URL 设置url-L URLLIST, 

--url-list=URLLIST 设置url列表

-e EXTENSIONS, --extensions=EXTENSIONS 网站脚本类型

-w WORDLIST,

 --wordlist=WORDLIST 设置字典

-l, --lowercase 小写

-f, --force-extensions 强制扩展字典里的每个词条

-s DELAY, --delay=DELAY 设置请求之间的延时

-r, --recursive Bruteforce recursively 递归地扫描

---

 irsearch.py敏感文件扫描结果保存目录，目录：/root/dirsearch/reboots/

查看方法：复制URl到物理机浏览器
直接选择URl在kali 浏览器打开。
