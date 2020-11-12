linux-kernel_1
---

相关依赖

sudo apt-get install zlib1g-dev

sudo apt-get install libglib2.0-dev

sudo apt-get install autoconf automake libtool

sudo apt-get install libsdl1.2-dev

---

sudo apt-get install libncurses5-dev

sudo apt-get install build-essential openssl

sudo apt-get install flex

sudo apt-get install bison

sudo apt-get install openssl

sudo apt-get install klibssl-dev

---


1、export ARCH=x86  //1.指定硬件体系架构  

2.配置board config,此处配置为 x86_64_defconfig。好了，我们点好菜了，菜单就是x86_64_defconfig

make  x86_64_defconfig

3.配置内核

这一步其实是对第2步的菜单进行微调，我们需要内核支持ramdisk驱动，所以需要选中如下配置：

General setup ---> ----> [*] Initial RAM filesystem and RAM disk (initramfs/initrd) support Device Drivers ---> [*] Block devices ---> <*> RAM block device support (65536) Default RAM disk size (kbytes)

4.编译内核

tar xvf linux内核包

export ARCH=x86

存储内核配置 linux/arch/x86/configs/x86_64_defconfig

cd linux

make  x86_64_defconfig

make
编译成功后的内核位于：arch/x86_64/boot/bzImage

---

busybox

tar xvf busybox-1.32.0.tar.bz2 工具集合

把busybox配置为静态编译，这样busybox在运行的时候就不需要额外的动态链接库了。

make menuconfigBusybox Settings  --->      Build Options  --->            [*] Build BusyBox as a static binary (no shared libs)

编译和安装

make && make install

编译完成后的busybox就安装在源码根目录下的_install目录了，我们进入_install目录，

mkdir etc dev mnt

mkdir -p etc/init.d/

vim etc/fstab

proc  /proc proc  defaults 0 0

temps /tmp  rpoc  defaults 0 0

none  /tmp  ramfs defaults 0 0

sysfs /sys  sysfs defaults 0 0

mdev  /dev  ramfs defaults 0 0

vim etc/init.d/rcS

mkdir -p /proc

mkdir -p /tmp

mkdir -p /sys

mkdir -p /mnt

/bin/mount -a

mkdir -p /dev/pts

mount -t devpts devpts /dev/pts

echo /sbin/mdev > /proc/sys/kernel/hotplug

mdev -s

chmod 755 etc/init.d/rcS

vim etc/inittab

::sysinit:/etc/init.d/rcS

::respawn:-/bin/sh

::askfirst:-/bin/sh

::cttlaltdel:/bin/umount -a -r

chmod 755 etc/inittab

cd dev# mknod console c 5 1

mknod null c 1 3

---

思路：

1.先制作一个空的镜像文件；

2.然后把此镜像文件格式化为ext3格式；

3.然后把此镜像文件挂载，并把根文件系统复制到挂载目录；

4.卸载该镜像文件。

5.打成gzip包。

#!/bin/bash

rm -rf rootfs.ext3

rm -rf fs

dd if=/dev/zero of=./rootfs.ext3 bs=1M count=32

mkfs.ext3 rootfs.ext3

mkdir fs

mount -o loop rootfs.ext3 ./fs

cp -rf ./_install/* ./fs

umount ./fs

gzip --best -c rootfs.ext3 > rootfs.img.gz

最终生成的文件系统镜像名字为：rootfs.img.gz

---

qemu-system-x86_64 \ 

 -kernel ./linux-4.9.229/arch/x86_64/boot/bzImage  \ 

 -initrd ./busybox-1.30.0/rootfs.img.gz   \ 

 -append 'root=/dev/ram init=/linuxrc'  \  

-serial file:output.txt

完整的最小linux系统

qemu-system-x86_64 -kernel ./linux-4.9.242/arch/x86_64/boot/bzImage  -initrd ./busybox-1.32.0/rootfs.img.gz  -append ./busybox-1.32.0/_install/linuxrc  -serial file:output.txt

---

相关依赖

sudo apt-get install zlib1g-dev

sudo apt-get install libglib2.0-dev

sudo apt-get install autoconf automake libtool

sudo apt-get install libsdl1.2-dev

---

sudo apt-get install libncurses5-dev

sudo apt-get install build-essential openssl

sudo apt-get install flex

sudo apt-get install bison

sudo apt-get install openssl

sudo apt-get install klibssl-dev

---

apt-cache search pixman 查询相关依赖

lsmod 驱动

elasticsearch

insmod helloDev.ko

dmesg -c

---

sudo make mrproper 清楚编译过程产生的中间文件，刚刚解压状态

sudo make clean 清楚中间文件

sudo make menuconfig 配置内核


---

kernel-book 推荐

Linux内核设计与实现

linux device drivers