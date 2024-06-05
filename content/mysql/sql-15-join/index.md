---
title: SQL 15 - Join
weight: 15
tags:
  - MySQL
---

Menghubungkan dua / lebih tabel berdasarkan mutual key, dalam hal ini foreign key.

Join biasanya digambarkan ibarat diagram venn, terdapat sisi kiri dan kanan. dalam hal ini adalah tabel kiri dan kanan.

Di contoh ini, kita memiliki dua tabel:

Tabel akun pemain (`accounts`):

| account_id | first_name | last_name | username |
|------------|------------|-----------|----------|
|          1 | Beck       | Yohanna   | becky9   |
|          2 | Hanifah    | Shabari   | biraa6   |
|          3 | Yitzhak    | Rabin     | yitzhak  |
|          4 | Saqid      | Mussadiq  | sadick09 |

Tabel `scoreboard` pemain. Di scoreboard pemain anonim/guest juga tercatat dalam tabel skor ini.

| score_id | score | account_id |
|----------|-------|------------|
|      100 |    30 |          1 |
|      101 |    15 |          1 |
|      102 |     5 |          2 |
|      103 |    10 |          3 |
|      104 |    50 |          2 |
|      105 |    20 |          3 |
|      106 |    25 |       NULL |
|      107 |    10 |       NULL |
|      108 |    10 |       NULL |

Kita akan membuat skenario tabel `accounts` berada di kiri dan `scoreboard` di kanan.

## Join inner

List tabel yang match di kedua sisi.

```sql
select *
from accounts inner join scoreboard 
on accounts.account_id = scoreboard.account_id;
```

| account_id | first_name | last_name | username | score_id | score | account_id |
|------------|------------|-----------|----------|----------|-------|------------|
|          1 | Beck       | Yohanna   | becky9   |      100 |    30 |          1 |
|          1 | Beck       | Yohanna   | becky9   |      101 |    15 |          1 |
|          2 | Hanifah    | Shabari   | biraa6   |      102 |     5 |          2 |
|          2 | Hanifah    | Shabari   | biraa6   |      104 |    50 |          2 |
|          3 | Yitzhak    | Rabin     | yitzhak  |      103 |    10 |          3 |
|          3 | Yitzhak    | Rabin     | yitzhak  |      105 |    20 |          3 |

## Join left

List tabel sisi kiri.

```sql
select *
from accounts left join scoreboard 
on accounts.account_id = scoreboard.account_id;
```

| account_id | first_name | last_name | username | score_id | score | account_id |
|------------|------------|-----------|----------|----------|-------|------------|
|          1 | Beck       | Yohanna   | becky9   |      100 |    30 |          1 |
|          1 | Beck       | Yohanna   | becky9   |      101 |    15 |          1 |
|          2 | Hanifah    | Shabari   | biraa6   |      102 |     5 |          2 |
|          2 | Hanifah    | Shabari   | biraa6   |      104 |    50 |          2 |
|          3 | Yitzhak    | Rabin     | yitzhak  |      103 |    10 |          3 |
|          3 | Yitzhak    | Rabin     | yitzhak  |      105 |    20 |          3 |
|          4 | Saqid      | Mussadiq  | sadick09 |     NULL |  NULL |       NULL |

Perhatikan ID 4, `sadick09` tetap terdisplay, walaupun belum pernah mencetak skor.

## Join right

```sql
select *
from accounts right join scoreboard 
on accounts.account_id = scoreboard.account_id;
```

| account_id | first_name | last_name | username | score_id | score | account_id |
|------------|------------|-----------|----------|----------|-------|------------|
|          1 | Beck       | Yohanna   | becky9   |      100 |    30 |          1 |
|          1 | Beck       | Yohanna   | becky9   |      101 |    15 |          1 |
|          2 | Hanifah    | Shabari   | biraa6   |      102 |     5 |          2 |
|          3 | Yitzhak    | Rabin     | yitzhak  |      103 |    10 |          3 |
|          2 | Hanifah    | Shabari   | biraa6   |      104 |    50 |          2 |
|          3 | Yitzhak    | Rabin     | yitzhak  |      105 |    20 |          3 |
|       NULL | NULL       | NULL      | NULL     |      106 |    25 |       NULL |
|       NULL | NULL       | NULL      | NULL     |      107 |    10 |       NULL |
|       NULL | NULL       | NULL      | NULL     |      108 |    10 |       NULL |
