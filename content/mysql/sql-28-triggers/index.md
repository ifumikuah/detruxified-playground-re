---
title: SQL 28 - Triggers
weight: 28
tags:
  - MySQL
---


`trigger` men-trigger value di dalam kolom saat update tables.

Skenario, sebuah table `salaries`:

| id | hourly | monthly |
|----|--------|---------|
|  1 |      8 |    5760 |
|  2 |     23 |   16560 |

Kita akan mengupdate agar kolom `monthly` reflect terhadap perubahan perjamnya `hourly`.

Artinya: Setiap perubahan nilai baru dari `monthly` diupdate `hourly * 24 * 30`, Sebagaimana terdapat 24 jam x 30 hari dalam satu bulan.

```mysql
create trigger before_hourly_upd
before update on salaries
for each row
set new.monthly = (new.hourly * 30 * 24 );
```

Trigger tersimpan dengan nama `before_hourly_upd`.

## Lebih lanjut

- https://dev.mysql.com/doc/refman/8.0/en/trigger-syntax.html
- https://www.digitalocean.com/community/tutorials/how-to-use-triggers-in-mysql
- https://www.dolthub.com/blog/2023-06-09-writing-mysql-triggers/
- https://www.youtube.com/watch?v=jVbj72YO-8s
