# 安全审计-Lynis
---

一、Lynis是什么？ Lynis是一款基于UNIX系统的安全审计工具，如Linux，macOS，BSD等，它执行深入的安全扫描并在系统本身上运行。Lynis的主要目标是测试安全防御，并提供进一步系统强化的提示。扫描完成后，Lynis还会为我们生成一份包含所有扫描结果的安全报告。 Lynis专注于从内部扫描系统本身，它还将扫描一般系统信息，易受攻击的软件包以及可能的配置问题。系统管理员和审计员通常使用Lynis来评估其系统的安全性。Lynis也是黑客惯常使用的一款渗透工具

 二、Lynis可概括如下，帮助大家理解和掌握 特征： 漏洞扫描 系统加固 入侵检测 中心管理 自定义行为规划 报告 安全面板 持续监测 技术支持 目标： 自动安全审计 符合性测试 漏洞侦测 有助于： 配置管理 软件补丁管理 系统加固 渗透测试 恶意软件扫描 入侵检测  

三、Lynis适用哪些人员？ Lynis非常适合于安全审计人员，网络安全专家，渗透测试人员，网络和系统管理人员以及安全工程师使用

四、Lynis支持参数有哪些？ 用法： lynis command [options]  lynis 命令 [选项]    命令： audit audit system : 执行本地安全扫描 audit system remote 

 : 远程安全扫描 audit dockerfile 

 : 分析Docker文件   show show : 显示所有命令 show version : 显示Lynis版本 show help : 显示帮助   update update info : 显示更新详细信息 update release : 更新Lynis版本 选项： --no-log : 不要创建日志文件 --pentest : 非特权扫描（适用于最适合） --profile 

 : 使用给定的配置文件扫描系统 --quick (-Q) : 快速模式，不要等待用户输入   布局选项： --no-colors : 不要在输出中使用颜色 --quiet (-q) : 无输出 --reverse-colors : 优化浅色背景的彩色显示   其它选项： --debug : 调试日志记录到屏幕 --view-manpage (--man) : 查看手册页 --verbose : 在屏幕上显示更多细节 --version (-V) : 显示版本号并退出   企业选项： --plugin-dir "

" : 定义可用插件的路径 --upload : 将数据上传到中央节点 五、Lynis怎么使用？举例 1、扫描系统 # lynis audit system 或者 lynis --check-all 2、lynis audit system remote 192.168.x.x （远程扫描服务器，需指定ip地址，根据提示操作） 3、日志查看 more /var/log/lynis-report.dat
