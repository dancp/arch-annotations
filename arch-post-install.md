### Pós

**Habilitar suporte 32-bits**

    # nano /etc/pacman.conf
    
    [multilib]
    Include = /etc/pacman.d/mirrorlist
<br>

**Xorg**

    # pacman -S xorg
<br>

**Nvidia**

    # nvidia-390xx nvidia-390xx-utils lib32-nvidia-390xx-utils nvidia-390xx-settings
<br>

**Som**

    # alsa-utils alsa-lib alsa-oss pulseaudio pulseaudio-alsa lib32-libpulse lib32-alsa-plugins
<br>

**KDE Plasma**

    # pacman -S plasma kde-applications
    ou
    # pacman -S plasma-desktop kdebase
    ou
    # pacman -S plasma-desktop dolphin konsole
    # ark gwenview spectacle kate okular kcalc
    # kde-gtk-config kinfocenter plasma-pa user-manager polkit-kde-agent kdialog plasma-nm kwallet kwallet-pam kwalletmanager
    # kolourpaint kruler kget kdf kfind kdeconnect discover
<br>

**Display Manager**

    # pacman -S sddm sddm-kcm
    # systemctl enable sddm.service
<br>

**Network Manager** (Opcional)

    # systemctl enable NetworkManager.service
    
    /etc/NetworkManager/conf.d/dhcp-client.conf

    [main]
    dhcp=dhclient
<br><br>

### Extras

**Geral**

    # pacman -S xdg-user-dirs pacman-contrib fakeroot jshon expac git wget networkmanager-openvpn
    # pacman -S gimp telegram-desktop wine qbittorrent firefox libreoffice latte-dock wine
<br>

**Openshh**

    # pacman -S openssh
    # systemctl enable sshd.service

 **Firewall**
 
    # pacman -S gufw
    # ufw enable
    # systemctl enable ufw.service
<br>

 **Steam**
 
    # pacman -S steam  lib32-libpulse lib32-libxtst libxfixes lib32-libxrandr lib32-glib2 lib32-gtk2 lib32-gdk-pixbuf2 lib32-openal
<br>

 **Yay**
 
    # git clone https://aur.archlinux.org/yay.git
    # cd yay
    # makepkg -si
<br>

 **Fonts**
 
    # pacman -S noto-fonts ttf-ubuntu-font-family ttf-dejavu ttf-freefont ttf-liberation ttf-droid ttf-inconsolata ttf-roboto terminus-font ttf-font-awesome
<br>

  **pulseeffects**
  
    # pacman -S pavucontrol-qt pulseeffects boost-libs glibmm gst-plugins-bad gst-plugins-good gstreamer gtk3 gtkmm3 libebur128 libpulse libsamplerate libsigc++ libsndfile lilv zita-convolver calf lsp-plugins mda.lv2 rubberband zam-plugins appstream-glib boost itstool meson
<br>

  **Codecs**

    # pacman -S --needed a52dec faac faad2 flac jasper lame libdca libdv libmad libmpeg2 libtheora libvorbis libxv wavpack x264 xvidcore 
    # pacman -S --needed opencl-nvidia lib32-opencl-nvidia lib32-libvdpau libva-vdpau-driver mesa-vdpau lib32-mesa-vdpau
    # pacman -S --needed gst-{plugins-{bad,ugly},libav} libdvdcss libquicktime mencoder x264 lib32-gst-plugins-{base,good}
    # pacman -S --needed ttf-{croscore,roboto,ubuntu-font-family} wqy-zenhei otf-{font-awesome,fira-sans,fira-code}
<br>

fstab

    # <file system> <dir> <type> <options> <dump> <pass>
    # UUID=fed816ab-65fd-4fbe-b4e0-c4443224cc7f
    /dev/sda4               /               ext4            rw,relatime     0 1
    #UUID=62F90749644D8BBC
    /dev/sda3       /run/media/dancp/Files/ ntfs    defaults        0       0

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Pós Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-post-install.md)
- [Melhorias](https://github.com/dancp/arch-annotations/blob/master/tweaks.md)
