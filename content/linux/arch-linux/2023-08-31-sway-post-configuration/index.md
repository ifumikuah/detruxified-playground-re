---
title: Post-konfigurasi Sway
draft: false
weight: 3
---

Post-konfigurasi Arch Linux dengan spesifikasi:

| Facility | Progs |
|-|-|
|Graphical session|`sway`,`swaybg`,`xorg-xwayland`|
|Terminal|`foot`|
|Dual boot|`os-prober`|
|NTFS|`ntfs-3g`|
|Audio|`pipewire`,`wireplumber`,`pipewire-alsa`,`pipewire-pulse`,`alsa-utils`|
|Networking|`networkmanager`,`network-manager-applet`,`nm-connection-editor`|
|Polkit|`polkit`|
|Display Manager|`ly`|
|Bar/Panel|`waybar`|
|Menu utility|`wofi`|
|Equalizer|`easyeffects`,`lsp-plugins-noicons`,`calf`|
|Bluetooth|`bluez`,`bluez-utils`,`blueman`|

## Appearance/Visual

|Font|Purpose|
|-|-|
|Roboto|Entire display UI|
|JetBrains Mono|Codes|
|Twemoji(Twitter's emoji)|Emoji|
|Font Awesome 6|Icon fonts|
|Noto CJK|Asian typeface|

```bash
yay -S ttf-font-awesome ttf-roboto ttf-jetbrains-mono ttf-hanazono noto-fonts-cjk ttf-twemoji
```

## Getting started

Install semua yang ada di atas menggunakan `yay`, lalu clone repo dotfiles.

Sesudah diclone, jangan dulu copy-paste semuanya.

### Polkit

Biasanya `polkit` sudah hidup sedari `sway` diinstall, cek dengan:
```bash
systemctl status polkit
```
Jika belum, hidupkan dengan:
```bash
sudo systemctl enable --now polkit
```

### Audio 

{{< highlight bash "linenos=table" >}}
systemctl --user --now enable pipewire
systemctl --user --now enable pipewire-pulse
systemctl --user --now enable wireplumber
{{< /highlight >}}

### Brightnessctl

Copy dibawah ini ke `/etc/udev/rules.d/backlight.rules`:
```plain
RUN+="/bin/chgrp video /sys/class/backlight/intel_backlight/brightness"
RUN+="/bin/chmod g+w /sys/class/backlight/intel_backlight/brightness"
```

Tambah user ke group `video`:
```bash
sudo usermod -aG video your_user
```
Perlu relog/restart untuk melihat effectnya.

### Environment Variables

```bash
export MOZ_ENABLE_WAYLAND=1
export PATH="${PATH}:/home/detrux/bin"
export LIBVA_DRIVER_NAME=i965
export QT_QPA_PLATFORMTHEME=qt5ct 
```

### Bluetooth

Hidupkan service bluetooth:
```bash
sudo systemctl enable --now bluetooth
```

### Display Manager

```bash
sudo systemctl enable ly
```
Ly akan langsung dimulai di *tty2*, disarankan lakukan konfig ly ini belakangan.

## Important

Di git dotfiles, jangan lupa ubah PATH /user sesudah /home menjadi nama username kamu.
Misal:
```plain
.../home/muhfad/.config/blah
```
menjadi
```plain
.../home/jamalsniper/.config/blah
```

