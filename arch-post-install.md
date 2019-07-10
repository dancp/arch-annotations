## Índice

1. [Pós Instalação](#pós-instalação)
    - [Iniciar conexão com a Internet](#iniciar-conexão-com-a-internet)
    - [Habilitar suporte 32-bits](#habilitar-suporte-32-bits)
    - [Xorg](#xorg)
    - [Nvidia](#nvidia)
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

#### Iniciar conexão com a Internet

    # systemctl start dhcpcd
<br>

#### Habilitar suporte 32-bits

    # nano /etc/pacman.conf
    
    [multilib]
    Include = /etc/pacman.d/mirrorlist
<br>

#### Xorg

    # pacman -S xorg
<br>

#### Nvidia

    # pacman -S nvidia-390xx nvidia-390xx-utils lib32-nvidia-390xx-utils nvidia-390xx-settings
<br>

#### Intel

    # pacman -S mesa lib32-mesa xf86-video-intel vulkan-intel

#### Som

    # pacman -S alsa-utils alsa-lib alsa-oss pulseaudio pulseaudio-alsa lib32-libpulse lib32-alsa-plugins
<br>

#### KDE Plasma

    # pacman -S plasma-desktop dolphin konsole
    # ark gwenview spectacle kate okular kcalc
    # kde-gtk-config kinfocenter plasma-pa user-manager polkit-kde-agent powerdevil
    # kdialog plasma-nm kwallet kwallet-pam kwalletmanager
    # kolourpaint kruler kget kdf kfind kdeconnect discover
<br>

#### Display Manager

    # pacman -S sddm sddm-kcm
    # systemctl enable sddm.service
<br>

#### Network Manager

    # pacman -S dhclient
    
    /etc/NetworkManager/conf.d/dhcp-client.conf
    [main]
    dhcp=dhclient
    
    # systemctl enable NetworkManager.service
<br><br>

## Extras

#### Geral

    # pacman -S xdg-user-dirs pacman-contrib jshon expac git wget networkmanager-openvpn
    # pacman -S gimp telegram-desktop qbittorrent firefox libreoffice latte-dock flameshot
    # pacman -S audacity flatpak
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

#### Fonts
 
    # pacman -S noto-fonts ttf-ubuntu-font-family ttf-dejavu ttf-freefont ttf-liberation ttf-droid ttf-inconsolata ttf-roboto terminus-font ttf-font-awesome
    # pacman -S --needed ttf-{croscore,roboto,ubuntu-font-family} wqy-zenhei otf-{font-awesome,fira-sans,fira-code}
<br>

#### Codecs

    # pacman -S --needed a52dec faac faad2 flac jasper lame libdca libdv libmad libmpeg2 libtheora libvorbis libxv wavpack x264 xvidcore 
    # pacman -S --needed opencl-nvidia390xx lib32-opencl-nvidia-390xx lib32-libvdpau libva-vdpau-driver mesa-vdpau lib32-mesa-vdpau
    # pacman -S --needed gst-{plugins-{bad,ugly},libav} libdvdcss libquicktime mencoder x264 lib32-gst-plugins-{base,good}
<br>

#### Pulse Effects
  
    # pacman -S pulseeffects pavucontrol-qt
    # pacman -S --needed boost-libs glibmm gst-plugins-bad gst-plugins-good gstreamer gtk3 gtkmm3 libebur128 libpulse libsamplerate libsigc++ libsndfile lilv zita-convolver calf lsp-plugins mda.lv2 rubberband zam-plugins appstream-glib boost itstool meson
    
    add to startup > pulseeffects --gapplication-service &>/dev/null
<br>

#### Openssh

    # pacman -S openssh
    # systemctl enable sshd.service
<br>

#### Yay
 
    # git clone https://aur.archlinux.org/yay.git
    # cd yay
    # makepkg -si
<br>

#### Wine

    # pacman -S wine wine_gecko wine-mono winetricks
<br>

#### Steam
 
    # pacman -S steam  lib32-libpulse lib32-libxtst libxfixes lib32-libxrandr lib32-glib2 lib32-gtk2 lib32-gdk-pixbuf2 lib32-openal
<br>

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
