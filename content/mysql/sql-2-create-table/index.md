---
title: SQL 2 - Create table
weight: 2
tags:
  - MySQL
---

	Didalam sebuah database ada sebuah / lebih dari satu table.

## Membuat table

Membuat tabel sama seperti membuat database, bedanya kamu juga perlu menambahkan kolom beserta tipe datanya.

Misal, kolom pertama adalah `karyawan_id` dengan value tipe data `int`.

```mysql
create table karyawan (
	karyawan_id int,
	nama varchar(50),
	gaji decimal(5, 2),
	tanggal_mulai date
);
```

## Rename table

```mysql
rename table karyawan to employees;
```

Mengubah nama tabel `karyawan` -> `employees`

## Drop table

```mysql
drop table karyawan;
```

## Alter table

Alter table adalah memodifikasi kolom didalam table.

Membuat kolom baru `telepon`.
```mysql
alter table karyawan add telepon varchar(12);
```

Rename kolom tersebut.
```mysql
alter table karyawan rename column telepon to no_telepon;
```

Delete kolom.
```mysql
alter table karyawan drop column no_telpon;
```

## Modifikasi kolom

Modifikasi tipe data.
```mysql
alter table karyawan
modify column nama varchar(25);
```

Setiap code eksekusinya sql, selalu diakhiri oleh semicolon `;`. Jadi kode diatas sama saja dengan:
```mysql
alter table karyawan modify column nama varchar(25);
```

Pindahkan posisi kolom.
```mysql
alter table karyawan
modify nama varchar(25) after gaji;
```

Akan mengubah kolom:

| karyawan_id  | nama | gaji | tanggal_mulai |
|-|-|-|-|

Menjadi:

| karyawan_id  | gaji | nama | tanggal_mulai |
|-|-|-|-|

Pindahkan kolom menjadi posisi pertama.
```mysql
alter table karyawan
modify nama varchar(25) first;
```

Menjadi:

| nama  | gaji | karyawan_id | tanggal_mulai |
|-|-|-|-|
