---
title: SQL 21 - Union
weight: 21
tags:
  - MySQL
---

Menggabungkan rows di dua tabel yang berbeda.

Ada syarat yang harus dipenuhi sebelum melakukan union:
- Jumlah kolom harus sama.
- Tipe data kolom harus sama.

Ada dua tabel:

`accounts`:

| account_id | first_name | last_name | username |
|------------|------------|-----------|----------|
|          1 | Beck       | Yohanna   | becky9   |
|          2 | Hanifah    | Shabari   | biraa6   |
|          3 | Yitzhak    | Rabin     | yitzhak  |
|          4 | Saqid      | Mussadiq  | sadick09 |

`administrators`:

| id   | username  |
|------|-----------|
| 1000 | itsmaaya  |
| 1001 | jenniffer |
| 1002 | joann     |

Menggabungkan `administrators` ke table, accounts. Karena keduanya memiliki kolom yang beda, kita hanya `select` kolom `account_id` dan `username` saja pada `account`.

```mysql
select account_id, username from accounts
union
select * from administrators;
```

## Lebih lanjut

- https://www.w3schools.com/sql/sql_union.asp
