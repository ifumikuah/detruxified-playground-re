---
title: SQL 7 - Time
weight: 7
tags:
  - MySQL
---

Membuat semacam "timestamp" di mysql.

Ini akan di buat di table baru
```mysql
create table timex(
	`current_date` date,
	`current_time` time,
	`current_datetime` datetime
)
```

Menambah value baru berupa waktu saat ini di tiga format yang berbeda:
```mysql
insert into test (`current_date`, `current_time`, `current_datetime`)
values (current_date(), current_time(), now());

select * from test;
```
