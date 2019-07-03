### Tweaks
 
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
