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

    # sudo pacman -S --needed base-devel git openssh unzip unrar p7zip wget reflector
<br>

#### Packages

    # git clone https://github.com/dancp/arch-annotations.git
    # sudo pacman -S --needed - < pkglist.txt
<br>

#### Interface Gráfica

    # sudo pacman -S --needed xorg xorg-xinit
    # sudo pacman -S --needed xf86-video-amdgpu mesa lib32-mesa mesa-vdpau lib32-mesa-vdpau libva lib32-libva libva-mesa-driver lib32-libva-mesa-driver opencl-mesa lib32-opencl-mesa libva-vdpau-driver lib32-libva-vdpau-driver vulkan-radeon lib32-vulkan-radeon vkd3d lib32-vkd3d
    # sudo pacman -S --needed plasma qt5 kde-system kde-utilities kde-multimedia kde-graphics kde-accessibility dolphin-plugins kdeconnect appmenu-gtk-module
<br>

#### Som

    # sudo pacman -S --needed alsa-plugins lib32-alsa-plugins alsa-oss lib32-alsa-oss pipewire lib32-pipewire pipewire-alsa pipewire-pulse libpulse lib32-libpulse easyeffects
<br>

#### Codecs

    # sudo pacman -S --needed ffmpeg gst-libav gstreamer lib32-gstreamer lib32-gst-plugins-base lib32-gst-plugins-base-libs gst-plugins-good gst-plugins-ugly gst-plugins-bad flac lib32-flac wavpack celt lib32-celt lame a52dec libdca libmad libmpcdec opencore-amr opus speex libvorbis faac faad2 libfdk-aac
    # sudo pacman -S --needed jasper libwebp libavif libheif
    # sudo pacman -S --needed aom dav1d rav1e svt-av1 libde265 libdv libmpeg2 schroedinger libtheora lib32-libtheora x264 x265 xvidcore
<br>

#### Fonts

    # sudo pacman -S --needed fontconfig lib32-fontconfig freetype2 lib32-freetype2 noto-fonts noto-fonts-emoji noto-fonts-cjk awesome-terminal-fonts tex-gyre-fonts gnu-free-fonts dina-font tamsyn-font terminus-font cantarell-fonts inter-font bdf-unifont adobe-source-code-pro-fonts adobe-source-sans-fonts gentium-plus-font ttf-bitstream-vera ttf-croscore ttf-dejavu ttf-droid ttf-ibm-plex ttf-liberation ttf-linux-libertine ttf-roboto ttf-ubuntu-font-family ttf-anonymous-pro ttf-cascadia-code ttf-fantasque-sans-mono otf-fantasque-sans-mono ttf-fira-mono otf-fira-mono otf-fira-sans ttf-fira-code ttf-hack otf-hermit ttf-inconsolata ttc-iosevka ttf-jetbrains-mono ttf-monofur ttf-opensans ttf-junicode ttf-joypixels ttf-caladea ttf-carlito ttf-cormorant ttf-eurof ttf-font-awesome ttf-freefont ttf-indic-otf ttf-lato ttf-proggy-clean
<br>

#### Extras

    # sudo pacman -S --needed telegram-desktop firefox chromium latte-dock gparted qbittorrent gimp inkscape kdenlive krita libreoffice mpv code atom audacity flatpak obs-studio simplescreenrecorder lib32-simplescreenrecorder
    # sudo pacman -S --needed htop zsh libusb lib32-libusb ldns nfs-utils sshfs
<br>

#### Display Manager
    # sudo pacman -S --needed sddm sddm-kcm
    # sudo systemctl enable sddm.service
<br>

#### Network Manager
    # sudo pacman -S --needed networkmanager openvpn networkmanager-openvpn
    # sudo systemctl enable NetworkManager.service
    # sudo systemctl disable dhcpcd
<br>

#### Openssh
    # sudo pacman -S --needed openssh
    # sudo systemctl enable sshd.service
<br>

#### Firewall
 
    # sudo pacman -S --needed ufw ufw-extras
    # sudo systemctl enable ufw.service
    # sudo ufw enable
```
Basic Config
# sudo ufw default deny
# sudo ufw allow from 192.168.0.0/24
# sudo ufw limit SSH
```
```
KDEConnect
# sudo ufw allow 1714:1764/udp
# sudo ufw allow 1714:1764/tcp
# sudo ufw reload
```
<br>

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
