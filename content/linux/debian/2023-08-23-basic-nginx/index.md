---
title: Basic Nginx Setup
draft: false
weight: 2
resources: 
    - name: nginx
      src: nginx.png
      title: Halaman default nginx
---

{{< toc >}}

Menginstall HTTP Web Server nginx. 

Tutorial ini mengasumsikan debian sebagai server, sesuaikan dengan distro masing-masing jika tidak menggunakan debian.

## Prerequisite &#x1F9E0;

- Basic bash commands: `cp`, `mkdir`, `sudo`, `cat`, `mv`, `rm`
- Use CLI text editor: `vi`, `vim`, `nvim`, `emacs` or `nano`

## Install nginx

```plain
sudo apt install nginx
```

## Firewall (optional)

Jika menggunakan firewall, buka port 80 dan 443 (http dan https). Umumnya, semua distro memakai `ufw` atau `firewalld` sebagai firewall, lihat petunjuk firewall masing-masing jika tidak memakai keduanya.

{{< tabs "1" >}}
{{< tab "ufw" >}}
{{< highlight plain "linenos=table" >}}

sudo ufw allow "Nginx Full"
sudo ufw reload

{{< /highlight >}}
{{< /tab >}}
{{< tab "firewalld" >}}
{{< highlight plain "linenos=table" >}}

sudo firewall-cmd --add-service=http --permanent
sudo firewall-cmd --add-service=https --permanent
sudo firewall-cmd --reload

{{< /highlight >}}
{{< /tab >}}
{{< /tabs >}}

## You're ready to go

Pergi ke alamat localhost (jika di server) atau alamat IP server untuk melihat halaman nginx.
{{< img name=nginx >}}

## Where's config &#x1F913;

File konfigurasi terletak di `/etc/nginx/`. Ada 3 file penting yaitu:

```markdown
---
/etc/nginx/
---

|- nginx.conf
|
|- sites-available/
|   |
|   |- default
|
|- sites-enabled/
    |
    |- default -> /etc/nginx/sites-available

```
| File/dir name | Keterangan |
|-|-|
| `nginx.conf` | menyimpan semua konfigurasi nginx |
| `site-available/` | konfigurasi per website |
| `site-enabled/` <sup>1</sup> | akan terbaca oleh nginx ketika service dimulai |

<sup>[1]</sup> Umumnya file yang ada di dalamnya soft-link (shortcut) dari `site-available/`.

### Root directory

Lihat `/etc/nginx/sites-available/default` sebagai referensi. Biasanya directory website terletak di `/var/www/`

Dibawah adalah contoh dari konfig. `default`:
```plain
server {
        listen 80 default_server;
        listen [::]:80 default_server;
        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;
        server_name cherrypie.home;

        location / {
                try_files $uri $uri/ =404;
        }
}
```
Webpage ini akan membaca `index.html` yang ada di `/var/www/html/` melalui port `80`.

## Nyalakan nginx

```plain
sudo systemctl restart nginx
```

Jika kamu hanya ingin reload konfigurasi nginx, jalankan:

```plain
sudo nginx -s reload
```