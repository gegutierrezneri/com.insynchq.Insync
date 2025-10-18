# Insync Flatpak

This is an experimental community flatpak recipe.
This is working as of October 2025 with Insync v3.9.6.60027

## Pre-requisites for Steamdeck

If you do not want to disable  read-only mode, you also need to install 2 additional flatpaks from flathub before building this local flatpak.

```
flatpak install flathub org.flatpak.Builder
flatpak install flathub org.freedesktop.Sdk/x86_64/24.08
```

## Building

```
flatpak run org.flatpak.Builder build-dir --user --ccache --force-clean --install com.insynchq.Insync.yml
```

Then you can run it via the command line:

```
flatpak run com.insynchq.Insync
```

or just search for the installed app on your system

## Known problems

- The tray icon isn't using the correct icons and falls back to three dots
- Autostart set from within insync does not work you can use the following config in ~/.config/autostart/insync.desktop instead:

```
[Desktop Entry]
Type=Application
Name=com.insynchq.Insync
X-XDP-Autostart=com.insynchq.Insync
Exec=flatpak run com.insynchq.Insync
X-Flatpak=com.insynchq.Insync
X-GNOME-Autostart-Delay=3
```
