### Tweaks
 
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
