---
title: SQL 12 - Default constraint
weight: 12
tags:
  - MySQL
---

Constraint untuk menetapkan nilai default

```mysql
create table scoreboard (
	user_id int not null auto_increment,
	username varchar(25) unique,
	score int default 20,
	constraint min_score check (score >= 10)
);
```

Jika `score` tidak diisi valuenya, maka default akan digunakan, yaitu `20`.

## Alter

```mysql
alter table scoreboard
alter score set default 20
```
