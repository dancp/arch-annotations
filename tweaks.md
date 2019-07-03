**Arc Theme**
 
    # pacman -S kvantum-qt5 arc-kde kvantum-theme-arc arc-gtk-theme papirus-icon-theme
<br>

**Zsh**
 
    # pacman -S zsh
    # chsh -l
    # chsh -s full-path-to-shell
<br>
 
**Oh My Zsh**
 
    # sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
<br>

**Plugins**
zsh-syntax-highlight zsh-autosuggestions

    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

    source ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
    source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
<br>

**Wallpapers**
  
    # ln -s $HOME/Pictures/Wallpapers $HOME/.local/share/wallpapers
<br>

**Relógio/Dual boot W10**
 
    # timedatectl set-local-rtc 1 --adjust-system-clock
<br>

**Firefox**

    /home/??/.mozilla/firefox/??
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

**KDE Plasma Volume Fix**

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
