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


#### Habilitar suporte 32-bits

    # nano /etc/pacman.conf
    
    [multilib]
    Include = /etc/pacman.d/mirrorlist
<br>

#### Display Manager

    # pacman -S sddm sddm-kcm
    # systemctl enable sddm.service
<br>

#### Network Manager

    # pacman -S dhclient
    
    /etc/NetworkManager/conf.d/dhcp-client.conf
    [main]
    dhcp=dhcpcd
    
    # systemctl enable NetworkManager.service
<br><br>

## Extras

#### Openssh

    # pacman -S openssh
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

#### Pulse Effects
  
    # pacman -S pulseeffects pavucontrol-qt
    # pacman -S --needed boost-libs glibmm gst-plugins-bad gst-plugins-good gstreamer gtk3 gtkmm3 libebur128 libpulse libsamplerate libsigc++ libsndfile lilv zita-convolver calf lsp-plugins mda.lv2 rubberband zam-plugins appstream-glib boost itstool meson
<br>

#### Internet
    # systemctl disable dhcpcd
<br>

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
