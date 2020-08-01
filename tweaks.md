## Índice

1. [Melhorias](#melhorias)
   - [Arc Theme](#arc-theme)
   - [Zsh](#zsh)
   - [Oh My Zsh](#oh-my-zsh)
   - [Zsh plugins](#zsh-plugins)
   - [Cor no pacman](#cor-no-pacman)
   - [Nano Syntax Highlighting](#nano-syntax-highlighting)
   - [Pasta de Wallpapers](#pasta-de-wallpapers)
   - [Relógio/Dual boot W10](#relógio-dual-boot-w10)
   - [Salvar configurações do alsamixer](#salvar-configurações-do-alsamixer)
   - [Firefox](#firefox)
   - [KDE Plasma Volume Fix](#kde-plasma-volume-fix)
   - [Arch mirrorlist](#arch-mirrorlist)
   - [fstab](#fstab)

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Pós Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-post-install.md)
<br>

## Melhorias

#### Arc Theme
 
    # pacman -S kvantum-qt5 arc-kde kvantum-theme-arc arc-gtk-theme papirus-icon-theme
<br>

#### Zsh
 
    # pacman -S zsh
    # chsh -l
    # chsh -s full-path-to-shell
<br>
 
#### Oh My Zsh
 
    # sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
<br>

#### Zsh plugins
zsh-syntax-highlight & zsh-autosuggestions

    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

    source ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
    source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
<br>

#### Cor no pacman
    Color
    # /etc/pacman.conf
<br>

#### Nano Syntax Highlighting
    # curl https://raw.githubusercontent.com/scopatz/nanorc/master/install.sh | sh
<br>

#### Pasta de Wallpapers
  
    # ln -s $HOME/Pictures/Wallpapers $HOME/.local/share/wallpapers
<br>

#### Relógio/Dual boot W10
 
    # timedatectl set-local-rtc 1 --adjust-system-clock
<br>

#### Pulse Effects Tweaks 

    /etc/pulse/default.pa
    load-module module-device-manager
    
    pulseeffects --gapplication-service &>/dev/null
<br>

#### Salvar configurações do alsamixer

    # sudo alsactl store

<br>

#### Firefox
```
Right click the Firefox launcher in the app launcher > Edit Application
Application tab > Command
   GTK_USE_PORTAL=1 /usr/lib/firefox/firefox %u
```

```
  new string
    widget.content.gtk-theme-override
  value=Arc
```
    /home/dancp/.mozilla/firefox/???.default-release
    chrome/userChrome.css
    
    toolkit.legacyUserProfileCustomizations.stylesheets  
```
#PersonalToolbar
{
    opacity:0 !important;
    margin-top: -23px !important;
    transition: all 0.4s ease 0s !important;
    }

#navigator-toolbox:hover > #PersonalToolbar
{
    visibility: visible !important;
    margin-top: 0px !important;
    transition: all 0.4s ease 0s !important;
    opacity: 1 !important;
    }
 ```
<br>

#### Mudar nome de partição

    lsblk -o NAME,SIZE,LABEL

  ext2/3/4 (e2fsprogs)
  
    e2label /dev/sdXX new_label
    
  ntfs (ntfs-3g)
  
    ntfslabel /dev/sdXX new_label
    
  swap (util-linux)
  
    swaplabel -L new_label /dev/sdXX
    
  fat/vfat (dosfstools)
  
    fatlabel /dev/sdXX new_label
    
  btrfs (btrfs-progs)
  
    btrfs filesystem label /dev/sdXX new_label 
<br>

kvm
https://blog.programster.org/kvm-missing-default-network
<br>

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Pós Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-post-install.md)
