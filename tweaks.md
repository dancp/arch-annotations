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

#### Salvar configurações do alsamixer

    # sudo alsactl store

<br>

#### Firefox

```
  new string
    widget.content.gtk-theme-override
  value=Arc
```
    /home/dancp/.mozilla/firefox/???.default-release
    chrome/userChrome.css
  
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

#### KDE Plasma Volume Fix

    *modify* /usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/osd/Osd.qml

```
import QtQuick 2.0
import QtQuick.Window 2.2
import org.kde.plasma.core 2.0 as PlasmaCore
import org.kde.plasma.components 2.0 as PlasmaComponents
import org.kde.plasma.extras 2.0 as PlasmaExtra

PlasmaCore.Dialog {
    id: root
    location: PlasmaCore.Types.Floating
    type: PlasmaCore.Dialog.OnScreenDisplay
    outputOnly: true

    flags: Qt.X11BypassWindowManagerHint | Qt.FramelessWindowHint
    x: Screen.width - width - Math.round(Screen.height/25*(1+((Screen.width/Screen.height-1)*0.5)))
    y: Math.round(Screen.height/25)


    property int timeout: 1800
    property var osdValue
    property string icon
    property bool showingProgress: false
    property bool animateOpacity: false

    Behavior on opacity {
        SequentialAnimation {
            PauseAnimation { duration: 100 }
            NumberAnimation {
                duration: root.timeout
                easing.type: Easing.InQuad
            }
        }
        enabled: root.animateOpacity
    }

    mainItem: OsdItem {
        rootItem: root
    }
}
```

    *modify* /usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/osd/OsdItem.qml

```
import QtQuick 2.0
import org.kde.plasma.core 2.0 as PlasmaCore
import org.kde.plasma.components 2.0 as PlasmaComponents
import org.kde.plasma.extras 2.0 as PlasmaExtra
import QtQuick.Window 2.2

Item {
    property QtObject rootItem
    property int iconWidth: units.iconSizes.medium
    property int progressBarWidth: Math.round(Screen.width/1000)*100
    height: iconWidth
    width: iconWidth*2 + progressBarWidth + Math.round(Screen.width/1000)*4

    PlasmaCore.IconItem {
        id: icon
        height: parent.height
        width: iconWidth
        source: rootItem.icon
    }

    PlasmaComponents.ProgressBar {
        id: progressBar
        width: progressBarWidth
        height: parent.height
        x: iconWidth
        visible: rootItem.showingProgress
        minimumValue: 0
        maximumValue: 100
        value: Number(rootItem.osdValue)
    }

    PlasmaExtra.Heading {
        id: label
        height: parent.height
        width: rootItem.showingProgress ? iconWidth + Math.round(Screen.width/1000)*4 : progressBarWidth  + iconWidth
        x: rootItem.showingProgress ? iconWidth + progressBarWidth : iconWidth
        visible: true
        text: rootItem.showingProgress ? rootItem.osdValue : (rootItem.osdValue ? rootItem.osdValue : "")
        horizontalAlignment: Text.AlignHCenter
        maximumLineCount: 1
        elide: Text.ElideLeft
        minimumPointSize: theme.defaultFont.pointSize
        fontSizeMode: Text.HorizontalFit
    }
}
```
<br>

#### Arch mirrorlist

    /etc/pacman.d/mirrorlist

    https://www.archlinux.org/mirrorlist/
    
    ## Brazil
    Server = http://br.mirror.archlinux-br.org/$repo/os/$arch             (23 ms)
    Server = http://linorg.usp.br/archlinux/$repo/os/$arch                (29 ms)
    Server = http://www.caco.ic.unicamp.br/archlinux/$repo/os/$arch       (31 ms)
    Server = http://mirror.ufscar.br/archlinux/$repo/os/$arch             (34 ms)
    Server = http://archlinux.c3sl.ufpr.br/$repo/os/$arch                 (35 ms)
    Server = http://archlinux.pop-es.rnp.br/$repo/os/$arch                (35 ms)
    Server = http://pet.inf.ufsc.br/mirrors/archlinux/$repo/os/$arch      (41 ms)
    Server = http://mirror.ufam.edu.br/archlinux/$repo/os/$arch           (83 ms)
<br>

#### fstab

    # <file system> <dir> <type> <options> <dump> <pass>
    # UUID=fed816ab-65fd-4fbe-b4e0-c4443224cc7f
    /dev/sda4               /               ext4            rw,relatime     0 1
    # UUID=62F90749644D8BBC
    /dev/sda3       /run/media/dancp/Files/ ntfs    defaults        0       0
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

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Pós Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-post-install.md)
