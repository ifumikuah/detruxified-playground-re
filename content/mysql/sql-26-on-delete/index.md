---
title: SQL 26 - On Delete
weight: 26
tags:
  - MySQL
---

`on delete` adalah modifier untuk constraint foreign key. Karena foreign key terikat dengan table lain, table yang teriikat ini perlu di update andai kata salah satu id/value di sumber foreign key terhapus.

Ada 2 keyword untuk `on delete`:
- `set null`, ubah isi value pada kolom foreign key menjadi `null` jika row pada sumber dihapus.
- `cascade`, menghapus/menghilangkan baris pada foreign key jika row pada sumber dihapus.

## Membuat on delete

Sama seperti saat membuat foreign key, tinggal tambahkan `on delete`

```mysql
create table scoreboard (
	user_id int not null auto_increment,
	username varchar(25) unique,
	score int,
	account_id int,
	primary key (user_id),
	constraint fk_account_id
	foreign key (account_id) 
	references accounts (account_id) on delete cascade
);
```

Diatas membuat foreign key `on delete` menjadi `cascade`.

## Alter

Foreign key yang terlajur dibuat tidak bisa diubah langsung, satu-satunya cara adalah drop foreign key yang sudah dibuat sebelumnya kemudian buat baru lagi.

```mysql
alter table scoreboard drop foreign key fk_account_id;

alter table scoreboard
add constraint fk_account_id
foreign key (account_id) references accounts (account_id) on delete cascade;
```
