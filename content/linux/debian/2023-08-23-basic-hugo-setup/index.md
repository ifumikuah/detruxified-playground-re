---
title: Hugo Setup on Server
draft: false
weight: 3
---

{{< toc >}}

Setup [Hugo](https://gohugo.io/) di server debian. Hugo adalah static site generator, website ini juga dibuat menggunakan hugo.

Tutorial ini mengasumsikan debian sebagai server, sesuaikan dengan distro masing-masing jika tidak menggunakan debian.

## Prerequisite &#x1F9E0;

- Basic bash commands: `cp`, `mkdir`, `sudo`, `cat`, `mv`, `rm`
- Use CLI text editor: `vi`, `vim`, `nvim`, `emacs` or `nano`
- Already read: [Basic nginx setup](/linux/debian/2023-08-23-basic-nginx/), [Basic SSH setup](/linux/2023-08-23-basic-ssh-setup) (optional)

{{< hint type=important >}}
Tutorial ini tidak mengajarkan kamu cara menggunakan hugo, tetapi hanya konfigurasi agar hugo bekerja di server kamu dan dapat diakses di device satu jaringan.
{{< /hint >}}

## Install hugo

```plain
apt install hugo
```

## Firewall (optional)

Jika menggunakan firewall, buka port 1313 (hugo menggunakan port 1313). Umumnya, semua distro memakai `ufw` atau `firewalld` sebagai firewall, lihat petunjuk firewall masing-masing jika tidak memakai keduanya.

{{< tabs "1" >}}
{{< tab "ufw" >}}
{{< highlight plain "linenos=table" >}}

sudo ufw allow 1313
sudo ufw reload

{{< /highlight >}}
{{< /tab >}}
{{< tab "firewalld" >}}
{{< highlight plain "linenos=table" >}}

sudo firewall-cmd --add-port=1313/tcp --permanent
sudo firewall-cmd --reload

{{< /highlight >}}
{{< /tab >}}
{{< /tabs >}}

## Building site &#x1F528;

Sampai disini hugo sudah bisa dijalankan, tapi belum ada situs sama sekali. Generate situs dengan: 

{{< highlight plain "linenos=table" >}}

sudo su
# cd /var/www/

{{< /highlight >}}

disarankan, membuat situs di `/var/www` agar pekerjaan lebih mudah.

{{< hint type=tip >}}
Sebaiknya ikuti arahan membuat website dari [hugo](https://gohugo.io/getting-started/quick-start/) jika kamu bingung dengan step ini.
{{< /hint >}}


{{< highlight plain "linenos=table" >}}

/var/www # hugo new site quickstart
/var/www # cd quickstart
/var/www/quickstart # git init
/var/www/quickstart # git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
/var/www/quickstart # echo "theme = 'ananke'" >> hugo.toml
/var/www/quickstart # hugo server

{{< /highlight >}}

Sekarang, `quickstart` adalah root directory website, hugo akan membaca semua yang ada di directory tersebut.

### Membuat konten

Agar bekerja dengan baik, harus ada satu artikel di website.

```plain
/var/www/quickstart # hugo new content posts/my-first-post.md
```

File artikel tersebut berformat markdown, terletak di `quickstart/content/posts`. Isi dengan artikel bebas.

```markdown
---
title: "My First Post"
date: 2022-11-20T09:03:20-08:00
draft: false
---
## Introduction

This is **bold** text, and this is *emphasized* text.

Visit the [Hugo](https://gohugo.io) website!
```

## Fire up &#x1F525;

Nyalakan live preview hugo dengan:
```plain
hugo server --bind=0.0.0.0 --baseURL="http://192.168.1.15" -D
```
Ganti `192.168.1.15` dengan IP server kamu. Parameter `-D` akan menampilkan juga draft.

## Public

Jika ingin publikasi hasilnya, directory hasil situs ada di `public`. Sebelum itu kamu harus generate website dengan:

```plain
/var/www/quickstart # hugo
```

Maka `public` akan terisi dengan website kamu dan siap di publish.

### Menggunakan nginx untuk publish website

Tambah konfigurasi website baru di `/etc/nginx/sites-available/`.

{{< highlight plain "linenos=table" >}}

# touch /etc/nginx/sites-available/cherrypie.conf
# ln -s /etc/nginx/sites-available/cherrypie.conf /etc/nginx/sites-enabled/

{{< /highlight >}}

Edit config `cherrypie.conf` yang baru saja dibuat.

```plain
server {
        listen 80;
        listen [::]:80;

        root /var/www/quickstart/public;
        index index.html;

        server_name cherrypie.home;

        location / {
                try_files $uri $uri/ =404;
        }
}
```

Hapus config `default` yang ada di `sites-enabled/`.

```plain
# rm -rf /etc/nginx/sites-enabled/default
```

Reload nginx
```plain
# nginx -s reload
```

## Membuat artikel

Gunakan VSCode dengan fitur SSH nya untuk membuat konten dengan mudah. Untuk import file static seperti gambar, video dan lagu, kamu bisa menggunakan SFTP seperti WinSCP.