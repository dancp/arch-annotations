**Habilitar suporte 32-bits**

    # nano /etc/pacman.conf
    [multilib]
    Include = /etc/pacman.d/mirrorlist

**Xorg**

    # pacman -S xorg

**Nvidia**

    # nvidia-390xx nvidia-390xx-utils lib32-nvidia-390xx-utils nvidia-390xx-settings

**Som**

    # alsa-utils alsa-lib alsa-oss pulseaudio pulseaudio-alsa lib32-libpulse lib32-alsa-plugins

**KDE Plasma**

    # pacman -S plasma kde-applications
    ou
    # pacman -S plasma-desktop kdebase
    ou
    # pacman -S plasma-desktop dolphin konsole
    # pacman -S ark gwenview spectacle kate okular kcalc
    # pacman -S kde-gtk-config kinfocenter plasma-pa user-manager polkit-kde-agent kdialog plasma-nm kwallet kwallet-pam kwalletmanager
    # pacman -S kolourpaint kruler kget kdf kfind kdeconnect discover

**Display Manager**

    # pacman -S sddm sddm-kcm
    # systemctl enable sddm.service

**Network Manager** (Opcional)

    # systemctl enable NetworkManager.service

**Extras**

    # pacman -S xdg-user-dirs pacman-contrib fakeroot jshon expac git wget openssh pavucontrol-qt pulseeffects

 **Codecs**
 
    # pacman -S a52dec faac faad2 flac jasper lame libdca libdv libmad libmpeg2 libtheora libvorbis libxv wavpack x264 xvidcore 

 **Firewall**
 
    # pacman -S gufw
    # ufw enable
    # systemctl enable ufw.service

 **Fonts**
 
    # pacman -S noto-fonts ttf-ubuntu-font-family ttf-dejavu ttf-freefont ttf-liberation ttf-droid ttf-inconsolata ttf-roboto terminus-font ttf-font-awesome

 **Steam**
 
    # pacman -S steam  lib32-libpulse lib32-libxtst libxfixes lib32-libxrandr lib32-glib2 lib32-gtk2 lib32-gdk-pixbuf2 lib32-openal

 **Yay**
 
    # git clone https://aur.archlinux.org/yay.git
    # cd yay
    # makepkg -si

 **Zsh**
 
    # pacman -S zsh
    # chsh -l
    # chsh -s full-path-to-shell
    
 **Oh My Zsh**
 
    # sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

 **Relógio/Dual boot W10**
 
    # timedatectl set-local-rtc 1 --adjust-system-clock

 **Arc Theme**
 
    # pacman -S kvantum-qt5 arc-kde kvantum-theme-arc arc-gtk-theme papirus-icon-theme

 **Geral**
 
    # pacman -S gimp telegram-desktop wine qbittorrent firefox libreoffice latte-dock
<br>

### Tweaks
 
  Wallpapers
  
    # ln -s $HOME/Pictures/Wallpapers $HOME/.local/share/wallpapers
    
  **Codecs**
  
    # pacman -S --needed opencl-nvidia lib32-opencl-nvidia lib32-libvdpau libva-vdpau-driver mesa-vdpau lib32-mesa-vdpau
    # pacman -S --needed gst-{plugins-{bad,ugly},libav} libdvdcss libquicktime mencoder x264 lib32-gst-plugins-{base,good}
    # pacman -S --needed ttf-{croscore,roboto,ubuntu-font-family} wqy-zenhei otf-{font-awesome,fira-sans,fira-code}

  **pulseeffects**
  
    # pacman -S boost-libs glibmm gst-plugins-bad gst-plugins-good gstreamer gtk3 gtkmm3 libebur128 libpulse libsamplerate libsigc++ libsndfile lilv zita-convolver calf lsp-plugins mda.lv2 rubberband zam-plugins appstream-glib boost itstool meson
