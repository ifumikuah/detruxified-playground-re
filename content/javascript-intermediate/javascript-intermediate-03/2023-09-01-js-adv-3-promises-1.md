+++
title = "Javascript Intermediate 03: Promises Intro"
draft = false
weight = 1
tags = ['javascript']
+++

## Apa itu Promises

Promises adalah sebuah janji, sebuah object yang merepresentasikan sebuah janji.

### Janji

Janji adalah sebuah "janji" yang kita tidak tau outcome nya.

Contoh: A meminjam seratus B, A berjanji akan membayar utang tersebut dengan tenggat waktu 2 bulan, jika lewat 2 bulan maka B berasumsi bahwa A kabur dan B akan menelepon polisi.

Jika di representasikan dengan if else, maka akan seperti ini.

```js
if (diBayar) {
    return "utang terlunaskan";
} else if (!diBayar) {
    return "peminjam kabur, lapor polisi!!";
}
//Atau
if (diBayar) {
    return "utang terlunaskan";
} else {
    return "peminjam kabur, lapor polisi!!";
}
```

Di Promises, terdapat tiga state/kondisi, yaitu:
- Pending, Initial state, masih di H- pelunasan utang, belum melewati waktu ketentuan yaitu diatas 60 Hari.
- Fulfilled, Success state, A sudah melunaskan pinjaman uangnya.
- Rejected, Failed state, B menelepon polisi dengan alasan A kabur 60 Hari setelah dipinjamkan uang.

### Asynchronous Operations

Promises berjalan secara asychronous, apa itu asynchronous?. Saya akan menjelaskan Synchronous dan Asynchronous dengan analogi pemesanan makanan.

Bilang kita membuka stand jualan burger.
- Pelanggan pertama : memesan 3 burger daging varian combo (waktu memasak 3x 8menit).
- Pelanggan kedua : memesan 1 roti panggang (waktu memasak 1x30 detik).
- pelanggan ketiga : memesan 1 burger reguler (waktu memasak 1x1 menit).

#### Synchronous
Kita akan memasak pesanan secara *sequential* dimulai dari pelanggan #1, selama 24 menit. Di dunia nyata, ini akan membuat pelanggan #2 dan seterusnya pulang karena mereka tidak mau menunggu 24 menit untuk memesan roti panggang yang hanya butuh waktu 30 detik penyajian.

Pada umumnya, pemrograman sederhana menggunakan metode ini, contohnya `if else`.

#### Asynchronous
Kita akan memasak semua pesanan secara parallel, Kita memasak pesanan #1 tapi disisi lain juga memprioritaskan pesanan paling ringan terdahulu. TL;DR, multitasking.