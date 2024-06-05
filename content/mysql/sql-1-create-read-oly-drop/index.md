---
title: SQL 1 - Create, Read-only, Drop
weight: 1
tags:
  - MySQL
---

## Membuat sebuah database

Membuat database bernama `myDB`

```mysql
create database myDB;
```

## Set `myDB` sebagai database default

```mysql
use myDB;
```

## Membuat database menjadi read-only

```mysql
alter database myDB read only = 1;
```

database yang berstatus read-only tidak bisa di *drop* atau dihapus, jadi matikan read-only sebelum mengubah/menghapus database.

```mysql
alter database myDB read only = 0;
```

## Menghapus/drop database

```mysql
drop database myDB;
```
