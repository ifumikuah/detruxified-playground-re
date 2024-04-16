+++
title = "Python: Environment"
draft = false
weight = 12
tags = ['python']
+++

## Environment

Environment atau scope adalah lingkungan dimana kode dijalankan.

Ketika kamu baru saja menginstall *plain* python vanilla tanpa tambahan apapun, maka program yang kamu jalankan berada di **global scope** atau di lingkungan sistem operasi kamu langsung.

### Virtual Environment

Jika kamu belum mengenal Virtual Environment sebelumnya maka dipastikan kode yang kamu eksekusi selama ini berada di **global environment** atau di lingkungan sistem operasi.

Virtual Environment adalah upaya untuk membuat sebuah lingkungan rekayasa agar addon/versi yang dibutuhkan pada kode tersebut tidak bentrok.

Jika kamu membuat dua proyek yang berbeda dalam satu lingkungan, maka kemungkinan besar akan ada bentrok versi terhadap addon/library tambahan pada masing masing program.

## Virtual Environment menggunakan virtualenv

Install `virtualenv` menggunakan `pip`, `pip` biasanya sepaket jika kamu menginstall python.

```plain
pip install virtualenv
```
`virtualenv` terletak di:

```plain
C:\Users\your_username\AppData\Local\Programs\Python\Python312\Scripts\


Note:
"C:\Users\your_username\AppData\Local\Programs\Python" adalah lokasi dimana python di install dalam kasus ini, yang lain mungkin memiliki direktori yang beda.

"Python312" adalah versi python yang kamu install, dalam kasus ini versi 3.12 yang diinstall
```

Pastikan direktori tersebut masuk kedalam `$PATH` di Environment Variables.

### Membuat virtualenv (quick start)

```plain
## Buat sebuah direktori untuk proyek baru. ##
> mkdir project_alpha

## Masuk ke direktori tersebut ##
> cd project_alpha

## Inisalisasi environment baru ##
> virtualenv .

## Masuk ke environment yang baru saja dibuat ##
> .\Scripts\activate

## Melihat library/modules apa saja yang terpasang di environment ini ##
(project_alpha) > pip list

## Keluar dari environment dan kembali ke global ##
(project_alpha) > deactivate

## Di global, (project_alpha) kamu akan hilang menandakan kamu tidak lagi di lingkungan "project_alpha" ##
>
```

### Menginstall sebuah library 

Misal, menginstall library visualisasi data `seaborn`.

```plain
## Pastikan berada di virtual environment proyek kamu ##
(project_alpha) > pip install seaborn==0.10
## diatas akan mengistall versi 0.10 ##

(project_alpha) > pip list
```

Mengimport library di proyek

```python
import seaborn as sb

# code here
```