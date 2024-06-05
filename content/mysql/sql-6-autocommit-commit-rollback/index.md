---
title: SQL 6 - Autocommit, Commit, Rollback
weight: 6
tags:
  - MySQL
---

By default sql membuat sebuah commit setiap query dijalankan, namun apa yang terjadi jika query yang tidak kita inginkan berjalan dan sudah terlanjur di commit oleh sql.

## Matikan autocommit

```mysql
set autocommit = off
```

## Commit secara manual

Commit akan menyimpan susunan table yang saat ini menjadi sebuah "snapshot".

```mysql
commit;
```

## Optional: Simulasikan sebuah perubahan

Sebagai contoh disini akan simulasi seluruh table dihapus:
```mysql
delete from employees;
select * from employees;
```

## Rollback

Ups, table terhapus

Rollback, kembali ke keadaan saat melakukan commit:
```mysql
rollback;
```
