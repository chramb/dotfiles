# Directories needed
```
~/.local/bin/ <- to ln nvim -> vim
~/.local/share/icons
~/.local/share/fonts
```
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
  - Gnome
  - GSConnect
  - Multi-Account Containers

# Other Packages
## DNF
```
sudo dnf in neovim papirus-icon-theme gnome-console
```
