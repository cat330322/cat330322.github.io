arch-uefi
---

编辑 /etc/pacman.d/mirrorlist， 在文件的最顶端添加

Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch

sudo pacman -Syy

fdisk /dev/sda

输入:g 建立gpt分区表:

sda1 +200M

sda2 +200M

sda3 all

mkfs.fat -F32 /dev/sda1

mkfs.ext4 /dev/sda2 

mkfs.ext4 /dev/sda3

mount /dev/sda3 /mnt

mkdir /mnt/boot

mount /dev/sda2 /mnt/boot

mkdir /mnt/boot/EFI

mount /dev/sda1 /mnt/boot/EFI

pacstrap -i /mnt base base-devel linux linux-firmware

genfstab -U /mnt >> /mnt/etc/fstab

cat /mnt/etc/fstab

arch-chroot /mnt /bin/bash

nano /etc/locale.gen

locale-gen

echo LANG=en_US.UTF-8 > /etc/locale.conf

ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

pacman -S dosfstools grub efibootmgr

grub-install --target=x86_64-efi --efi-directory=/boot/EFI --recheck

grub-mkconfig -o /boot/grub/grub.cfg

passwd

useradd -m -g users -s /bin/bash arch

nano /etc/sudoers

pacman -S dhcpcd

exit root

systemctl start dhcpcd

systemctl enable dhcpcd

---

显卡  lspci | grep VGA

pacman -S xf86-video-intel

安装X窗口系统

pacman -S xorg

pacman -S ttf-dejavu wqy-microhei

---

dwm

pacman -S xoeg-server xorg-server-utils xorg-xinit xf86-video-intel xf86-input-synaptics xorg-twm xterm
