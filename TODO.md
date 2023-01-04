# Directories needed
```
~/.local/bin/ <- to ln nvim -> vim
~/.local/share/icons
~/.local/share/fonts
```
# Gnome
## Change Monospace font
> From: 'Source Code Pro 10'
```
gsettings set org.gnome.desktop.interface monospace-font-name 'FiraCode Nerd Font 10'
```
## Extensions installed
- AppIndicator and KStatusNotifierItem Support
- Bluetooth Quick Connect
- Compiz windows effect
- GSConnect

# Add cursor theme to flatpak
```
flatpak --user override --filesystem=/home/$USER/.icons/:ro
```

# Flatpak 
## Remove all flatpak remotes and add Flathub as user
```shell
flatpak remote-delete fedora 
flatpak remote-delete flathub
flatpak --user remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
# Firefox
## Remove firefox rpm and install from flathub
```shell
sudo dnf rm firefox -y
flatpak --user install  org.mozilla.firefox
flatpak --user override --socket=wayland --env=MOZ_ENABLE_WAYLAND=1 org.mozilla.firefox
```

## Firefox chagnges
- Change security to strict
- HTTPS-Only mode in all windows
- Dark theme
- Disable Built-in Password Manager
- Extensions:
  - Ublock Origin
  - Bitwarden
  - Multi-Account Containers
- Add security Exception for weechat relay cert
- Disable sponsored shortcuts

# DNF Repos
```
sudo rm /etc/yum.repos.d/{_copr_phracek-PyCharm,google-chrome,rpmfusion-nonfree-steam,rpmfusion-nonfree-nvidia-driver}.repo
sudo dnf in \
  https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
  https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf config-manager --add-repo https://pkgs.tailscale.com/stable/fedora/tailscale.repo
```
# Other Packages
## DNF
```
sudo dnf in neovim papirus-icon-theme gnome-console intel-media-driver \
    gh bat git-delta lsd duf tailscale @virtualization
sudo dnf rm rhythmbox totem gnome-{boxes,tour,text-editor}
```
