---
title: SQL 24 - Subquery
weight: 24
tags:
  - MySQL
---

Sub query adalah menjalankan query didalam query:

Mari bilang kita ingin mencari rata-rata dari panjang karakter di `username`.

```mysql
SELECT AVG(LENGTH(nickname)) FROM users;
```

Namun, bagaimana jika kita ingin mencari nama-nama yang diatas rata-rata.

```mysql
select * from users
where LENGTH(nickname) > (
	SELECT AVG(LENGTH(nickname)) FROM users
);
```

Jadi terdapat query didalam sebuah query.
