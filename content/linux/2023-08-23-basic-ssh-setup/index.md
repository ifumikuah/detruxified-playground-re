---
title: Basic SSH Server Setup
draft: false
weight: 1
---

{{< toc >}}

SSH adalah sebuah protocol jaringan yang digunakan untuk remote login. Artinya, kamu bisa mengendalikan atau login ke sebuah sistem dari jarak jauh.

## Prerequisite &#x1F9E0;

- Basic bash commands: `cp`, `mkdir`, `sudo`, `cat`, `mv`, `rm`

## Install OpenSSH

{{< tabs "1" >}}
{{< tab "Debian" >}}
```plain
sudo apt install openssh-server
```
{{< /tab >}}
{{< tab "Arch" >}}
```plain
sudo pacman -Sy openssh
```
{{< /tab >}}
{{< tab "Fedora" >}}
```plain
sudo dnf install openssh-server
```
{{< /tab >}}
{{< /tabs >}}

## Config

Nyalakan service SSH

```plain
sudo systemctl enable sshd
```
### Firewall (optional)

Jika menggunakan firewall, buka port 22 untuk service SSH. Umumnya, semua distro memakai `ufw` atau `firewalld` sebagai firewall, lihat petunjuk firewall masing-masing jika tidak memakai keduanya.

{{< tabs "2" >}}
{{< tab "ufw" >}}
```plain
sudo ufw allow "SSH"
sudo ufw reload
```
{{< /tab >}}
{{< tab "firewalld" >}}
```plain
sudo firewall-cmd --add-service=ssh --permanent
sudo firewall-cmd --reload
```
{{< /tab >}}
{{< /tabs >}}

### /etc/ssh/sshd_config

File config terletak di `/etc/ssh/sshd_config`. Ada satu parameter penting yaitu `PasswordAuthentication`, defaultnya adalah `no`, artinya kamu tidak bisa masuk SSH melalui password tradisional.

Ganti ke `yes` agar bisa masuk menggunakan password.
```plain
PasswordAuthentication yes
```
Dibawah adalah contoh konfigurasi yang mengizinkan masuk ke system root tidak berpassword. Gunakan ini jika kamu ingin menginstall Arch Linux dengan SSH (Live ISO Arch tidak memiliki password).
```plain
PasswordAuthentication yes
PermitRootLogin yes
PermitEmptyPasswords yes
```

## Restart service

```plain
sudo systemctl restart sshd
```

## SSH Client

Client adalah orang yang me-remote access sebuah SSH Server, secara default semua OS sudah tersedia SSH Client didalamnya.

Akses dengan:
```plain
ssh username@ip_address -p 22
```
Contoh mengakses server `samudrabiru.io` dengan username `tech` di port `16734`
```plain
ssh tech@samudrabiru.io -p 16734
```