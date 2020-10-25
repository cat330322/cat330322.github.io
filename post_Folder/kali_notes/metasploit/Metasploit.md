#Metasploit

---

查找exploit：

search cve:2009 type:exploit app:client

---

show exploits  列出所有渗透攻击模块

show payloads  攻击载荷

show auxiliary 辅助攻击载荷

search name 查找攻击和其他模块

info 展示相关信息

use name 装载一个模块

set LHOST 反弹shell的地址

set RHOST 远程主机或目标主机

show options 列出模块参数

show targets 列出目标平台

set target num 目标操作系统及补丁

set payload name 指定攻击载荷

show advanced 列出所有高级配置

set autorunscript migrate -f 渗透攻击后，自动迁移另一个进程

check 检车目标是否选定渗透攻击存在相应安全漏洞

expolit 执行

exploit -j 后台执行

session -l 列出可用的交互会话

session -i number 选定会话

---

about usebase

msfconsole

search ms08-067

use 模块

show payloads

set payload 载荷

show options

set RHOST + 目标地址

set LHOST + 本地地址

show targets

set target + 序列

run


---

msfconsole基本命令

back（返回）：从目前的情况下向后移动

banner：Display an awesome metasploit banner

Cd:改变当前的工作目录

Color:切换颜色

connect（远程连接）：与主机通信

edit（编辑）：编辑与$ VISUAL或$ EDITOR当前模块的

exit（退出命令行）：退出控制台

get （获取变量）：获取特定上下文变量的值

getg （全局获取变量）：获取一个全局变量的值

go_pro ：启动Metasploit的网页图形用户界面

grep： grep的另一个命令的输出

help（帮助） ：帮助菜单

info（获取模块信息）：关于一个或多个模块显示信息

irb：进入irb脚本模式

jobs：显示和管理职位

kill（结束进程）：结束一个进程

load（加载）：加载一个框架插件

loadpath ：搜索和负载从一个路径模块

makerc：保存自开始进入到一个文件中的命令

popm：弹出最新的模块从堆栈中并使其活跃

previous ：将以前加载模块作为当前模块

pushm ：推主动或模块列表在模块栈

quit （退出控制台）:退出控制台

reload_all Reloads :从所有定义的模块路径的所有模块

rename_job :重命名工作

resource :运行存储命令在文件

route：通过会话路由流量

save：将数据存储主动

search（搜索exp等模块关键字）：搜索模块的名称和说明

sessions（会话功能）：转储会话列表和显示有关会话的信息

set（设置参数）：设置一个特定的上下文变量的值

setg（全局设置参数）：设置一个全局变量的值

show（展示参数模块）：给定类型的显示模块或所有模块

sleep ：什么都不做对的指定秒数

spool ：写控制台输出到一个文件以及屏幕

threads ：查看和操作后台线程

unload（卸载某个插件）：卸载一个框架插件

unset（删除某个设置参数）：取消设置一个或多个特定的上下文变量

unsetg（取消全局某个设置参数）：取消设置一个或多个全局变量的

use（使用某个模块）：选择按名称模块

version（查看版本信息）：显示的框架和控制台库版本号


