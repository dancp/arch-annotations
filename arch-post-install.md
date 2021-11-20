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

    # sudo nano /etc/pacman.conf
    
    [multilib]
    Include = /etc/pacman.d/mirrorlist
    
    # sudo pacman -Sy
<br>

#### Packages

    # git clone https://github.com/dancp/arch-annotations.git
    # sudo pacman -S --needed - < pkglist.txt
<br>

#### Interface Gráfica

    # sudo pacman -S xorg
    # sudo pacman -S --needed xf86-video-amdgpu mesa lib32-mesa mesa-vdpau lib32-mesa-vdpau libva-mesa-driver lib32-libva-mesa-driver libva-vdpau-driver lib32-libva-vdpau-driver vulkan-radeon lib32-vulkan-radeon vkd3d lib32-vkd3d
    # sudo pacman -S --needed plasma
<br>

#### Display Manager

    # sudo systemctl enable sddm.service
<br>

#### Network Manager

    # sudo systemctl enable NetworkManager.service
<br>

#### Openssh

    # sudo systemctl enable sshd.service
<br>

#### Firewall
 
    # sudo pacman -S gufw
    # sudo ufw enable
    # sudo systemctl enable ufw.service
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
    # sudo systemctl disable dhcpcd
<br>

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
