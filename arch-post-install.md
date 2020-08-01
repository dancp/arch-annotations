## Índice

1. [Pós Instalação](#pós-instalação)
    - [Habilitar suporte 32-bits](#habilitar-suporte-32-bits)
    - [Packages](#packages)
    - [Display Manager](#display-manager)
    - [Network Manager](#network-manager)
    - [Openssh](#openssh)
    - [Firewall](#firewall)
    - [Yay](#yay)
    
- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
<br>

## Pós Instalação

#### Habilitar suporte 32-bits

    # nano /etc/pacman.conf
    
    [multilib]
    Include = /etc/pacman.d/mirrorlist
    
    # sudo pacman -Sy
<br>

#### Packages

    # git clone https://github.com/dancp/arch-annotations.git
    # sudo pacman -S --needed - < pkglist.txt
<br>

#### Display Manager

    # systemctl enable sddm.service
<br>

#### Network Manager

    # systemctl enable NetworkManager.service
<br>

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
