## Índice

1. [Pós Instalação](#pós-instalação)
    - [Suporte 32-bits](#suporte-32-bits)
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

#### Suporte 32-bits

    # sudo nano /etc/pacman.conf
    
    [multilib]
    Include = /etc/pacman.d/mirrorlist
    
    # sudo pacman -Sy
<br>

#### Pré

    # sudo pacman -S --needed base-devel git openssh unzip unrar wget reflector
<br>

#### Packages

    # git clone https://github.com/dancp/arch-annotations.git
    # sudo pacman -S --needed - < pkglist.txt
<br>

#### Interface Gráfica

    # sudo pacman -S xorg xorg-xinit
    # sudo pacman -S --needed xf86-video-amdgpu mesa lib32-mesa mesa-vdpau lib32-mesa-vdpau libva-mesa-driver lib32-libva-mesa-driver libva-vdpau-driver lib32-libva-vdpau-driver vulkan-radeon lib32-vulkan-radeon vkd3d lib32-vkd3d
    # sudo pacman -S --needed plasma
<br>

#### Som

    # sudo pacman -S --needed alsa-plugins alsa-oss pipewire lib32-pipewire pipewire-alsa pipewire-pulse libpulse lib32-libpulse easyeffects
<br>

#### Codecs

    # sudo pacman -S --needed ffmpeg gst-libav gst-plugins-good gst-plugins-ugly gst-plugins-bad flac wavpack celt lame a52dec libdca libmad libmpcdec opencore-amr opus speex libvorbis faac faad2 libfdk-aac
    # sudo pacman -S --needed jasper libwebp libavif libheif
    # sudo pacman -S --needed aom dav1d rav1e svt-av1 libde265 libdv libmpeg2 schroedinger libtheora x264 x265 xvidcore
<br>

#### Fonts

    # sudo pacman -S --needed freetype2 noto-fonts noto-fonts-emoji noto-fonts-cjk awesome-terminal-fonts tex-gyre-fonts gnu-free-fonts dina-font tamsyn-font terminus-font cantarell-fonts inter-font bdf-unifont adobe-source-code-pro-fonts adobe-source-sans-fonts gentium-plus-font ttf-bitstream-vera ttf-croscore ttf-dejavu ttf-droid ttf-ibm-plex ttf-liberation ttf-linux-libertine ttf-roboto ttf-ubuntu-font-family ttf-anonymous-pro ttf-cascadia-code ttf-fantasque-sans-mono otf-fantasque-sans-mono ttf-fira-mono otf-fira-mono otf-fira-sans ttf-fira-code ttf-hack otf-hermit ttf-inconsolata ttc-iosevka ttf-jetbrains-mono ttf-monofur ttf-opensans ttf-junicode ttf-joypixels ttf-caladea ttf-carlito ttf-cormorant ttf-eurof ttf-font-awesome ttf-freefont ttf-indic-otf ttf-lato ttf-proggy-clean
<br>

#### Extras

    # sudo pacman -S --needed telegram-desktop firefox chromium latte-dock gparted qbittorrent gimp inkscape kdenlive krita libreoffice mpv code atom audacity zsh ufw ufw-extras appmenu-gtk-module htop flatpak
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
