---
title: SQL 10 - Not Null Constraint
weight: 10
tags:
  - MySQL
---

Membuat `not null` constraint, `not null` membuat sebuah kolom dilarang untuk membuat nilai `null` di setiap valuenya.


```mysql
create table food(  
	`id` int unique,  
	`name` varchar(20) not null,     
	`price` int not null
);
```

Untuk menambahkannya di tabel yang sudah dibuat sebelumnya:
```mysql
alter table food
modify id int not null;
```
