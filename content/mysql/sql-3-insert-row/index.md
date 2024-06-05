---
title: SQL 3 - Insert row
weight: 3
tags:
  - MySQL
---

Menambah baris di tabel yang baru dibuat.

## Menambah baris baru

| karyawan_id  | nama | gaji | tanggal_mulai |
|-|-|-|-|
| 1 | "Arif" | 15.30 | "2024-01-11" |

```mysql
insert into karyawan
values (1, "Arif", 15.30, "2024-01-11");
```

Catatan: Urutan value harus cocok dengan urutan kolom.

## Menambah banyak baris baru

```mysql
insert into karyawan
values 
	(2, "Budi", 10.50, "2024-01-25"),
	(3, "Joni", 6.50, "2024-02-14"),
	(4, "Reza", 6.50, "2024-03-28");
```

## Menambah baris dengan value kolom kosong

Apa yang terjadi jika value yang diisi tidak lengkap.

```mysql
insert into karyawan
values (5, "Aceng");
```

Akan terjadi error!

Solusi:

```mysql
insert into karyawan (karyawan_id, nama)
values (5, "Aceng");
```

Atau walaupun baris yang dimasukkan lengkap, cara paling aman adalah seperti berikut:
```mysql
insert into karyawan (karyawan_id, nama, gaji, tanggal_mulai)
values (1, "Arif", 15.30, "2024-01-11");
```

