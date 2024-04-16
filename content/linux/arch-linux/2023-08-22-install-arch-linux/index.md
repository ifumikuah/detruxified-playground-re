---
title: Instalasi Arch Linux
draft: false
weight: 1

resources:
    - name: partition-sizing
      src: "partition-sizing.png"
      title: Contoh partisi 7.5GB
---

{{< toc >}}

Arch Linux merupakan salah satu distro yang menawarkan minimalisme dan bleeding-edge. Arch merupakan rolling release distro, artinya package yang ada didalamnya selalu up-to date, kelemahannya adalah sistem sewaktu-waktu bisa rusak di saat yang tidak terduga.

## Persiapan

Sebelum menginstall, ada baiknya kamu mempersiapkan hal-hal seperti:
- Koneksi Internet (disarankan ethernet)
- Bootable Arch ISO tentunya

## Install

Jika kamu menggunakan ethernet, maka internet sudah ready to go, sebaliknya jika kamu menggunakan jaringan wireless maka harus konfigurasi wireless dulu.

### Wi-Fi

Cek nama device kamu dengan `ip link`, device wireless card biasanya punya nama berawalan "w", misal. `wlan0`,`wlp3s0`. Hidupkan device tersebut dengan `ip link set nama_device up`.

#### rfkill

Jika wireless card gagal hidup, maka ada dua kemungkinan soft-block atau hard-block.

- hard-block : cek apakah laptop kamu memiliki switch fisik untuk hidup-matikan wi-fi
- soft-blok : jalankan `rfkill unblock wlan` untuk unblock wi-fi

Disarankan, jalankan `rfkill` untuk mengecek status block wireless card.

#### iwctl

Gunakan `iwctl` untuk masuk ke mode shell interaktif iwd, lihat prompt kamu akan berubah menjadi `[iwd]#` maka kamu berada dalam shell interaktif iwd.

{{< highlight plain "linenos=table" >}}
[iwd]# station nama_device scan
[iwd]# station nama_device get-networks
[iwd]# station nama_device connect nama_ssid_jaringan_wifi
{{< /highlight >}}

Keluar dari iwd jika berhasil tersambung.

Satu langkah lagi, jalankan `dhcpcd nama_device` untuk mendapatkan IP DHCP. Cek internet kamu dengan `ping 8.8.8.8`

### Partisi

Cari disk yang ingin di install arch dengan `fdisk -l` atau `lsblk`. Disk biasanya memiliki nama seperti `/dev/sda`, `/dev/vda`, atau `/dev/nvme0n1`. Pada umumnya, jika kamu memiliki SSD atau HDD namanya `sda,sdb,sdc,...`, `vda,vdb,...` untuk disk virtual, dan `nvme0n1,nvme0n2,...` untuk NVMe.

Arch Linux menyarankan pakai `fdisk` untuk partisi disk, tapi ada cara lain yang lebih mudah yaitu dengan `cfdisk`. Cfdisk berbentuk seperti GUI sehingga kita bisa navigasi didalamnya.

#### Mengetahui firmware BIOS

Umumnya, ada dua jenis firmware BIOS, yaitu EFI dan MBR. Untuk mengecek apakah kamu pengguna EFI atau MBR, gunakan `fdisk`:

```plain
# fdisk -l /dev/sda
```

Lihat pada tulisan `disklabel`, jika `gpt` maka kamu pengguna EFI, jika `dos` maka kamu pengguna MBR

#### cfdisk

Normalnya struktur partisi yang standard adalah seperti berikut:

{{< tabs "1" >}}
{{< tab "EFI" >}}

| mount point | tipe partisi | details |
|-|-|-|
| `/boot` | EFI System | Partisi untuk menyimpan bootloader, disarankan 512MB |
| `[SWAP]` | Linux Swap | Partisi swap, disarankan 2GB+ |
| `/` | Linux Filesystem | Partisi root, pakai semua yang tersisa<sup>1</sup> |
| `/home` | Linux Filesystem | Partisi home (Optional), pakai semua yang tersisa<sup>1</sup> |

{{< /tab >}}
{{< tab "MBR" >}}

| mount point | tipe partisi | details |
|-|-|-|
| `[SWAP]` | Linux Swap | Partisi swap, disarankan 2GB+ |
| `/` | Linux Filesystem | Partisi root, pakai semua yang tersisa<sup>1</sup> |
| `/home` | Linux Filesystem | Partisi home (Optional), pakai semua yang tersisa<sup>1</sup> |

{{< /tab >}}
{{< /tabs >}}

<sup>[1]</sup> Jika kamu memakai `/home`, partisi root butuh kisaran 15-40GB untuk menyimpan sistem. Untuk disk 256GB setidaknya berikan root sebesar 30GB, untuk 1TB disk cukup butuh 60-100GB partisi root.

{{< hint type=important >}}

Untuk pengguna MBR, abaikan steps untuk `/boot` di tahap selanjutnya jika kamu menggunakan MBR

{{< /hint >}}

Jalankan perintah `cfdisk /dev/sda`, lalu atur partisi dengan acuan tabel diatas.

Jika kamu kebingungan untuk cara memberikan ukuran partisi, lihat pesan dibawah saat kamu disuruh input jumlah partisi, 512M untuk 512MB, 2G untuk 2GB, dan seterusnya.

{{< img name=partition-sizing >}}

Jangan lupa write dan quit jika sudah selesai.

#### Format partisi

Sesudah dipartisi, partisi yang baru saja dibuat harus diformat sebelum menginstall Arch didalamnya. Setiap partisi memiliki filesystem nya masing masing. Untuk kasus ini kita menggunakan ext4 sebagai filesystem utama.

Sebelum itu, kamu harus mengecek dimana partisi `/boot`,`/`,`swap`,dan `/home` menggunakan `lsblk`.

{{< tabs "4" >}}
{{< tab "EFI" >}}

Contoh:
| mount point | tipe partisi | letak |
|-|-|-|
| /boot | FAT32 | `/dev/sda1` |
| swap | Swap | `/dev/sda2` |
| / | ext4 | `/dev/sda3` |
| /home<sup>2</sup> | ext4 | `/dev/sda4` |

{{< /tab >}}
{{< tab "MBR" >}}

Contoh:
| mount point | tipe partisi | letak |
|-|-|-|
| swap | Swap | `/dev/sda2` |
| / | ext4 | `/dev/sda3` |
| /home<sup>2</sup> | ext4 | `/dev/sda4` |

{{< /tab >}}
{{< /tabs >}}

<sup>[2]</sup> Kamu tidak perlu format `/home` jika tidak memakainya

Untuk format partisi, ikuti perintah berikut secara berurutan:

{{< highlight plain "linenos=table" >}}
# mkfs.fat -F 32 /dev/sda1
# mkfs.ext4 /dev/sda3
# mkfs.ext4 /dev/sda4
{{< /highlight >}}

#### Swap

Aktifkan swap dengan:

{{< highlight plain "linenos=table" >}}
# mkswap /dev/sda2
# swapon /dev/sda2
{{< /highlight >}}

### Mount

Saatnya mount partisi root ke `/mnt` agar bisa menginstall Arch nantinya.

```plain
# mount /dev/sda3 /mnt
```

Buat `/mnt/boot` dan `/mnt/home` agar kamu bisa mount partisi boot dan home (jika pakai).

{{< highlight plain "linenos=table" >}}
# mkdir -p /mnt/boot
# mkdir -p /mnt/home
{{< /highlight >}}

Mount partisi tesrebut.

{{< highlight plain "linenos=table" >}}
# mount /dev/sda1 /mnt/boot
# mount /dev/sda4 /mnt/home
{{< /highlight >}}

Cek dengan `lsblk` atau `fdisk -l` dan pastikan semuanya sudah tepat. Sesuai tabel contoh tadi, partisi yang tepat akan seperti ini:

{{< tabs "2" >}}
{{< tab "EFI" >}}

| partition | mounted to |
|-----------|------------ |
| `/dev/sda1` | /mnt/boot |
| `/dev/sda2` | swap  |
| `/dev/sda3` | /mnt |
| `/dev/sda4` | /mnt/home |

{{< /tab >}}
{{< tab "MBR" >}}

| partition | mounted to |
|-----------|------------|
| `/dev/sda2` | swap  |
| `/dev/sda3` | /mnt |
| `/dev/sda4` | /mnt/home |

{{< /tab >}}
{{< /tabs >}}

### Install Arch

Install base Arch dan package yang diperlukan dengan:

```plain
# pacstrap -K /mnt base base-devel linux linux-firmware vim nano networkmanager wpa_supplicant grub man-db man-pages xdg-user-dirs
```
{{< hint type=important >}}

Untuk pengguna EFI, tambahkan package `efibootmgr` agar bisa booting dengan GRUB.

{{< /hint >}}

### fstab

Sebelum masuk ke arch baru kamu, generate fstab dengan perintah `genfstab -U /mnt >> /mnt/etc/fstab`.

{{< expand "Apa kegunaannya ?" "🤔" >}}
## fstab

fstab dapat digunakan untuk menentukan bagaimana partisi disk atau sistem file jarak jauh harus dipasang ke filesystem.
{{< /expand >}}

### Post-konfigurasi

Saatnya kamu chroot ke system arch kamu dengan `arch-chroot /mnt`

#### Timezone

Set time zone dengan:

```plain
# ln -sf /usr/share/zoneinfo/Asia/Jakarta /etc/localtime
```

Pastikan linux menggunakan UTC dengan:

```plain
# hwclock --systohc
```

#### Localization

Edit file `/etc/locale.gen` dan hilangkan `#` pada `en_US.UTF-8 UTF-8`, generate locale dengan `locale-gen`.

Buat locale.conf dengan perintah:
```plain
# echo "LANG=en_US.UTF-8" > /etc/locale.conf
```

#### Hostname

Atur hostname dengan:

```plain
# echo "nama_hostname" > /etc/hostname
```

Agar hostname kamu bisa di resolve, tambahkan ini di `/etc/hosts`:
```plain
127.0.0.1        localhost
::1              localhost
127.0.1.1        nama_hostname
```

#### User management

Tambahkan password untuk root kamu dengan perintah `passwd`.

Sebagai tambahan, ada baiknya jika kamu membuat non-root user dengan:

{{< highlight plain "linenos=table" >}}
# useradd -mG wheel nama_user
# passwd nama_user
{{< /highlight >}}

#### GRUB

Jangan lupa untuk generate GRUB, jika tidak kamu tidak bisa masuk ke system kamu.

{{< tabs "3" >}}
{{< tab "EFI" >}}

{{< highlight plain "linenos=table" >}}
# grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
# grub-mkconfig -o /boot/grub/grub.cfg
{{< /highlight >}}

{{< /tab >}}
{{< tab "MBR" >}}

{{< highlight plain "linenos=table" >}}
# grub-install --target=i386-pc /dev/sda
# grub-mkconfig -o /boot/grub/grub.cfg
{{< /highlight >}}

{{< /tab >}}
{{< /tabs >}}

#### Other services

Hidupkan service NetworkManager dengan:

```plain
# systemctl enable NetworkManager
```

Exit chroot dengan `exit` jika semuanya sudah pas.

### Reboot

Sebelum reboot, unmount dulu partisi tadi dengan:

```plain
# umount -R /mnt
```

Lalu reboot dengan `reboot`.

## Post-installation

Sesudah menginstall, kamu akan booting ke tampilan CLI karena tidak ada grafis sama sekali. Kamu boleh menginstall bebas display server atau bahkan tidak memakai display server sama sekali. Jika tidak tahu harus mulai dari mana, [cek post ini](#).