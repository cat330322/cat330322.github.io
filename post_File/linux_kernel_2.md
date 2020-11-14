linux_kernel_2
---

Linux内核4.19.12，BusyBox1.29.3和Syslinux6.03
ubuntu

sudo apt install wget make gawk gcc bc bison flex xorriso libelf-dev libssl-dev

---

wget http://kernel.org/pub/linux/kernel/v4.x/linux-4.19.12.tar.xz

wget http://busybox.net/downloads/busybox-1.29.3.tar.bz2

wget http://kernel.org/pub/linux/utils/boot/syslinux/syslinux-6.03.tar.xz

mkdir isoimage

tar -xvf linux-4.19.12.tar.xz

tar -xvf busybox-1.29.3.tar.bz2

tar -xvf syslinux-6.03.tar.xz

cd busybox-1.29.3

make distclean defconfig

sed -i "s|.*CONFIG_STATIC.*|CONFIG_STATIC=y|" .config

make busybox install

cd _install

rm -f linuxrc

mkdir dev proc sys

echo '#!/bin/sh' > init

echo 'dmesg -n 1' >> init

echo 'mount -t devtmpfs none /dev' >> init

echo 'mount -t proc none /proc' >> init

echo 'mount -t sysfs none /sys' >> init

echo 'setsid cttyhack /bin/sh' >> init

chmod +x init

find . | cpio -R root:root -H newc -o | gzip > ../../isoimage/rootfs.gz

cd ../../linux-4.19.12

make mrproper defconfig bzImage

cp arch/x86/boot/bzImage ../isoimage/kernel.gz

cd ../isoimage

cp ../syslinux-6.03/bios/core/isolinux.bin .

cp ../syslinux-6.03/bios/com32/elflink/ldlinux/ldlinux.c32 .

echo 'default kernel.gz initrd=rootfs.gz' > ./isolinux.cfg

xorriso \

    -as mkisofs \

    -o ../minimal_linux_live.iso \

    -b isolinux.bin \

    -c boot.cat \

    -no-emul-boot \

    -boot-load-size 4 \

    -boot-info-table \

    ./

cd ..

---

minimal.sh

#!/bin/sh

set -ex

KERNEL_VERSION=5.0.2

BUSYBOX_VERSION=1.30.1

SYSLINUX_VERSION=6.03

wget -O kernel.tar.xz http://kernel.org/pub/linux/kernel/v5.x/linux-${KERNEL_VERSION}.tar.xz

wget -O busybox.tar.bz2 http://busybox.net/downloads/busybox-${BUSYBOX_VERSION}.tar.bz2

wget -O syslinux.tar.xz http://kernel.org/pub/linux/utils/boot/syslinux/syslinux-${SYSLINUX_VERSION}.tar.xz

tar -xvf kernel.tar.xz

tar -xvf busybox.tar.bz2

tar -xvf syslinux.tar.xz

mkdir isoimage

cd busybox-${BUSYBOX_VERSION}

make distclean defconfig

sed -i "s|.*CONFIG_STATIC.*|CONFIG_STATIC=y|" .config

make busybox install

cd _install

rm -f linuxrc

mkdir dev proc sys

echo '#!/bin/sh' > init

echo 'dmesg -n 1' >> init

echo 'mount -t devtmpfs none /dev' >> init

echo 'mount -t proc none /proc' >> init

echo 'mount -t sysfs none /sys' >> init

echo 'setsid cttyhack /bin/sh' >> init

chmod +x init

find . | cpio -R root:root -H newc -o | gzip > ../../isoimage/rootfs.gz

cd ../../linux-${KERNEL_VERSION}

make mrproper defconfig bzImage

cp arch/x86/boot/bzImage ../isoimage/kernel.gz

cd ../isoimage

cp ../syslinux-${SYSLINUX_VERSION}/bios/core/isolinux.bin .

cp ../syslinux-${SYSLINUX_VERSION}/bios/com32/elflink/ldlinux/ldlinux.c32 .

echo 'default kernel.gz initrd=rootfs.gz' > ./isolinux.cfg

xorriso \

  -as mkisofs \

  -o ../minimal_linux_live.iso \

  -b isolinux.bin \

  -c boot.cat \

  -no-emul-boot \

  -boot-load-size 4 \

  -boot-info-table \

  ./

cd ..

set +ex

---

qemu64.sh

#!/bin/sh

qemu-system-x86_64 -m 128M -cdrom minimal_linux_live.iso -boot d -vga std

---

clean.sh

#!/bin/sh

rm -rf busybox* isoimage kernel* linux* *.iso syslinux*