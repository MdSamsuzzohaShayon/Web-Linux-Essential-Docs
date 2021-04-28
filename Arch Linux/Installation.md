# Arch Linux

 [Arch linux on virtualbox](https://wiki.archlinux.org/index.php/VirtualBox/Install_Arch_Linux_as_a_guest)
 - Install virtualbox -> [download arch linux](https://archlinux.org/download/)
 - From virtual box create a new container -> setup -> start arch linux
 - Change fonts size `ls /usr/share/kbd/consolefonts` from here set font size `setfont ter-232.psf.gz` \ setfont ter-216.psf.gz
 - Check for internet connection `ping archlinux.org`
 - Load councile keymap or keyboard layout `ls /usr/share/kbd/keymaps/i386/qwerty` -> `loadkeys us.map.gz` (not required)
 - Check our system is booted in uefi mode `ls /sys/fireware/efi/efivars`
 - Setup time and date `timedatectl set-ntp true` and check  `timedatectl status`
 - Creating partition -> use `efdisk` -> Create first new partition from free space -> set size of 1gb and type of **EFISystem** -> create another partition from freespace -> size whole -> default linux file system -> once two partition is made write the file and quite
 - Format partition for second partition `mkfs.ext4 /dev/sda2`, for first partition `mkfs.fat -F32 /dev/sda1`
 - Mount both partition `mount /dev/sda2 /mnt`, create dir `mkdir /mnt/efi` mount first partition `mount /dev/sda1 /mnt/efi`
 - use **pacstrap** to get packages `pacstrap /mnt base linux linux-firmware`

 - Generate a uuid for our disk -> `genfstab -U /mnt >> /mnt/etc/fstab`
 - Change over to root file system `arch-chroot /mnt` and `ls` 
 - Setup timezone `ln -sf /usr/share/zoneinfo` see all the zone -> `ln -sf /usr/share/zoneinfo/Bangladesh/Dhaka /etc/localtime`
 - Setup clock `hwclock --systohc`
 - Install text editor **vim** and **nano** `pacman -Syu vim` and `pacman -Syu nano`
 - Open `nano /etc/locale.gen` and uncomment `en_US.UTF-8 UTF-8` from examples
 - Set hostname for our computer `nano /etc/hostname` name anything
 - now setup hosts `nano /etc/hosts` add those lines
    ```
    127.0.0.1   localhost
    ::1         localhost
    127.0.1.1   shayon.localdomain  shayon
    ```
 - Set password for root `passwd`
 - Create a user `useradd -G wheel,audio,video -m shayon` this will also create a user home dir -> set password for user `passwd shayon`
 - Get few packages -> Newworking setup on arch linux `pacman -Syu netctl` and `pacman -Syu dhcpcd` 
 - Install sudo for asking permission for normal users `pacman -Syu sudo` -> `EDITOR=nano visudo` now uncomment `%Wheel ALL=(ALL) ALL`
 - Install boot -> `pacman -Syu grub efibootmgr` -> we are ready to setup arch linux grub boot loader
 - 
