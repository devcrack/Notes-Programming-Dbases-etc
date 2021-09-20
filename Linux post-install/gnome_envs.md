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