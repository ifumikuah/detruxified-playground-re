---
title: SQL 8 - Unique constraint
weight: 8
tags:
  - MySQL
---

constraint adalah semacam modified untuk kolom, di catatan ini akan memberikan contraint `unique`, membuat value di sebuah kolom harus unik satu sama lain.

```mysql
create table food(  
	`id` int unique,  
	`name` varchar(20),     
	`price` int
);
```

Well, apa yang harus dilakukan jika table sudah terlanjur dibuat?, kamu bisa menambahkan constraint sesudahnya.

Disini akan menambahkan constraint `unique` terhadap kolom `name`
```mysql
alter table food
add constraint unique(name)
```

Ini akan membuat semua nama di kolom `name` tidak ada boleh yang sama, jika sama maka penambahan baris tersebut tidak diterima.
