## Índice

1. [Pre Instalação](#pre-instalação)
    - [Configurar layout do teclado](#configurar-layout-do-teclado)
    - [Atualizar o relógio do sistema](#atualizar-o-relógio-do-sistema)
    - [Criar partições](#criar-partições)
    - [Estrutura de partições](#estrutura-de-partições)
    - [Formatar partições](#formatar-partições)
    - [Montar partições](#montar-partições)
2. [Instalação](#instalação)
    - [Mirrors](#mirrors)
    - [Instalar os pacotes base](#instalar-os-pacotes-base)
3. [Configuração do Sistema](#configuração-do-sistema) 
    - [Fstab](#fstab)
    - [Chroot](#chroot)
    - [Fuso horário](#fuso-horário)
    - [Localização](#localização)
    - [Linguagem](#linguagem)
    - [Layout do teclado](#layout-do-teclado)
    - [Nome do computador](#nome-do-computador)
    - [Initramfs](#initramfs)
    - [Senha do Root](#senha-do-root)
    - [Criar usuário](#criar-usuário)
    - [Grub](#grub)
    - [Reiniciar](#reiniciar)

- [Pós Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-post-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
<br>

## Pre Instalação
<br>

### Pré Configurações

#### Configurar layout do teclado

    # loadkeys br-abnt2
    ou
    # localectl set-keymap br-abnt2
<br>

#### Atualizar o relógio do sistema

    # timedatectl set-ntp true
<br><br>

### Partições
#### Listar discos e partições

    # fdisk -l
<br>

#### Criar partições

    # cfdisk /dev/sdX
<br>

#### Estrutura de partições

    # /dev/sdX1 (512MB) /boot/efi
    # /dev/sdX2 (-GB)   /
    # /dev/sdX3 (-GB)   /home
    # /dev/sdX4 (-GB)   swap
<br>

#### Formatar partições

    # mkfs.fat -F32 /dev/sdX1
    # mkfs.ext4 /dev/sdX2
    # mkfs.ext4 /dev/sdX3
    # mkswap /dev/sdX4
<br>

#### Montar partições

    # mount /dev/sdX2 /mnt
    # mkdir -p /mnt/home && mount /dev/sda3 /mnt/home
    # mkdir -p /mnt/boot/efi && mount /dev/sda1 /mnt/boot/efi
    # swapon /dev/sdX4
<br><br>

## Instalação

#### Mirrors

    # reflector --country Brazil --age 12 --sort rate --save /etc/pacman.d/mirrorlist
<br>

#### Instalar os pacotes base

    # pacstrap /mnt base linux linux-firmware

<br><br>

## Configuração do Sistema

#### Fstab

    # genfstab -U /mnt >> /mnt/etc/fstab
<br>

#### Chroot

    # arch-chroot /mnt
<br>

#### Ferramentas 

    # pacman -S dhcpcd nano sudo
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

    # nano /etc/locale.conf
    # LANG=en_US.UTF-8
    # LC_ADDRESS=pt_BR.UTF-8
    # LC_IDENTIFICATION=pt_BR.UTF-8
    # LC_MEASUREMENT=pt_BR.UTF-8
    # LC_MONETARY=pt_BR.UTF-8
    # LC_NAME=pt_BR.UTF-8
    # LC_NUMERIC=pt_BR.UTF-8
    # LC_PAPER=pt_BR.UTF-8
    # LC_TELEPHONE=pt_BR.UTF-8
    # LC_TIME=pt_BR.UTF-8

<br>

#### Layout do teclado

    # nano /etc/vconsole.conf
    # KEYMAP=br-abnt2
    # FONT=
    # FONT_MAP=
<br>

#### Nome do computador

    # nano /etc/hostname
    # nomedamaquina
    
    # nano /etc/hosts
    127.0.0.1  localhost
    127.0.1.1  nomedamaquina
    ::1        localhost ip6-localhost ip6-loopback
    ff02::1    ip6-allnodes
    ff02::2    ip6-allrouters

<br>

#### Initramfs

    # mkinitcpio -P
<br>

#### Senha do Root

    # passwd
<br>

#### Criar usuário

    # useradd -m -G sys,log,dbus,rfkill,storage,lp,wheel -s /bin/bash nomedousuario
    # passwd nomedousuario
    # sed -i '/%wheel ALL=(ALL) ALL/s/^#//' /etc/sudoers
<br>

#### Grub

    # pacman -S grub efibootmgr os-prober amd-ucode ntfs-3g
    # grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=Arch
    # grub-mkconfig -o /boot/grub/grub.cfg
<br>

#### Internet

    # systemctl enable dhcpcd
<br>

#### Reiniciar

    # exit
    # umount -R /mnt
    # reboot
<br>

- [Pós Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-post-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
