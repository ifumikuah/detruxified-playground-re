---
title: SQL 22 - View
weight: 22
tags:
  - MySQL
---

`VIEW` adalah virtual table yang update otomatis berdasarkan hasil database real.

Membuat views bernama `players` dari table `accounts`:

| account_id | first_name | last_name | username |
|------------|------------|-----------|----------|
|          1 | Beck       | Yohanna   | becky9   |
|          2 | Hanifah    | Shabari   | biraa6   |
|          3 | Yitzhak    | Rabin     | yitzhak  |
|          4 | Saqid      | Mussadiq  | sadick09 |

Kita hanya butuh kolom `account_id` dan `username` saja untuk keperluan display skor.

```mysql
create view players as
select account_id, username
from accounts;

select * from players;
```

| account_id | username |
|------------|----------|
|          1 | becky9   |
|          2 | biraa6   |
|          4 | sadick09 |
|          3 | yitzhak  |

View `players` ini akan terupdate otomatis ketika kamu menambahkan `row` baru di `accounts`.

