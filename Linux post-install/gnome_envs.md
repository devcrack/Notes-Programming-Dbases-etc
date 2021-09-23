# Post installation Gnome Environtments 
<br>
This was done in GNOME Shell 3.38.4

## Installing themes 
[Installing Themes on GNOME](https://itsfoss.com/install-switch-themes-gnome-shell/)

## Force alt + tab to switch only on current workspace in GNOME shell

Very fast & easy, without any installations/extensions:

1. Install dconf-editor (already installed on current debian/ubuntu distributions):

```sudo apt-get install dconf-editor```

2. Open dconf-editor (from the Dash or a Terminal)

3. Navigate to: org -> gnome -> shell -> app-switcher
Set "current-workspace-only" to true

4. Set "current-workspace-only" to true

## Where are the stored the default background system pictures
Usually are stored in: /usr/share/backgrounds

## Automatically Change Wallpaper Periodically
- [Desk Changer Gnome Extension](https://extensions.gnome.org/extension/1131/desk-changer/)

- A good post about this: [4 ways of periodically change the wallpapers in linux](https://ubuntuhandbook.org/index.php/2018/07/4-wallpaper-changer-ubuntu-18-04/)

<br>
<br>

## Linux Spotify KeyBindings

1. Install xbindkeys: ```sudo apt install xbindkeys```
2. Create the default configuration file for xbindkeys: 
```xbindkeys --defaults > ~/.xbindkeysrc```
3. Edit the file recently created
```nano ~/.xbindkeysrc```
4. My spotify configuration:

```
# Spotify Config

# Play / Pause
"dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlayPause"
Control + Shift + Up

# Next Song
"dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Next"
Control + Shift + Right

# Previous Song
"dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Previous"
Control + Shift + Left
##################################
```

Other usefull resources about this:
- [KeyBindings spotify in linux](https://shkspr.mobi/blog/2011/12/linux-spotify-keybindings/)
- [Some keybindings](https://pastebin.com/i1YfDLY6)
- [How use Arrow Keys in XbindKeys](https://gist.github.com/mbergmanpga/c07c37a3d8da7c285060b714e01a5ee7)
- [What are the MOD Keys](https://askubuntu.com/questions/120928/what-is-the-mod4d-shortcut-key)



