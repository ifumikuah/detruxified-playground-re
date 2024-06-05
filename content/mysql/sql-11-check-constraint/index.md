---
title: SQL 11 - Check constraint
weight: 11
tags:
  - MySQL
---

`CHECK` constraint adalah constraint regulasi terhadap value kolom.

## Menambah di table baru

`constraint min_score check (score >= 10)` membuat constraint `check` dengan nama `min_score`, value `score` diterima jika `>= 10`.

```mysql
create table scoreboard (
	user_id int not null auto_increment,
	username varchar(25) unique,
	score int,
	constraint min_score check (score >= 10)
);
```

## Alter di table yang sudah ada

```mysql
alter table scoreboard
add constraint min_score check (score >= 10);
```
