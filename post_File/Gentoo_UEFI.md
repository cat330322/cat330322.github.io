###Gentoo

---


＃使用 parted 分区工具

parted /dev/nvme0n1

＃查看操作说明

(parted) help

＃设置 gpt 分区类型 注意：这个设置会格式化整个磁盘

(parted) mklabe gpt

＃容量查看 MB

(parted) unit mib

＃分区大小 start：起始容量 end：结束容量，分区大小：end - start

(parted) mkpart primary start end

＃打印整个磁盘分区

(parted) print

(parted) mkpart primary 1 11

(parted) name 1 grub

(parted) set 1 bios_grub on

(parted) mkpart primary 11 139

(parted) name 2 boot

(parted) set 2 boot on


(parted) mkpart primary 139 -l

(parted) name 3 root


mkfs.ext2 /dev/nvme0n1p

mkfs.fat -F 32 /dev/nvme0n1p2

mkfs.ext4 /dev/nvme0n1p3

＃创建boot home目录

mkdir -p /mnt/gentoo/boot/efi 

mkdir /mnt/gentoo/home

mount /dev/nvme0n1p3 /mnt/gentoo

mount /dev/nvme0n1p2 /mnt/gentoo/boot/efi

mount /dev/sda3 /mnt/gentoo/home

mount

date 月日时间年

cd /mnt/gentoo

time tar xvf stage3-amd64-20180920T214502Z.tar.xz

cat /proc/cpuinfo | grep processor

echo 'MAKEOPTS="-j9"' >> /etc/portage/make.conf

mirrorselect -i -o >> /mnt/gentoo/etc/portage/make.conf

mkdir --parents /mnt/gentoo/etc/portage/repos.conf

cp /mnt/gentoo/usr/share/portage/config/repos.conf /mnt/gentoo/etc/portage/repos.conf/gentoo.conf


cp --dereference /etc/resolv.conf /mnt/gentoo/etc/

mount --types proc /proc /mnt/gentoo/proc

mount --rbind /sys /mnt/gentoo/sys

mount --rbind /dev /mnt/gentoo/dev

chroot /mnt/gentoo /bin/bash

source /etc/profile

export PS1="(chroot) ${PS1}"

emerge-webrsync

eselect profile list

eselect profile set 12

time emerge --ask --quiet --update --deep --newuse @world

ls /usr/share/zoneinfo/Asia

echo "Asia/Shanghai" > /etc/timezone

emerge --config sys-libs/timezone-data

nano -w /etc/locale.gen

locale-gen

eselect locale list

eselect locale set 8

env-update && source /etc/profile && export PS1="(chroot) $PS1"

emerge --ask sys-kernel/gentoo-sources

etc-update -3

time emerge --ask --quiet sys-kernel/genkernel

nano -w /etc/fstab

time genkernel all

ls /boot/kernel* /boot/initramfs*
//会显示两个文件　　

time emerge --ask --quiet sys-kernel/linux-firmware

nano -w /etc/conf.d/hostname

＃将hostname变量设置为自己取的主机名字

hostname =“Guard”

nano -w /etc/conf.d/net

＃将dns_domain_lo变量设置为所选域名

dns_domain_lo =“homenetwork”

time emerge --ask  --quiet --noreplace net-misc/netifrc

cd /etc/init.d

ln -s net.lo net.enp3s0

rc-update add net.enp3s0 default


nano -w /etc/hosts

passwd

nano -w /etc/conf.d/hwclock

＃修改：clock="local"

emerge --ask app-admin/sysklogd

rc-update add sysklogd default

emerge --ask sys-apps/mlocate

rc-update add sshd default

emerge --ask net-misc/dhcpcd

echo 'GRUB_PLATFORMS="efi-64"' >> /etc/portage/make.conf

emerge --ask sys-boot/grub:2


grub-install --target=x86_64-efi --efi-directory=/boot/efi --removable

grub-mkconfig -o /boot/grub/grub.cfg

exit

reboot
