# Metasploit-持久化
---

查看攻击者主机目前的会话连接情况，命令：sessions

命令：sessions -i Id

命令：sessions -i 5

命令：help

查看攻击者主机当前的进行Id，命令：getpid

查看受害者主机的所有进程，命令：ps

选择上述列出的一个系统进程，利用命令将攻击者主机的会话信息跟受害者主机的系统进程绑定在一起提高会话稳定性，如下图所示。例子：migrate 6832

再次确定当前的进程号（pid），命令：getpid

