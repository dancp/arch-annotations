## Índice

1. [Pre Instalação](#pre-instalação)
    - [Configurar Layout do Teclado](#configurar-layout-do-teclado)
    - [Atualizar o Relógio do Sistema](#atualizar-o-relógio-do-sistema)
    - [Listar discos](#listar-discos)
    - [Criar partições](#criar-partições)
    - [Formatar as partições](#formatar-as-partições)
    - [Montar os sistemas de arquivos](#montar-os-sistemas-de-arquivos)
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

### Teclado, internet e relógio

#### Configurar Layout do Teclado

    # loadkeys br-abnt2
    ou
    # localectl set-keymap br-abnt2
<br>

#### Obter conexão WiFi

    # wifi-menu
<br>

#### Obter conexão a cabo

    # systemctl start dhcpcd
<br>

#### Atualizar o Relógio do Sistema

    # timedatectl set-ntp true
<br>

### Partições
#### Listar discos e partições

    # fdisk -l
<br>

#### Criar partições

    # cfdisk /dev/sdX
<br>

#### Estrutura de partições (BIOS)

    # /dev/sdX1 (-GB)   /
    # /dev/sdX2 (-GB)   /home
    # /dev/sdX3 (-GB)   swap
<br>

#### Formatar as partições (BIOS)

    # mkfs.ext4 /dev/sdX1
    # mkfs.ext4 /dev/sdX2
    # mkswap /dev/sdX3
<br>

#### Montar partição (BIOS)

    # mount /dev/sdX1 /mnt
    # mkdir -p /mnt/home && mount /dev/sda2 /mnt/home
    # swapon /dev/sdX3
<br>

#### Estrutura de partições (UEFI)

    # /dev/sdX1 (512MB) /boot/efi
    # /dev/sdX2 (-GB)   /
    # /dev/sdX3 (-GB)   /home
    # /dev/sdX4 (-GB)   swap
<br>

#### Formatar as partições (UEFI)

    # mkfs.fat -F32 /dev/sdX1
    # mkfs.ext4 /dev/sdX2
    # mkfs.ext4 /dev/sdX3
    # mkswap /dev/sdX4
<br>

#### Montar partição (UEFI)

    # mount /dev/sdX2 /mnt
    # mkdir -p /mnt/home && mount /dev/sda2 /mnt/home
    # mkdir -p /mnt/boot/efi && mount /dev/sda1 /mnt/boot/efi
    # swapon /dev/sdX3
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

    # echo LANG=en_US.UTF-8 >> /etc/locale.conf
    # export LANG=en_US.UTF-8 
<br>

#### Layout do teclado

    # echo KEYMAP=br-abnt2 >> /etc/vconsole.conf
<br>

#### Nome do computador

    # echo meuhostname >> /etc/hostname
    
    # nano /etc/hosts
    127.0.0.1   localhost.localdomain   localhost
    ::1         localhost.localdomain   localhost
    127.0.1.1   meuhostname.localdomain meuhostname
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

#### Grub (BIOS)

    # pacman -S grub os-prober intel-ucode ntfs-3g
    # grub-install --target=i386-pc /dev/sdX
    # grub-mkconfig -o /boot/grub/grub.cfg
<br>

#### Grub (BIOS)

    # pacman -S grub efibootmgr os-prober intel-ucode ntfs-3g
    # grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=grub --recheck
    # grub-mkconfig -o /boot/grub/grub.cfg
<br>

#### Conexão Wifi

    # pacman -S networkmanager wpa_supplicant iw
    
    # systemctl enable NetworkManager

#### Reiniciar

    # exit
    # umount -R /mnt
    # reboot
<br>

- [Pós Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-post-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
