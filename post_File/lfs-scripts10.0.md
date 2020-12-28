#lfs-scripts10.0

---

构建 LFS（Linux 从零开始）的指令和脚本，版本 10.0

http://www.linuxfromscratch.org/lfs/

https://github.com/cat330322/lfs-scripts.git

---

ftp://ftp.lfs-matrix.net/pub/lfs/ （美国加利福尼亚州洛杉矶，200Mbps）

http://ftp.lfs-matrix.net/pub/lfs/ （美国加利福尼亚州洛杉矶，200Mbps）

ftp://ftp.osuosl.org/pub/lfs/（美国奥萨瓦利斯，100Mbps）

http://ftp.osuosl.org/pub/lfs/（美国奥瓦利斯，100Mbps）

http://mirror.jaleco.com/lfs/pub/（美国华盛顿特区，1 Gbps）

---

mkdir /mnt/lfs

fdisk /dev/sdb

---

mkfs.ext4 /dev/sdb1

mkdir /mnt/lfs

mount /dev/sdb1 /mnt/lfs

---

export LFS=/mnt/lfs

---

source .bashrc

---

cd $LFS

cp /<location_of_the_package>/lfs-packages-10.0.tar .

tar xf lfs-packages-10.0.tar

mv 10.0 sources

chmod -v a+wt $LFS/sources

mv $LFS/sources/tcl8.6.10-src.tar.gz $LFS/sources/tcl8.6.10.tar.gz

---

cp /<location_of_the_scripts>/*.sh $LFS

---

mkdir -pv $LFS/{bin,etc,lib,sbin,usr,var,lib64,tools}

---

groupadd lfs
useradd -s /bin/bash -g lfs -m -k /dev/null lfs
passwd lfs

---

chown -R lfs:lfs $LFS/*
chown lfs:lfs $LFS

---


su - lfs

---

cat > ~/.bash_profile << "EOF"

exec env -i HOME=$HOME TERM=$TERM PS1='\u:\w\$ ' /bin/bash

EOF

---

cat > ~/.bashrc << "EOF"

set +h

umask 022

LFS=/mnt/lfs

LC_ALL=POSIX

LFS_TGT=$(uname -m)-lfs-linux-gnu

PATH=/usr/bin

if [ ! -L /bin ]; then PATH=/bin:$PATH; fi

PATH=$LFS/tools/bin:$PATH

export LFS LC_ALL LFS_TGT PATH

EOF

source ~/.bashrc

---

sh $LFS/lfs-cross.sh | tee $LFS/lfs-cross.log

---

exit

---

chown -R root:root $LFS/*

chown root:root $LFS

---

mkdir -pv $LFS/{dev,proc,sys,run}

mknod -m 600 $LFS/dev/console c 5 1

mknod -m 666 $LFS/dev/null c 1 3

mount -v --bind /dev $LFS/dev

mount -v --bind /dev/pts $LFS/dev/pts

mount -vt proc proc $LFS/proc

mount -vt sysfs sysfs $LFS/sys

mount -vt tmpfs tmpfs $LFS/run

if [ -h $LFS/dev/shm ]; then

  mkdir -pv $LFS/$(readlink $LFS/dev/shm)

fi

---

chroot "$LFS" /usr/bin/env -i   \

    HOME=/root                  \

    TERM="$TERM"                \

    PS1='(lfs chroot) \u:\w\$ ' \

    PATH=/bin:/usr/bin:/sbin:/usr/sbin \

    /bin/bash --login +h

---

mkdir -pv /{boot,home,mnt,opt,srv}

mkdir -pv /etc/{opt,sysconfig}

mkdir -pv /lib/firmware

mkdir -pv /media/{floppy,cdrom}

mkdir -pv /usr/{,local/}{bin,include,lib,sbin,src}

mkdir -pv /usr/{,local/}share/{color,dict,doc,info,locale,man}

mkdir -pv /usr/{,local/}share/{misc,terminfo,zoneinfo}

mkdir -pv /usr/{,local/}share/man/man{1..8}

mkdir -pv /var/{cache,local,log,mail,opt,spool}

mkdir -pv /var/lib/{color,misc,locate}

ln -sfv /run /var/run

ln -sfv /run/lock /var/lock

install -dv -m 0750 /root

install -dv -m 1777 /tmp /var/tmp

ln -sv /proc/self/mounts /etc/mtab

echo "127.0.0.1 localhost $(hostname)" > /etc/hosts

cat > /etc/passwd << "EOF"

root:x:0:0:root:/root:/bin/bash

bin:x:1:1:bin:/dev/null:/bin/false

daemon:x:6:6:Daemon User:/dev/null:/bin/false

messagebus:x:18:18:D-Bus Message Daemon User:/var/run/dbus:/bin/false

nobody:x:99:99:Unprivileged User:/dev/null:/bin/false

EOF

cat > /etc/group << "EOF"

root:x:0:

bin:x:1:daemon

sys:x:2:

kmem:x:3:

tape:x:4:

tty:x:5:

daemon:x:6:

floppy:x:7:

disk:x:8:

lp:x:9:

dialout:x:10:

audio:x:11:

video:x:12:

utmp:x:13:

usb:x:14:

cdrom:x:15:

adm:x:16:

messagebus:x:18:

input:x:24:

mail:x:34:

kvm:x:61:

wheel:x:97:

nogroup:x:99:

users:x:999:

EOF

touch /var/log/{btmp,lastlog,faillog,wtmp}

chgrp -v utmp /var/log/lastlog

chmod -v 664  /var/log/lastlog

chmod -v 600  /var/log/btmp

exec /bin/bash --login +h

---

sh /lfs-chroot.sh | tee /lfs-chroot.log

---

find /usr/{lib,libexec} -name \*.la -delete

rm -rf /usr/share/{info,man,doc}/*

---

sh /lfs-system.sh | tee /lfs-system.log

---

passwd root

---

logout

chroot "$LFS" /usr/bin/env -i          \

    HOME=/root TERM="$TERM"            \

    PS1='(lfs chroot) \u:\w\$ '        \

    PATH=/bin:/usr/bin:/sbin:/usr/sbin \

    /bin/bash --login

---

sh /lfs-final.sh | tee /lfs-final.log

