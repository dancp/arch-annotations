## Índice

1. [Melhorias](#melhorias)
   - [Oh My Zsh](#oh-my-zsh)
   - [Zsh plugins](#zsh-plugins)
   - [Cor no pacman](#cor-no-pacman)
   - [Nano Syntax Highlighting](#nano-syntax-highlighting)
   - [Pasta de Wallpapers](#pasta-de-wallpapers)
   - [Relógio/Dual boot W10](#relógio-dual-boot-w10)
   - [Salvar configurações do alsamixer](#salvar-configurações-do-alsamixer)

- [Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-install.md)
- [Pós Instalação](https://github.com/dancp/arch-anotations/blob/master/arch-post-install.md)
<br>

## Melhorias

#### Oh My Zsh
 
    # sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
<br>

#### Zsh plugins

    # git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    # git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

    source ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
    source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
<br>

#### Configurações do pacman

    # sudo nano /etc/pacman.conf
<br>

#### Nano Syntax Highlighting

    # curl https://raw.githubusercontent.com/scopatz/nanorc/master/install.sh | sh
<br>

#### Linkar pasta de Wallpapers
  
    # ln -s $HOME/Pictures/Wallpapers $HOME/.local/share/wallpapers
<br>

#### Relógio/Dual boot W10
 
    # timedatectl set-local-rtc 1 --adjust-system-clock
<br>

#### Habilitar modo no pavucontrol 

    # sudo nano /etc/pulse/default.pa
    # load-module module-device-manager
    
    pulseeffects --gapplication-service &>/dev/null
<br>

#### Salvar configurações do alsamixer

    # sudo alsactl store
<br>

#### Kate

    # --startanon
<br>

#### Firefox

    # userChrome - toolkit.legacyUserProfileCustomizations.stylesheets
    # Pocket - extensions.pocket.enabled
<br>

#### Font config

    # /etc/fonts/local.conf
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <alias>
    <family>sans-serif</family>
    <prefer>
      <family>Noto Sans</family>
      <family>Noto Color Emoji</family>
      <family>Noto Emoji</family>
      <family>DejaVu Sans</family>
    </prefer>
    </alias>
    <alias>
    <family>serif</family>
    <prefer>
      <family>Noto Serif</family>
      <family>Noto Color Emoji</family>
      <family>Noto Emoji</family>
      <family>DejaVu Serif</family>
    </prefer>
    </alias>
    <alias>
    <family>monospace</family>
    <prefer>
      <family>Noto Mono</family>
      <family>Noto Color Emoji</family>
      <family>Noto Emoji</family>
    </prefer>
  </alias>
</fontconfig> 
```
<br>

#### Polkit

    # /etc/polkit-1/rules.d/99-arch.rules
```
    polkit.addRule(function(action, subject) {
		if (action.id.indexOf("org.freedesktop.udisks2.") == 0 && subject.isInGroup("storage")) {
			return polkit.Result.YES;
		}
	}
);
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
