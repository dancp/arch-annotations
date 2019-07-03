1. [Pre Instalação](#pre-instalação)
     - [Layout do Teclado](#layout-do-teclado)
       - [Modificar o layout](#modificar-o-layout)
     - [Atualizar o Relógio do Sistema](#atualizar-o-relógio-do-sistema)
     - [Partição dos Discos](#partição-dos-discos)
       - [Listar discos](#listar-discos)
       - [Criar partições](#criar-partições)
       - [Formatar as partições](#formatar-as-partições)
       - [Montar os sistemas de arquivos](#montar-os-sistemas-de-arquivos)
2. [Instalação](#instalação)
    - [Mirrors](#mirrors)
    - [Instalar os pacotes base](#instalar-os-pacotes-base)

<br>

## Pre Instalação
<br>

### Layout do Teclado
 
#### Modificar o layout

    # loadkeys br-abnt2
    ou
    # localectl set-keymap br-abnt2
<br>

### Atualizar o Relógio do Sistema

    # timedatectl set-ntp true
<br>

### Partição dos Discos

#### Listar discos

    # fdisk -l
<br>

#### Criar partições

    # cfdisk
<br>

#### Formatar as partições

    # mkfs.ext4 /dev/sdX1
    
    # mkswap /dev/sdX2
    # swapon /dev/sdX2
<br>

#### Montar os sistemas de arquivos

    # mount /dev/sdX1 /mnt

<br><br>

## Instalação

#### Mirrors

    > /etc/pacman.d/mirrorlist
    # sed "s/^Ser/#Ser/" /etc/pacman.d/mirrorlist > /tmp/mirrors
    # sed '/Brazil/{n;s/^#//}' /tmp/mirrors > /etc/pacman.d/mirrorlist
<br>

#### Instalar os pacotes base

    # pacstrap /mnt base base-devel

<br><br>

## Configuração do Sistema

#### Fstab

    # genfstab -p /mnt >> /mnt/etc/fstab
<br>

#### Chroot

    # arch-chroot /mnt
<br>

#### Fuso horário

    # ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime
    # hwclock --systohc
<br>

#### Localização

    # nano /etc/locale.gen
    > en_US.UTF-8 UTF-8
    > pt_BR.UTF-8 UTF-8
    # locale-gen
<br>
  
#### Linguagem

    # echo LANG=en_US.UTF-8 > /etc/locale.conf
    # export LANG=en_US.UTF-8 
<br>

#### Layout do teclado

    # echo KEYMAP=br-abnt2 > /etc/vconsole.conf
<br>

#### Nome do computador

    # echo meuhostname > /etc/hostname
    
    # nano /etc/hosts
    127.0.0.1   localhost.localdomain   localhost
    ::1         localhost.localdomain   localhost
    127.0.1.1   meuhostname.localdomain meuhostname
<br>

#### Configurar conexão (Temporario)

    # systemctl enable dhcpcd
<br>

#### Initramfs

    # mkinitcpio -p linux
<br>

#### Senha do Root

    # passwd
<br>

#### Criar usuário

    # useradd -m -g users -G log,sys,wheel,rfkill,dbus -s /bin/bash usuario
    # passwd usuario
    # sed -i '/%wheel ALL=(ALL) ALL/s/^#//' /etc/sudoers
<br>

#### Grub

    # pacman -S grub os-prober intel-ucode ntfs-3g
    # grub-install --target=i386-pc /dev/sdX
    # grub-mkconfig -o /boot/grub/grub.cfg
<br>

#### Reiniciar

    # exit
    # umount -R /mnt
    # reboot

<br>

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Pós Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-post-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
