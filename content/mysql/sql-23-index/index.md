---
title: SQL 23 - Index
weight: 23
tags:
  - MySQL
---

Index berguna untuk mempercepat query / pencarian berdasarkan kolom tertentu. Defaultnya index sudah ada pada kolom `id` jika kita memberikannya primary key.

List apakah index sudah ada di table `tablename`:

```mysql
show indexes from tablename;
```

Menambah index:

```mysql
CREATE INDEX index_name 
ON tablename (col);
```

Bisa juga lebih dari satu kolom:

```mysql
ON tablename (col1, col2, col3, ...)
```

Best practices adalah untuk membuat index pada table yang jarang di update, karena pada table yang sering mengalami update, keberadaan `index` justru memperlambat proses update table tersebut.
