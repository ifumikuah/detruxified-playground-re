---
title: SQL 14 - Foreign key
weight: 14
tags:
  - MySQL
---

`FOREIGN KEY` menghubungkan antar tabel melalui mutual key, key ini bisa berbentuk string ataupun integer. Foreign key menghindari aksi destruktif yang merusak hubungan antar table satu sama lain.

Table yang dipasangi sebagai foreign key reference tidak bisa digangu-gugat barisnya sebelum baris tersebut tidak ada relasi/afiliasi dengan tabel lainnya.

Contoh, dua tabel dibawah saling terikat melalui kolom `account_id`.

Tabel akun pemain:

| account_id | first_name | last_name | username |
|------------|------------|-----------|----------|
|          1 | Beck       | Yohanna   | becky9   |
|          2 | Hanifah    | Shabari   | biraa6   |
|          3 | Yitzhak    | Rabin     | yitzhak  |

Table skor pemain:

| score_id | score | account_id |
|----------|-------|------------|
|      100 |    30 |          1 |
|      101 |    15 |          1 |
|      102 |     5 |          2 |
|      103 |    10 |          3 |
|      104 |    50 |          2 |
|      105 |    20 |          3 |

Kamu tidak akan bisa menghapus baris `account_id = 2` di table akun pemain, karena dipakai oleh table skor pemain.

## Membuat foreign key

```mysql
create table scoreboard (
	user_id int not null auto_increment,
	username varchar(25) unique,
	score int,
	account_id int,
	primary key (user_id),
	constraint fk_account_id
	foreign key (account_id) 
	references accounts (account_id)
);
```

Diatas akan membuat foreign key pada `account_id` dengan nama `fk_account_id`. `account_id` yang ada di table `scoreboard` terhubung dengan `account_id` milik `accounts`.

## Alter

```mysql
ALTER TABLE scoreboard  
ADD CONSTRAINT fk_account_id  
FOREIGN KEY (account_id) REFERENCES accounts(account_id);
```

## Drop

```mysql
ALTER TABLE scoreboard  
DROP FOREIGN KEY fk_account_id;
```
