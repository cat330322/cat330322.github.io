termux

---

Termux 会自动将环境变量 $PREFIX 设定为 /data/data/com.termux/files/usr

export EDITOR=vi

vi  $PREFIX/etc/apt/sources.list

apt edit-sources

pkg install apt-tools

proot

atilo

/data/data/com.termux/files/usr/etc/apt/sources.list 为如下内容

源 deb https://mirrors.ustc.edu.cn/termux stable main

apachectl -k start /stop

termux-setup-storage
