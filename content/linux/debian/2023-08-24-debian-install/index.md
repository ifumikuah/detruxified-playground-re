---
title: Debian Install
draft: false
weight: 1
resources:
    - name: 01-network
      src: "01-network-card.png"
      title: Network Cards
    - name: 04-locale
      src: "04-locale-select.png"
      title: Select en_US.UTF-8
    - name: 06-hostname
      src: "06-hostname.png"
      title: Hostname
    - name: 07-domain-name
      src: "07-domain-name.png"
      title: Hostname domain with hostname.home
    - name: 09-name
      src: "09-name.png"
      title: Your name
    - name: 17-confirm-write
      src: "17-confirm-write.png"
      title: Overview partisi
    - name: 19-scan-media
      src: "19-scan-media.png"
      title: Media scan
    - name: 20-select-mirror
      src: "20-select-mirror.png"
      title: Mirror
    - name: 23-software-select
      src: "23-software-select.png"
      title: Software selection
    - name: 25-grub-location
      src: "25-grub-location.png"
      title: GRUB install
    - name: 26-install-complete
      src: "26-install-complete.png"
      title: Install finished

---

{{< toc >}}

Step to step cara menginstall debian untuk server di VirtualBox. Jika kamu menggunakan komputer fisik, step mungkin sedikit berbeda di setting jaringan dan partisi.

## Prerequisites

- USB Bootable ISO Debian, jika menggunakan fisik
- ISO Debian, jika menggunakan VirtualBox

### Mendapatkan ISO

ISO bisa didapatkan dari website resmi [debian](https://www.debian.org/index.en.html), page untuk download iso sangat tricky, [pergi ke sini](https://www.debian.org/distrib/netinst) jika kamu ingin mendapatkan Live ISO minimal (600MB).

### Membuat bootable ISO (fisik)

Gunakan Rufus untuk membuat bootable ISO. [But how ? &#x1F914;](#)

## Konfigurasi VirtualBox

Buat virtual machine baru di VirtualBox dengan konfigurasi jaringan: 

{{< img name=01-network size=small >}}

Konfigurasi VirtualBox di tutorial ini adalah: 
- BIOS/MBR boot
- 20GB Disk
- 2 Adapter, Bridged Adapter (Adapter 1), Internal Adapter (Adapter 2)

## Install

Di menu boot ada 2 pilihan install, graphics install dan install.

Pilih **Graphical Install**.

### Bahasa

Pilih **English**, bahasa inggris membuat instalasi lebih mudah.

### Location

Pilih lokasi untuk waktu, Indonesia berada di:\
**other** > **Asia** > **Jakarta**

### Keyboard

Pilih **American English** untuk keyboard qwerty pada umumnya.

### Locales

Pilih **United States** - **en_US.UTF-8**

{{< img name=04-locale size=small >}}

### Network

Pilih yang **pertama**

{{< expand "Untuk pengguna install fisik 🖥" >}}
## Instal Fisik

Ada dua sumber jaringan, Wireless dan Ethernet (kabel)
- interface dengan nama seperti `wlan0`, `wlp2s0` adalah wireless.
- interface dengan nama seperti `eth0`, `enp0s2` adalah Ethernet.
{{< /expand >}}

### Hostname

Buat nama hostname, hostname adalah nama dari komputer/server kamu (bukan username).

{{< img name=06-hostname size=small >}}

### Domain

Buat domain dari hostname.

{{< img name=07-domain-name size=small >}}

### Password root

Isi password untuk root.

### Full name

Isi nama lengkap kamu, isi sembarang saja.

{{< img name=09-name size=small >}}

### Non-root user

Setelah itu kamu akan diminta untuk membuat user non-root dan passwordnya. 

{{< hint type=important >}}
Samakan password root dengan non-root agar tidak bingung.
{{< /hint >}}

### Clock timezone

Pilih zona waktu yang sesuai dengan tempatmu.

### Partisi

{{< hint type=warning >}}

Untuk instalasi fisik, lihat [post ini](#) dulu jika tidak tahu cara mem-partisi linux.

{{< /hint >}}

#### Partisi 1.1

Pilih **Guided**, proses lebih cepat sedikit konfigurasi. 

{{< hint type=warning >}}

Untuk instalasi fisik pilih **Manual** dan lihat [disini](#) sebagai panduan partisi.

{{< /hint >}}

#### Partisi 1.2

Pilih Harddisk tujuan, biasanya memiliki nama `sda`, `sdb`, ...

#### Partisi 1.3

Skema partisi, pilih yang **pertama**.

#### Partisi 1.4

Pilih **finish partitioning and write changes to disk**.

#### Partisi 1.5

Kira-kira, partisi akan seperti ini hasilnya:

{{< img name=17-confirm-write size=small >}}

Konfirmasi dengan pilih, **yes**.

### Installation media scan

Kamu akan diminta untuk scan media install lainnya, pilih **no**.

{{< img name=19-scan-media size=small >}}

### Mirror

Pilih negara dan lokasi mirror, untuk jaga-jaga apabila server down, pilih saja **deb.debian.org** (main server). Main server ada di semua negara, pilih saja **Indonesia** atau **United States**.

{{< img name=20-select-mirror size=small >}}

### Proxy

Kosongkan isian proxy dan continue.

### Popularity contest

Debian akan telemetry mengenai package yang paling sering dipakai di server kamu, pilih bebas, disarankan pilih **no**.

### Software Selection

Pilihan software yang ingin diinstall, karena tutorial ini tentang server headless, hapus centang debian desktop environment dan DE nya, pilih **SSH Server** dan **Standard system utilities**

{{< img name=23-software-select size=small >}}

### GRUB

Pilih **yes** untuk install GRUB Bootloader. Pilih lokasinya di disk yang kamu pilih [sebelumnya](#partisi-12).

{{< img name=25-grub-location size=small >}}

## Finishing

Saat sudah selesai, pilih **continue** untuk reboot.

{{< img name=26-install-complete size=small >}}