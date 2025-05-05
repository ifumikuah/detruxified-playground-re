+++
title = "Setup Git SSH dengan WSL2"
draft = false
weight = 1
tags = ['windows', 'wsl', 'linux']

[[resources]]
name = "fig1"
src = "img/fig1.png"
title = ""

[[resources]]
name = "fig2"
src = "img/fig2.png"
title = ""

[[resources]]
name = "fig3"
src = "img/fig3.png"
title = ""
+++

Artikel ini menjelaskan bagaimana cara set-up SSH Git untuk host windows dan WSL2 distro.

{{< hint type=note title=Note >}}
**Requirements**\
`git` dan `ssh` dari OpenSSH sudah terinstall di Windows dan WSL. Biasanya windows sudah ada `ssh` dan untuk WSL, Ubuntu dan Fedora sudah ada `ssh` terinstall didalamnya.
{{< /hint >}}

## Windows

Di terminal/powershell:

```
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Jika menggunakan Windows 10 lama atau yang lebih lawas, ganti `-t ed25519` menjadi `-t rsa -b 4096`.

Lalu akan muncul dialog:

*"Enter file in which to save the key (/c/Users/YOU/.ssh/id_ALGORITHM):"*, tekan saja **Enter**.

Setelahnya, akan diminta sebuah *passphrase* mirip seperti password, buat saja 1-3 angka yang mudah diingat. Atau boleh juga tidak memiliki *passphrase* sama sekali.


### SSH Auth Agent

Auth agent dijalankan agar ssh key tadi bisa digunakan.

Di terminal/powershell:

```
Get-Service -Name ssh-agent | Set-Service -StartupType AutomaticDelayedStart
Start-Service ssh-agent
```

Kemudian, tambahkan key di step awal tadi ke ssh agent:

```
ssh-add c:/Users/YOU/.ssh/id_ed25519
```

### Menambahkan SSH Pubkey

Pergi ke browser, sebelum itu pastikan github sudah login atas user yang diinginkan:

[https://github.com/settings/ssh/new](https://github.com/settings/ssh/new)

{{< img name=fig1 size=medium lazy=true >}}

Pada bagian **Title** isi saja bebas.

Kembali ke terminal/powershell:

```
cat ~/.ssh/id_ed25519.pub | clip
```

Jika kamu menggunakan powershell klasik, powershell yang bukan didalam windows terminal baru:

```
clip < ~/.ssh/id_ed25519.pub
```

Dua perintah diatas sama, menyimpan isi pubkey kedalam clipboard.

Lalu *paste* kan kedalam box **Key**, lalu klik **Add SSH key**.

## WSL

Di terminal windows, pergi ke `~/.ssh/`:

```
cd ~/.ssh/
```

Lalu `ls`, terdapat dua file untuk key:

```
id_ed25519      -> untuk private
id_ed25519.pub  -> untuk publik
```

Copy dan paste keduanya kedalam filesystem WSL, filesystem WSL berada pada alamat `\\wsl$` di address bar explorer:

{{< img name=fig2 size=medium lazy=true >}}

Lalu pergi ke `\\wsl$ > distroname > home > $USER > .ssh`.

Jika tidak ada `.ssh`, kamu bisa buat baru direktori tersebut dengan nama `.ssh`.

Copy alamat (copy address) tersebut dari address bar explorer:

{{< img name=fig3 size=medium lazy=true >}}

Sebagai contoh kasus diatas, maka perintah copy paste akan seperti ini:

```
cp .\id_ed25519* \\wsl.localhost\archlinux\home\unroot\.ssh
```

`.\id_ed25519*` artinya mencocokkan semua target yang memiliki nama berawalan sebelum * (yaitu id_ed25519...).

## Git

Didalam Git Windows dan WSL, atur dulu global.name dan global.email:

```
git config --global user.name "John Doe"
git config --global user.email "mailname@serv.dom"
```

Coba clone salah satu repositori melalui ssh, ketik `yes` ketika diminta masukan dalam "*known host*", lalu masukkan *passphrase* yang sudah dibuat sebelumnya.