## Índice

1. [Pós Instalação](#pós-instalação)
    - [Habilitar suporte 32-bits](#habilitar-suporte-32-bits)
    - [Xorg](#xorg)
    - [Nvidia](#nvidia)
    - [AMD](#amd)
    - [Intel](#intel)
    - [Som](#som)
    - [KDE Plasma](#kde-plasma)
    - [Display Manager](#display-manager)
    - [Network Manager](#network-manager)
2. [Extras](#extras)
    - [Geral](#geral)
    - [Firewall](#firewall)
    - [Fonts](#fonts)
    - [Codecs](#codecs)
    - [Pulse Effects](#pulse-effects)
    - [Openssh](#openssh)
    - [Yay](#yay)
    - [Wine](#wine)
    - [Steam](#steam)
    
- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
<br>

## Pós Instalação


#### Packages

    # git clone https://github.com/dancp/arch-annotations.git
    # pacman -S --needed - < pkglist.txt
<br>

#### Habilitar suporte 32-bits

    # nano /etc/pacman.conf
    
    [multilib]
    Include = /etc/pacman.d/mirrorlist
<br>

#### Display Manager

    # systemctl enable sddm.service
<br>

#### Network Manager

    /etc/NetworkManager/conf.d/dhcp-client.conf
    [main]
    dhcp=dhcpcd
    
    # systemctl enable NetworkManager.service
<br><br>

## Extras

#### Openssh

    # systemctl enable sshd.service
<br>

#### Firewall
 
    # pacman -S gufw
    # ufw enable
    # systemctl enable ufw.service
```    
# ufw default deny
# ufw allow from 192.168.0.0/24
# ufw limit SSH
```
```
KDEConnect
sudo ufw allow 1714:1764/udp
sudo ufw allow 1714:1764/tcp
sudo ufw reload
```
<br>

#### Internet
    # systemctl disable dhcpcd
<br>

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
