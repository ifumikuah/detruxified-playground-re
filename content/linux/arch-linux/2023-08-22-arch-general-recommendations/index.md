---
title: "General Recommendations : Desktop"
draft: false
weight: 2
---

Baru saja menginstall Arch Linux tapi bingung mau ngapain selanjutnya. You come into right page!, sebelum menginstall package, ada baiknya kamu mengetahui kebutuhan. Untuk apa Arch Linux ini kamu gunakan.

## Just for Learning &#x1F3EB;

Install KDE, GNOME atau Xfce untuk belajar.

{{< tabs "1" >}}
{{< tab "KDE" >}}
## KDE

UI Mirip Windows, very customisable, sangat cocok jika kamu seorang immigrant dari windows yang ingin pindah ke linux.

### Cons:
- Jika kamu mengalami gangguan seperti OCD, atau tidak suka melihat UI dengan buttom banyak yang berdempetan, maka cobalah untuk menahan diri.

Approx. memory usage: 500M+ at idle (fresh installation)

### Steps:
```plain
# pacman -S plasma plasma-wayland-session xorg-server
# systemctl enable sddm
```
Lalu reboot.
{{< /tab >}}
{{< tab "GNOME" >}}
## GNOME

UI Mirip minimalist mirip MacOS, but better, sangat cocok jika kamu pecinta minimalist dan pengguna MacOS.
### Cons:
- Pengaturan yang sangat terbatas.

Approx. memory usage: 800M+ at idle (fresh installation)
### Steps:
```plain
# pacman -S gnome gnome-tweaks gnome-extensions xorg-server
# systemctl enable gdm
```
Lalu reboot.
{{< /tab >}}
{{< tab "XFCE" >}}
## XFCE

UI Fleksibel, mirip MacOS tapi tidak juga bisa dibilang begitu, sangat cocok jika kamu menjalankan linux di device kentang.
### Cons:
- Karena sifatnya yang sangat hemat sumber daya, package yang digunakan juga tergantung "kuno" e.g. Hanya support Xorg.

Approx. memory usage: 200M+ at idle (fresh installation)
### Steps:
```plain
# pacman -S xfce4 xfce4-group xorg-server lightdm lightdm-gtk-greeter
# systemctl enable lightdm
```
Lalu reboot.
{{< /tab >}}
{{< /tabs >}}

## Start new hobby AKA ricing &#x1F359;

You probably know what you're doing rn. Terdapat dua jenis display server saat ini di linux.

{{< tabs "2" >}}
{{< tab "Xorg" >}}
## Xorg Display Server
Software sepuh, Server ini dikenal dengan latensi nya yang tinggi (kurang responsive, boros performa), kelebihan yang diunggulkan adalah just works, jika kamu lebih mementingkan stabilitas daripada performa, gunakan ini.

### WM yang menggunakan Xorg
Berikut adalah rekomendasi WM yang harus kamu coba dimulai dari yang termudah sampai tersulit.
- bspwm : Komunitas yang ramai, lebih modular
- i3 : Komunitasnya juga ramai, agak kurang modular (fine level, still good tho).
- openbox : Floating tiling, ini artinya kamu selalu dalam mode floating windows.
- dwm : hyper-minimalistic, bahkan kamu harus build from source untuk rekonfigurasi.
{{< /tab >}}
{{< tab "Wayland" >}}
## Wayland Compositor
Saya akan menanggap kamu sudah mengerti basic Window Manager jika ingin menggunakan Wayland.

Pendatang sekaligus penerus sepuh, Memiliki latensi yang rendah dan lebih responsive, hemat performa. Namun kelemahan yang ada di Wayland adalah ibarat teknologi experimental, things likely to breaks.

### WM yang menggunakan Wayland
Saya rekomendasikan menggunakan dua kompositor ini secara berurut jika ingin belajar Wayland.
- sway : jika mahir i3, 100% kamu bisa menggunakan ini juga.
- hyprland : Eye Candies!!, compositor dengan visual effects terbaik dan terkeren imo.
{{< /tab >}}
{{< /tabs >}}

## Headless Server &#x1F4BB;

Kamu mungkin hanya ingin menggunakan Arch sebagai server. Install `openssh` lalu konfigurasi SSH di : 
```
/etc/ssh/sshd_config
```
`PermitRootlogin yes` dan `PasswordAuthentication yes` untuk mengizinkan root untuk login.

Sebelumnya, kamu harus tahu IP yang digunakan Arch tersebut untuk login, lalu:

```plain
ssh user_name@ip_address
```

Jika kamu memasang port lain untuk SSH, tambahkan parameter `-p` untuk port yang ingin dituju. Port default adalah 22.

## Hanya ingin menggunakan untuk kebutuhan sehari-hari &#x1F468;

Gunakan KDE jika kamu tidak terlalu peduli, KDE merupakan Desktop yang terlalu general sehingga bisa digunakan untuk apapun dan lumayan fleksibel.