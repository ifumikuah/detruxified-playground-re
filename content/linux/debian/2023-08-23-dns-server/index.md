---
title: DNS Server Setup
draft: false
weight: 4
resources: 
    - name: network-1
      src: network.drawio.png
      title: Ini yang biasanya terjadi

    - name: network-2
      src: network-2.drawio.png
      title: Ini yang diharapkan

    - name: router-admin
      src: router-admin.png
      title: Contoh pengaturan di router ZTE F660
---

{{< toc >}}

DNS membuat IP kamu bisa ditranslasikan menjadi nama seperti [www.server.com](#), proses translasi ini biasanya disebut [resolving](#). Salah satu resolver yang very basic adalah `dnsmasq`. 

Tutorial ini mengasumsikan debian sebagai server, sesuaikan dengan distro masing-masing jika tidak menggunakan debian.

## Prerequisite &#x1F9E0;

- Basic bash commands: `cp`, `mkdir`, `sudo`, `cat`, `mv`, `rm`
- Use CLI text editor: `vi`, `vim`, `nvim`, `emacs` or `nano`

## Skenario

Normalnya, jika memasang internet langganan, DNS akan berada di tangan router ISP kamu (benda putih yang ada antenna di rumahmu).

{{< img name=network-1 size=small >}}

Tapi, dengan menjadikan sebuah komputer sebagai DNS server, maka kamu bisa dengan bebas memberi nama domain IP address yang berada di satu jaringan.

{{< img name=network-2 size=small >}}

### Topologi

Karena konfigurasi cenderung rumit, kita akan membuat contoh kasus dengan topologi.

| Device | IP | Keterangan |
|-|-|-|
| Router | 192.168.1.1 | Router yang ada dirumahmu. |
| Server | 192.168.1.15 | Sebuah komputer yang berperan sebagai server, terinstall debian. |
| Laptop | 192.168.1.4 | Komputer satu jaringan sebagai client/tikus percobaan. |

{{< hint type=warning >}}
Pastikan kamu bisa mengakses admin router, dengan login ke `http://192.168.1.1`
{{< /hint >}}

## Config

Install alat tempur

```markdown
sudo apt install dnsmasq dnsutils
```

### File konfigurasi

Edit file config, terletak di `/etc/dnsmasq.conf`.

```plain
domain-needed
bogus-priv
cache-size=3000

server=1.1.1.1
server=8.8.8.8
```

{{< expand "Artinya apa bang messi 🤔" >}}
| params | keterangan |
|----|----|
| `server` | upstream dns, domain yang tidak bisa di resolve server akan langsung dilarikan ke `8.8.8.8` atau `1.1.1.1`. |
| `domain-needed` | domain yang tidak valid cuma diproses oleh local server (in this case debian). |
| `bogus-priv` | reverse resolve yang menuju ke ip local `192.168.1.x` tidak akan diteruskan ke upstream dns. |
| `cache-size` | jumlah maks cache query server, 8000 sudah lebih dari cukup untuk skala rumahan. |
{{< /expand >}}

### /etc/hosts

Alamat yang ingin kamu resolve akan tersimpan di `/etc/hosts`.

```plain
127.0.0.1       localhost

127.0.1.1       debian.192.168.1.15     debian



# The following lines are desirable for IPv6 capable hosts

::1     localhost ip6-localhost ip6-loopback

ff02::1 ip6-allnodes

ff02::2 ip6-allrouters



# Address reserved for dnsmasq

192.168.1.4    cherrypie.home
```

Restart dnsmasq :

```plain
sudo systemctl restart dnsmasq
```

## Crucial steps

Sekarang, kamu perlu mengganti DNS yang digunakan oleh router dengan cara pergi ke admin router kamu, lihat panduan masing-masing tipe router untuk mengganti DNS.

{{< img name=router-admin size=small lazy=false >}}

Kamu harus menyediakan dua DNS, yaitu DNS utama (IP server) dan backup DNS jika seandainya server kamu mati.

## Reconnect

Reconnect wi-fi device tikus percobaan, jika perlu restart router kamu agar DNS direfresh. Di server, lakukan nslookup dengan:
```plain
nslookup cherrypie.home
```
Kalau hasilnya ada `192.168.1.4` itu artinya sukses, jika tidak, dnsmasq butuh waktu untuk resolving.

Cara lain yang bisa kamu lakukan adalah dengan ping domain misal. cherrypie.home:
```plain
ping cherrypie.home -4
```
Tunggu beberapa menit sampai dibalas dengan `192.168.1.4`.