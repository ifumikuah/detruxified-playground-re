---
title: SQL 27 - Stored Procedures
weight: 27
tags:
  - MySQL
---

Stored Procedures mirip cara kerjanya seperti fungsi, Stored Procedures menyimpan instruksi untuk digunakan pada kesempatan lain (recallabe).

```mysql
delimiter //
create procedure get_table()
begin
	select * from client;
end//
delimiter ;
```

Penjelasan:
- Kita perlu mengubah delimiter menjadi `//` agar tidak bersinggungan dengan delimiter `;` yang ada di dalam blok eksekusi.
- `begin` dan `end` memulai dan mengakhiri blok eksekusi dengan nama `get_table`.
- Lalu kita akan mengambalikan delimiter yang sebelumnya yaitu `;`.

Memanggil: 

```mysql
call get_table();
```

## Dengan parameter

Parameter bisa lebih dari satu

```mysql
delimiter //
create procedure get_table(in ids int)
begin
	select * from client;
	where client_id = ids;
end//
delimiter ;
```

Memanggil, mencari id: `5`:

```mysql
call get_table(5);
```
