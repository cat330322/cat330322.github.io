lfs-10.0

---

export MAKEFLAGS='-j4'

make -j4

---
备份

cd $LFS &&

tar -cJpf $HOME/lfs-temp-tools-10.0.tar.xz .


---

在确认 $LFS设定正确后，运行以下命令从备份档案进行还原：

还原

cd $LFS &&

rm -rf ./* &&

tar -xpf $HOME/lfs-temp-tools-10.0.tar.xz

---

构建节点

https://bf.mengyan1223.wang/lfs/zh_CN/10.0/chapter08/introduction.html

----

mount -v --bind /dev $LFS/dev

mount -v --bind /dev/pts $LFS/dev/pts

mount -vt proc proc $LFS/proc

mount -vt sysfs sysfs $LFS/sys

mount -vt tmpfs tmpfs $LFS/run


chroot "$LFS" /usr/bin/env -i   \

    HOME=/root                  \

    TERM="$TERM"                \

    PS1='(lfs chroot) \u:\w\$ ' \

    PATH=/bin:/usr/bin:/sbin:/usr/sbin \

    /bin/bash --login +h

---

chroot "$LFS" /usr/bin/env -i          \

    HOME=/root TERM="$TERM"            \

    PS1='(lfs chroot) \u:\w\$ '        \

    PATH=/bin:/usr/bin:/sbin:/usr/sbin \

    /bin/bash --login

---

使用 ifup 和 ifdown 命令，手动启用或禁用网络接口

---

cat > /etc/resolv.conf << "EOF"

nameserver 114.114.114.114

EOF

---

cat > /etc/hosts << "EOF"

127.0.0.1 localhost.localdomain localhost

::1       localhost ip6-localhost ip6-loopback

ff02::1   ip6-allnodes

ff02::2   ip6-allrouters

EOF

LC_ALL=ISO-8859-1 locale charmap

---

cat > /etc/fstab << "EOF"

# 文件系统     挂载点       类型     选项                转储  检查

#                                                              顺序

/dev/deb1     /            ext4    defaults            1     1

proc           /proc        proc     nosuid,noexec,nodev 0     0

sysfs          /sys         sysfs    nosuid,noexec,nodev 0     0

devpts         /dev/pts     devpts   gid=5,mode=620      0     0

tmpfs          /run         tmpfs    defaults            0     0

devtmpfs       /dev         devtmpfs mode=0755,nosuid    0     0

# End /etc/fstab

EOF

---

cd /tmp 

grub-mkrescue --output=grub-img.iso 

xorriso -as cdrecord -v dev=/dev/cdrw blank=as_needed grub-img.iso

---

grub-install /dev/sdb

---


---

cat > /boot/grub/grub.cfg << "EOF"

set default=0

set timeout=5

insmod ext4

set root=(hd1,0)

menuentry "GNU/Linux, Linux 5.8.3-lfs-10.0" {

        linux   /boot/vmlinuz-5.8.3-lfs-10.0 root=/dev/sda1 ro

}

EOF

---

硬 盘	分 区	Linux中的设备文件名	GRUB中的设备文件名

第一块 SCSI 硬盘	第一个主分区	/dev/sdal	hd(0,0)

第二个主分区	/dev/sda2	hd(0,1)

扩展分区	/dev/sda3	hd(0,2)

第一个逻辑分区	/dev/sda5	hd(0,4)

第二块 SCSI 硬盘	第一个主分区	/dev/sdb1	hd(1,0)

第二个主分区	/dev/sdb2	hd(1,1)

扩展分区	/dev/sdb3	hd(1,2)

第一个逻辑分区	/dev/sdb5	hd(1,4)
