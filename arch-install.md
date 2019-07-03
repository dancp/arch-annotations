**Pre Instalação
 
|Layout do Teclado|

-Modificar o layout

    # loadkeys br-abnt2
    ou
    # localectl set-keymap br-abnt2

    
|Atualizar o Relógio do Sistema|

    # timedatectl set-ntp true


|Partição dos Discos|

Listar discos

    # fdisk -l

Criar partições

    # cfdisk

Formatar as partições

    # mkfs.ext4 /dev/sdX1
    
    # mkswap /dev/sdX2
    # swapon /dev/sdX2

Montar os sistemas de arquivos

    # mount /dev/sdX1 /mnt


**Instalação

Mirrors

    > /etc/pacman.d/mirrorlist
    # sed "s/^Ser/#Ser/" /etc/pacman.d/mirrorlist > /tmp/mirrors
    # sed '/Brazil/{n;s/^#//}' /tmp/mirrors > /etc/pacman.d/mirrorlist

Instalar os pacotes base

    # pacstrap /mnt base base-devel


**Configuração do Sistema

Fstab

    # genfstab -p /mnt >> /mnt/etc/fstab

Chroot

    # arch-chroot /mnt

Fuso horário

    # ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime
    # hwclock --systohc

Localização

    # nano /etc/locale.gen
    > en_US.UTF-8 UTF-8
    > pt_BR.UTF-8 UTF-8
    # locale-gen
    
Linguagem

    # echo LANG=en_US.UTF-8 > /etc/locale.conf
    # export LANG=en_US.UTF-8 

Layout do teclado

    # echo KEYMAP=br-abnt2 > /etc/vconsole.conf

Nome do computador

    # echo meuhostname > /etc/hostname
    
    # nano /etc/hosts
    127.0.0.1   localhost.localdomain   localhost
    ::1         localhost.localdomain   localhost
    127.0.1.1   meuhostname.localdomain meuhostname

Configurar conexão (Temporario)

    # systemctl enable dhcpcd

Senha do Root

    # passwd

Criar usuário

    # useradd -m -g users -G log,sys,wheel,rfkill,dbus -s /bin/bash usuario
    # passwd usuario
    # sed -i '/%wheel ALL=(ALL) ALL/s/^#//' /etc/sudoers

Grub

    # pacman -S grub os-prober intel-ucode ntfs-3g
    # grub-install --target=i386-pc /dev/sdX
    # grub-mkconfig -o /boot/grub/grub.cfg

Reiniciar

    # exit
    # umount -R /mnt
    # reboot
