---
title: SQL 20 - Self Join
weight: 20
tags:
  - MySQL
---

Menggabungkan satu atau lebih table, berdasarkan relasi antar kolom.

Sebuah table `affiliates`:

| user_id | username | affiliates_id |
|---------|----------|---------------|
|       1 | john     |             2 |
|       2 | jade     |             1 |
|       3 | mark     |             2 |
|       4 | wade     |             2 |
|       5 | kurt     |             3 |

`affiliates_id` mengindikasikan kepada siapa `username` di referensikan. Sebagai contoh `john`, `mark`, `wade` direferensikan oleh `jade`.

Jadi kita ingin membuat `affiliates_id` menampilkan nama usernamenya daripada `user_id` orang tersebut.

Pertama, yang dilakukan adalah kamu harus membuat table `affiliates` menjadi dua (duplikat) dan memberinya alias.

- `affiliates as a`
- `affiliates as b`

Setelanya lakukan operasi `inner` join:

```mysql
select *
from affiliates as a
inner join affiliates as b
```

Lalu tambahkan clause validasi/kriteria, kita ingin `affiliates_id`  di sisi kiri (`a`) sama dengan `user_id` di sisi kanan (`b`).

```mysql
select *
from affiliates as a
inner join affiliates as b
where a.affiliates_id = b.user_id;
```

| user_id | username | affiliates_id | user_id | username | affiliates_id |
|---------|----------|---------------|---------|----------|---------------|
|       1 | john     |             2 |       2 | jade     |             1 |
|       2 | jade     |             1 |       1 | john     |             2 |
|       3 | mark     |             2 |       2 | jade     |             1 |
|       4 | wade     |             2 |       2 | jade     |             1 |
|       5 | kurt     |             3 |       3 | mark     |             2 |

Kita hanya butuh kolom `user_id` dan `username` dari sisi `a` dan `username` dari sisi `b`.

```mysql
select a.user_id, a.username, b.username as affiliator
from affiliates as a
inner join affiliates as b
where a.affiliates_id = b.user_id;
```

| user_id | username | affiliator |
|---------|----------|------------|
|       1 | john     | jade       |
|       2 | jade     | john       |
|       3 | mark     | jade       |
|       4 | wade     | jade       |
|       5 | kurt     | mark       |
