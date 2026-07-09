# sairex bspwm rice for arch linux

A compact, opinionated bspwm "rice" configuration tailored for a dark Catppuccin-like aesthetic. This repository contains a full desktop setup: window manager, hotkeys, status bar, rofi themes, terminal configs and a fastfetch profile.

## Overview
![See](wallpapers/image.png)

- Window manager: `bspwm` (tiling, lightweight)
- Hotkeys: `sxhkd` (keybindings and app launcher)
- Bar: `polybar` with a custom theme and launch script
- App launcher: `rofi` with a Catppuccin theme
- Terminals: `alacritty` and `kitty` configs included
- Fastfetch config for presenting system info
- Wallpapers folder with system images

## Features

- Dark Catppuccin-inspired colors across components
- Preconfigured `polybar` modules (workspaces, battery, cpu, network)
- Handy `sxhkd` shortcuts for common apps and bspwm controls
- Autostart entries in `bspwm/bspwmrc` (polybar, dunst, nitrogen, sxhkd, etc.)
- `fastfetch` profile for attractive system info output

## Repository structure

- [bspwm](bspwm) — `bspwm` config and autostart (`bspwm/bspwmrc`)
- [sxhkd](sxhkd) — keybindings (`sxhkd/sxhkdrc`, `sxhkd/sxhkdrc.openbox`)
- [polybar](polybar) — `polybar` configs and `launch.sh` script
- [alacritty](alacritty) — `alacritty` terminal settings
- [kitty](kitty) — `kitty` terminal settings
- [rofi](rofi) — `rofi` themes (`config.rasi`, `catppuccin.rasi`)
- [fastfetch](fastfetch) — `fastfetch` config and README
- [wallpapers](wallpapers) — image assets

## Important files

- [bspwm/bspwmrc](bspwm/bspwmrc) — main bspwm autostart and rules
- [sxhkd/sxhkdrc](sxhkd/sxhkdrc) — primary keybindings (see comments)
- [polybar/launch.sh](polybar/launch.sh) — launches polybar for single/multi-monitor
- [polybar/config.ini](polybar/config.ini) and [polybar/modules.ini](polybar/modules.ini)
- [rofi/config.rasi](rofi/config.rasi) and [rofi/catppuccin.rasi](rofi/catppuccin.rasi)
- [fastfetch/config.jsonc](fastfetch/config.jsonc) — fastfetch layout

## Requirements

Install these components (exact package names vary by distribution):

- bspwm
- sxhkd
- polybar
- rofi
- nitrogen (or your wallpaper setter)
- dunst (notifications)
- pulsemixer / pavucontrol (audio)
- flameshot (screenshots)
- fastfetch (system info)
- kitty and/or alacritty (terminals)

On Arch-based systems you can install many of these with pacman:

```bash
sudo pacman -S bspwm sxhkd polybar rofi nitrogen dunst pulsemixer pavucontrol flameshot fastfetch kitty alacritty
```

## Installation (safe, non-destructive)

1. Backup your current configs:

```bash
cp -r ~/.config/bspwm ~/.config/bspwm.bak
cp -r ~/.config/sxhkd ~/.config/sxhkd.bak
cp -r ~/.config/polybar ~/.config/polybar.bak
```

2. Copy this repo's folders to your `~/.config/` (example):

```bash
mkdir -p ~/.config
cp -r bspwm sxhkd polybar rofi alacritty kitty fastfetch ~/.config/
```

3. Ensure `sxhkd` and required services are started. You can add to your `.xinitrc` or display manager session:

```bash
# example .xinitrc snippet
sxhkd &
~/.config/polybar/launch.sh &
nitrogen --restore &
dunst &
exec bspwm
```

4. Make `polybar/launch.sh` executable if needed:

```bash
chmod +x ~/.config/polybar/launch.sh
```

## Usage

- `sxhkd` contains many useful keybindings, including `super + Return` to open `kitty`, workspace navigation, screenshots and system actions. See [sxhkd/sxhkdrc](sxhkd/sxhkdrc).
- `bspwm` autostart (`bspwm/bspwmrc`) launches `sxhkd`, `polybar`, `nitrogen`, and other utilities by default.
- To manually launch polybar use the included script: `~/.config/polybar/launch.sh`.
- `fastfetch` can be run using `fastfetch -c ~/.config/fastfetch/config.jsonc`.

## Customization tips

- Change the colors for `polybar` in `polybar/colors.ini` (referenced from `polybar/config.ini`).
- Adjust `rofi` theme in `rofi/catppuccin.rasi` or switch `rofi/config.rasi` settings.
- Terminal preferences live in `alacritty/alacritty.toml` and `kitty/kitty.conf`.
- Window rules (floating apps, workspace assignments) are in `bspwm/bspwmrc`.
- Keybindings are in `sxhkd/sxhkdrc` — update shortcuts there.

## Notes & credits

- Some config headers mention author "Yusufbek" — original attributions are preserved in the files.
- I did not modify any configuration files; this README only documents and explains the existing setup.

## Want help?

If you want, I can:

- create an install script that copies files and sets permissions;
- add example `~/.xinitrc` or systemd user units to autostart components;
- generate screenshots and update README with visual previews.

Tell me which option you prefer and I will prepare it.
